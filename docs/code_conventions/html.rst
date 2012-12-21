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


Casing
++++++

HTML tags and attributes are written in minor letters. CSS classes, names and
IDs are written in camelCase casing, starting with a minor letter.

Example::

    <h1 id="mainElement" name="mainElement" class="mainElement></h1>


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
ID, name and class are always the first attributes for a HTML tag.

Example::

    <img id="id_foo" name="foo" class="fooClass" src="..." />


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
