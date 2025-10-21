# reStructuredText Help

## Comments

Comments in reStructuredText start with two periods (..) followed by a space. They can be placed anywhere in the document and will be ignored during rendering.

```
.. This is a comment and will not appear in the rendered document.
```

## Directives

Directives are block-level instructions in reStructuredText that tell Sphinx to do something special — insert content, render code, build a table, include files, etc.

```
.. directive_name:: optional argument
   :option: value

   content (optional)

.. note::
   This is a note directive.

.. image:: images/logo.png
   :alt: Project logo
   :width: 200px

```

Key points:

- Always begin with .. and end with ::.
- Options (indented, prefixed by :) must be indented consistently.
- Content (if any) is indented under the directive.

💡 Tip:  
Most directives come from Sphinx extensions, so when you enable new ones (like autodoc, todo, graphviz), they add their own custom directives too.

| Directive             | Purpose                                           | Example                                                    |
| --------------------- | ------------------------------------------------- | ---------------------------------------------------------- |
| `.. toctree::`        | Builds a table of contents and defines navigation | `rst .. toctree:: :maxdepth: 2`                            |
| `.. include::`        | Inserts another file’s content                    | `rst .. include:: intro.rst`                               |
| `.. image::`          | Embeds an image                                   | `rst .. image:: img/logo.png :width: 200px`                |
| `.. figure::`         | Like `image`, but adds captions                   | `rst .. figure:: img/plot.png   :caption: Example plot`    |
| `.. note::`           | Highlighted info box                              | `rst .. note:: Use Python 3.11`                            |
| `.. warning::`        | Warning box                                       | `rst .. warning:: Experimental feature`                    |
| `.. code-block::`     | Syntax-highlighted code block                     | `rst .. code-block:: python   print("Hello")`              |
| `.. literalinclude::` | Include and render an external code file          | `rst .. literalinclude:: ../src/main.py :language: python` |
| `.. automodule::`     | From autodoc — documents a Python module          | `rst .. automodule:: mymodule :members:`                   |
| `.. autoclass::`      | From autodoc — documents a class                  | `rst .. autoclass:: MyClass :members:`                     |
| `.. autofunction::`   | From autodoc — documents a function               | `rst .. autofunction:: my_func`                            |
| `.. math::`           | Render math (MathJax/LaTeX syntax)                | `rst .. math:: E = mc^2`                                   |
| `.. raw:: html`       | Insert raw HTML (for advanced customization)      | `rst .. raw:: html <hr>`                                   |
| `.. rubric::`         | Add a small section heading                       | `rst .. rubric:: Summary`                                  |
| `.. contents::`       | Auto-generated mini table of contents             | `rst .. contents:: :local:`                                |
| `.. sidebar::`        | Create a sidebar box                              | `rst .. sidebar:: Note   This is a sidebar.`               |

## Cross-references

### Overview

Cross-references create links between documentation elements (sections, code objects, pages).
Sphinx automatically resolves them — even if you rename files or reorganize docs.

```
:role:`target`

:role:`link text <target>`

See :ref:`installation guide <install-section>` for details.
```

| Role             | Purpose                                    | Example                                         | Notes                                                      |
| ---------------- | ------------------------------------------ | ----------------------------------------------- | ---------------------------------------------------------- |
| `:ref:`          | Link to a section label                    | ``rst See :ref:`install-section``               | Target defined with `.. _install-section:` above a heading |
| `:doc:`          | Link to another document                   | ``rst See :doc:`usage``                         | Uses file path (no extension)                              |
| `:any:`          | Try to resolve to any known target         | ``rst See :any:`MyClass``                       | Useful when mixing roles                                   |
| `:term:`         | Link to a glossary term                    | ``rst See :term:`API``                          | Requires a `.. glossary::` directive                       |
| `:pep:`          | Link to a Python PEP                       | ``rst :pep:`8``                                 | Auto-links to official Python PEP pages                    |
| `:rfc:`          | Link to an RFC                             | ``rst :rfc:`2616``                              | Auto-links to IETF RFC pages                               |
| `:download:`     | Link to a file for download                | ``rst :download:`Example <files/sample.zip>` `` | File must exist in source tree                             |
| `:mod:`          | Link to a Python module                    | ``rst :mod:`os``                                | Works with autodoc/imported modules                        |
| `:class:`        | Link to a documented class                 | ``rst :class:`MyClass``                         | Must be imported or autodoc’d                              |
| `:func:`         | Link to a function                         | ``rst :func:`my_package.do_something``          | Works for autodoc’d functions                              |
| `:meth:`         | Link to a class method                     | ``rst :meth:`MyClass.run``                      | Resolved via autodoc info                                  |
| `:attr:`         | Link to an attribute                       | ``rst :attr:`MyClass.value``                    | 〃                                                          |
| `:issue:`        | (if extension added) Link to issue tracker | ``rst :issue:`123``                             | Provided by 3rd-party extensions                           |
| `:doc:` + anchor | Link to specific section in another file   | ``rst :doc:`usage#advanced``                    | Works for Markdown (`myst_parser`) too                     |

### Defining Targets

To link to a specific place, add a label before a section:

```
.. _install-section:

Installation
============

Follow these steps to install the package.
```

Then link to it with `:ref:`:

```
See :ref:`install-section` for installation instructions.
```

✅ Tips:

- :ref: is the most robust for internal links — it survives file renames.
- For API docs, use domain roles like :class:, :func:, :mod:.
- With intersphinx, these roles can even link to external projects (like Python’s stdlib).

## Python

### Document Python Code

https://www.sphinx-doc.org/en/master/tutorial/describing-code.html#python

Example:

```
Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. py:function:: lumache.get_random_ingredients(kind=None)

   Return a list of random ingredients as strings.

   :param kind: Optional "kind" of ingredients.
   :type kind: list[str] or None
   :return: The ingredients list.
   :rtype: list[str]
```

### Doctest

- Extension `'sphinx.ext.doctest'`
- Enables testing of code snippets in the documentation.
- Code blocks marked with `.. doctest::` or just `>>>` are executed during the build process to verify correctness.
- The output of the code is compared against the expected output in the documentation.

Example:

```
>>> from lumache import get_random_ingredients
>>> from lumache import get_random_ingredients
['shells', 'gorgonzola', 'parsley'] # The expected output
```

# Syntax Cheatsheet

| Syntax            | Output              | Notes                              |
| ----------------- | ------------------- | ---------------------------------- |
| `*italic*`        | *italic*            | single asterisks                   |
| `**bold**`        | **bold**            | double asterisks                   |
| ` `inline code` ` | `inline code`       | for short code spans               |
| ``````            | `escaped backticks` | double for literal backtick        |
| ``:sub:`text```   | text                | Subscript (requires Sphinx role)   |
| ``:sup:`text```   | text                | Superscript (requires Sphinx role) |
| `\*escaped\*`     | *escaped*           | backslash escapes characters       |
| `.. note::`       | Note box            | directive for notes                |

Title Level 1
=============

Title Level 2
-------------

Title Level 3
~~~~~~~~~~~~~

Title Level 4
^^^^^^^^^^^^^

See also: https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html#restructuredtext-primer

...
