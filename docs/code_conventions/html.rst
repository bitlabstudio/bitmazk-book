HTML
====

General HTML
------------

* We indent by 4 spaces
* HTML tags and attributes are written in minor letters.
* Separate root level code via 2 lines
* Write IDs and class names as camelCase with small letter first.
* id and class are always the first attributes for a HTML tag

Django templates
----------------

* Code in main content blocks will not get further indented.
* When we have a for loop or if block in a Django template, the HTML
  markup inside that block will be further indented.
* ALWAYS wrap all string in {% trans "" %} tags.
* ALWAYS construct all URLs with the {% url "" %} tag
