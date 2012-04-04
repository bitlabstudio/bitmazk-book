Django
======

Django documentation
--------------------
* learn the tutorial
* beware: topics vs. references

Test Driven Development (TDD)
-----------------------------

Fixtures
--------
* dumpdata --indent 4 --natural appname > appname/fixtures/bootstrap.json
* loaddata bootstrap.json
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
