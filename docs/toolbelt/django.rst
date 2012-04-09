Django
======

Django documentation
--------------------
* learn the tutorial
* beware: topics vs. references

Test Driven Development (TDD)
-----------------------------

General rules
+++++++++++++
* Whenever you create a file in a Django app, you also create a
  filename_tests.py file in the tests folder.
* Remember to add the new filename_tests.py file to tests/__init__.py
* Test cases are named after the thing that is tested. If we test a class named
  ``Foo`` then the test case will be named ``FooTestCase``. If we test a method
  named ``foo_bar()`` then the test case will be named ``FooBarTestCase``.
* Always add a docstring to each test case like so::

      Tests for the ``foo_bar()`` method.

  This makes sure that if we are testing functions, the test case name is not
  misleading (because it is CamelCase when the function was snake_case).
* Usually all tests for one class go into one TestCase. If you have a method
  that should be tested and that method is super complex, then you can create
  it's own TestCase only for that method (name it like
  ClassNameMethodNameTestCase).
* When you want to test different calls to a method with different parameters
  and that TestCase has a setUp / tearDown that does a lot of stuff on the
  database, it might me more performant to just write one test and call the
  method with all its different parameters in that one test. In this case
  please write comments before each call that describe which case you are
  testing (since you don't describe this through the test method name any more)

Mixin
+++++

If your app has a model Foo and in your tests you need to add Foo objects to
your database, then you should add tests/mixins.py to your app and write a
FooMixin class that provides a create_foo() method. The method should also add
the newly created object to the class, so that we can make assertions on it in
the test without having to get it from the database again.


Models
++++++
* Before writing your model, test instantiation
* If the model has any methods that do stuff (for example get_full_name() or
  get_absolute_url()) then these methods need to be covered by UnitTests.
* We do not test behavior that is given by Django such as testing if blank=True
  works.

Views
+++++
* Before writing your views, test if the view is callable
* This can be done with self.client.get(url) or self.client.post(url, data)
* always use reverse() when referring to URLs
* Each ViewTestCase should have a method get_view_name() which returns the
  namespace:name of the view in this project.
* For views that need to be called with parameters, the test case should have
  a get_view_kwargs() method.

Fixtures
--------
We make sure that a new developer can always clone the repository and run fab
rebuild. As a result he must have a fully functional site with all test data
needed to run all our selenium tests (that means, to test any possible thing
that is possible on the project's website).

The workflow should be as follows:
* Create your model
* Add migrations for your model
* Add an admin for your model
* Login as admin, go the model admin, add some test data
* Extend fab dumpdata task so that your new testdata gets dumped as well
* All dumpdata commands should look like this::

      dumpdata --indent=4 --natural appname > appname/fixtures/bootstrap.json

* run fab dumpdata and see if the generated .json file contains the model you
  just added via the Django admin.
* if it looks good, run fab loaddata. As a result, you should have the exact
  same data in your database as before.
* WARNING: Do not add tons of data in the admin, then extend fab dumpdata and
  then run fab loaddata. If dumpdata was faulty and you run loaddata, your db
  will be deleted and thanks to the faulty dumpdata command all your data might
  be lost. So: First enter just a few items, do the workflow, see if everything
  works, then add all the rest of the needed test data.
* Finally commit your changes like "Updated fixtures for appname". It is
  usually a good idea to make fixture changes as own commits and code changes
  as own commits.

* conventions:
  * user@example.com <-- self describing usernames
    password: test123
  * admin <-- admin user
    password: test123

South
-----

* http://readthedocs.org/docs/south/en/latest/

Adding your new app to South:
* ./manage.py syncdb, because convert_to_south assumes that models and DB are
  in sync already
* ./manage.py convert_to_south appname

Adding new column to model
* implement new code
* ./manage.py schemamigration appname --auto
* ./manage.py migrate

* how to add a column
