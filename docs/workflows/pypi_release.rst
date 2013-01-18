PyPi Release
============

We try to release as many components of our work as possible. As a result you
can find a whole lot of our internal Django apps on Github at
https://github.com/bitmazk

Once a package is mature enough, we also create PyPi releases so that anyone
can easily install them via ``pip install package-name``.

For the following description please understand the following terms:

**Current release**

This is the release that is currently the latest release on PyPi. The
``CHANGELOG.txt`` of a project could look like this::

    ==== (ongoing) ===

    * Added this and that

    === 0.4 ===

    * Added this
    * Added that

In this example, ``0.4`` is the current release.

**Ongoing release**

Given the example ``CHANGELOG.txt`` from above, the ongoing release is labelled
as ``(ongoing)``. This is the release that you would get if you cloned the
current master branch from github. You cannot install this release form PyPi,
yet, because it is still ongoing and we don't know which version number it will
get, yet.


Version numbers
---------------

It's a science of it's own to do proper version number management. Here is how
we handle it:

* All packages start with version ``0.1``.
* When we introduce a new feature, we increase the sub-version to ``0.2``.
* When we add a bugfix or feature improvement, we increase the sub-sub-version
  to ``0.2.1``.
* When we think that the package is finally feature complete, we increase the
  major version to ``1.0``.
* A major version bump often means that the package might have backwards
  incompatible changes or that it depends on new major versions of other
  packages (such as Django).


Uploading a new PyPi Release
----------------------------

In order to upload a new PyPi Release for an existing package, the following
needs to be done:

* Make sure that you are an ``Owner`` or ``Maintainer`` for that package, if
  not, ask the owner to add you as a maintainer.
* Develop your patch, always add a description of what you have done to
  ``CHANGELOG.txt``
* Commit and push your patch
* Now it is time to prepare a new release. For this we need to bump the version
  number. Version number bumps should always be their own commits and never be
  done alongside normal patches.
* Open ``CHANGELOG.txt`` and add a new headline called ``(ongoing)``.
* Remove the ``ongoing`` from the last version and give it a new version
  number. Above you can find more information no how we chose version numbers.
* Open ``packagename/__init__.py`` and increase the version number to the new
  current release.
* Commit those two files. The commit message should be: `Released vX.X`
* Run ``git tag -a X.X`` where ``X.X`` is the new current release.
* Add ``vX.X`` as a message for that tag.
* Push your changes.

At this point the new release is done on Github. The new tag signals to fellow
developers that the master branch at this tag is stable and save to use. Now it 
is time to upload this release to PyPi:

* Remove the ``dist`` and ``package.egg.info`` folders
* Run ``python setup.py sdist``
* Have a very close look at all the files. Make sure that there are no unwanted
  HTML files (i.e. from the coverage folder) or other unwanted files, such as
  ``*.pyc`` or ``.ropeproject``. If this is the case, you need to improve the
  ``MANIFEST.in`` file, and repeat the last three steps.
* Also make sure that there are no missing files, such as HTML files of
  ``templates`` folder that you have newly added or ``*.md`` files for online
  documentation. By default the ``MANIFEST.in`` only includes all ``*.py``
  files recursively below the package name. Anything else must be added
  explicitly.
* When the files included in the distribution look good, run ``python setup.py
  sdist upload``
* Celebrate your new release!

Please note that at this point your projects of course do not yet profit from
the new release. As we usually create new releases in order to fix a customers
request, there is one last step left:

* Update ``requirements.txt`` files of projects that need the new release and
  deploy those projects.
