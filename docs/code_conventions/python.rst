Python
======

Imports
-------
* Imports appear in the following order::

      python builtins (os, sys)

      main frameworks (django)

      other frameworks / 3rd party apps (milkman, registration)

      our own stuff (appname.models)


      [actual code]

* Never import ``*``
* When the import line gets too long, wrap it like so, again alphabetically::

      from foobar import (
          bar,
          foo,
      )

* Classes are listed alphabetically

Breaking lines
--------------

* Break long strings with brackets, each newline starts with a space::

      ('My super'
       ' long'
       ' string')

* Break long conditionals with brackets::

      if (this == that
          and that == this):
          foobar()
