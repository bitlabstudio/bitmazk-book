HTML
====

General HTML
------------

Line length
+++++++++++

Unfortunately it is not very easy to produce HTML that fits into lines of 80
characters. Therefore for HTML it is OK tp produce lines that are longer and
aim for code that has very consequent indentation.


Quote marks
+++++++++++

We use double quote marks (``"``) to wrap HTML tag attributes and templatetag
parameters.

Example::

    <h1 id="anAttribute">Foobar</h1>
    {% trans "This text is a templatetag parameter" %}


Indentation
+++++++++++

Almost everything should be indented by 4 spaces. The only exception are ``{%
block %}`` tags and ``{% blocktrans %}`` tags.

Example for a ``{% block %}`` tag::

    {% block main %}
    <body>
        <h1>First indentation</h1>
        {% for object in object_list %}
            {% if object.pk %}
                <p>{{ object.name }}</p>
            {% endif %}
        {% endfor %}
    </body>
    {% endblock %}


Example for a ``{% blocktrans %}`` tag::

    <ul>
        <li>
            {% blocktrans %}
            Hello world! This is a blocktransified text. And we use it when we
            want to translate a big block of text, that possibly spans multiple
            lines.
            {% endblocktrans %}
        </li>
    </ul>


Casing & class names
++++++++++++++++++++

HTML tags and attributes are written in minor letters. CSS classes, names and
IDs are written in as variables with dash in order to follow the naming
conventions of the Twitter Bootstrap CSS framework.

Example::

    <h1 id="unique-element" name="some-name" class="element-class"></h1>


Data attributes
+++++++++++++++

Never reference IDs, names or classes in JavaScript. The risk that someone
changes the class on an element and then accidentally breaks some JavaScript
is too big.

If you need to identify a unique element via JavaScript, use
`$('[data-id="element"]')` and give the element that attribute. If you need to
identify a group of elements use `$('[data-class="elements"]')`. In fact you
can use any attribute name in order to add specific settings that can be read
by your JavaScript to all elements. We just prepend `data-` to all those
attributes because Twitter Bootstrap does the same and because it is a good
convention to indicate that this attribtue is used by some JavaScript.


Code blocks
+++++++++++
Separate root level code via 2 empty lines.

Example::

    {% block main %}
        ...
    {% endblock %}


    {% block extrajs %}
        ...
    {% endblock %}


Ordering of attributes
++++++++++++++++++++++
ID, name and class are always the first attributes for a HTML tag. After that
come data-attributes and then everything else. For input elements, the type
shall come first.

Example::

    <img id="id_foo" name="foo" class="foo-class" data-id="foobar" src="..." />
    <button type="submit" name="btn-foo" ...>Submit</button>


Django templates
----------------

i18n
++++

Always wrap all string in ``{% trans "" %}`` tags.

Example::

    {% load i18n %}
    {% trans "Hello World!" %}


URLs
++++

Always construct all URLs with the ``{% url "" %}`` tag. Make sure to load url
from future.

Example::

    {% load url from future %}
    <a href="{% url "object_delete" pk=object.pk %}">Delete</a>
