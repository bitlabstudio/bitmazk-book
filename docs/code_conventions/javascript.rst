JavaScript
==========

We try to make our JavaScript code look as close as possible to Python code.

Line length
-----------

JavaScript allows to easily break lines, so we should try to keep our lines
shorter than 80 characters.


Casing
------

Casing for variable names, classes, functions and constants should be the same
as in Python.


Quote marks
-----------

Like in Python, we always use single quote marks (``'``), unless the string
itself contains a single quote mark.

Example::

    $(document).ready(function() {
        $('#someId').hide()
        var foo = "Let's do it."
    });


Indentation
-----------

Like in HTML and in Python, we indent by four spaces::

    function my_function(foo) {
        if (foo===1) {
            return 1;
        }
    }


Lists
-----

JavaScript has the ugly pitfall that the last item of a list cannot be followed
by a comma. This can result in unnecessary bugs when someone inserts a new item
after the last item and forgets to add the missing comma. Therefore we prepend
the commas to the beginning of the list items::

    var mylist = [
        item1
        ,item2
        ,item3
        ,item4
    ]
