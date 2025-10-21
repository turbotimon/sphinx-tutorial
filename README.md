# sphinx-tutorial

From: https://www.sphinx-doc.org/en/master/tutorial/index.html

## Manual setup

1. Install Sphinx

    ```nix
    let
    pkgs = import <nixpkgs> {};
    in with pkgs; mkShell {
    packages = [
        (python3.withPackages (python-pkgs: with python-pkgs; [
            sphinx
            sphinx-autobuild
            sphinx-rtd-theme
        ]))
    ];
    }
    ```

    ```sh
    sphinx-build --version
    # sphinx-build 8.2.3
    ```

2. Create documentation layout

    ```sh
    sphinx-quickstart docs
    ```
    
3. Build HTML documentation

    ```sh
    sphinx-build -b html docs docs/_build/html
    ```

    ```sh
    cd docs; make html
    ```

4. Next steps: https://www.sphinx-doc.org/en/master/tutorial/automatic-doc-generation.html

..but autopilot version is merges.
 - Manual see branch `manual-setup`
 - Autopilot see branch `setup-sphinx-demo-repo`
This repository demonstrates the basic Sphinx documentation setup following the official Sphinx tutorial.

## Useful extensions:

- `sphinx-autobuild`: Automatically rebuilds documentation on changes and serves it via a local web server. Run with `sphinx-autobuild docs docs/_build/html`.
- `sphinx-rtd-theme`: A popular Sphinx theme used by Read the Docs.

Some other (llm generated) useful extensions:

| Extension                     | Built-in? | Description                                      | Example Usage                                      |
| ----------------------------- | --------- | ------------------------------------------------ | -------------------------------------------------- |
| `sphinx.ext.autodoc`          | ✅ Yes    | Automatically generates API docs from docstrings | `rst .. automodule:: mymodule   :members:`         |
| `sphinx.ext.napoleon`         | ✅ Yes    | Supports Google & NumPy style docstrings         | `rst .. autofunction:: myfunc`                     |
| `sphinx.ext.viewcode`         | ✅ Yes    | Adds links to highlighted source code in docs    | Just enable; adds “View Source” links              |
| `sphinx.ext.todo`             | ✅ Yes    | Adds TODO items in docs                          | `rst .. todo:: Implement this feature`             |
| `sphinx.ext.coverage`         | ✅ Yes    | Reports docstring coverage for modules           | `bash make coverage`                               |
| `sphinx.ext.mathjax`          | ✅ Yes    | Renders math formulas with MathJax               | ``rst :math:`E=mc^2` ``                            |
| `sphinx.ext.intersphinx`      | ✅ Yes    | Links to docs of other projects                  | `python inv:python:dict`                           |
| `sphinx.ext.autosectionlabel` | ✅ Yes    | Allows referencing section titles                | ``rst :ref:`my-section-title` ``                   |
| `sphinx.ext.duration`         | ✅ Yes    | Measures how long each step of the build takes   | Output shown during `make html`                    |
| `sphinx.ext.autosummary`      | ✅ Yes    | Generates summary tables for modules/classes     | `rst .. autosummary:: mymodule`                    |
| `sphinx_rtd_theme`            | ❌ No     | Read the Docs theme                              | `python html_theme = "sphinx_rtd_theme"`           |
| `sphinx_autodoc_typehints`    | ❌ No     | Uses type hints in API docs                      | `python extensions = ["sphinx_autodoc_typehints"]` |
| `myst_parser`                 | ❌ No     | Allows Markdown instead of reStructuredText      | `python extensions = ["myst_parser"]`              |
| `sphinx_copybutton`           | ❌ No     | Adds “copy” button to code blocks                | No config needed; adds button automatically        |
| `sphinx_tabs`                 | ❌ No     | Tabbed content in docs                           | `rst .. tabs:: .. tab:: First`                     |

## Copilot generated

### Project Structure

- `lumache/` - Sample Python package for documentation
- `docs/` - Sphinx documentation source files
  - `conf.py` - Sphinx configuration
  - `index.rst` - Documentation home page
  - `usage.rst` - Usage documentation
  - `api.rst` - API reference
  - `Makefile` - Build commands for Unix/Linux/macOS
  - `make.bat` - Build commands for Windows

### Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Building Documentation

To build the HTML documentation:

```bash
cd docs
make html
```

The generated documentation will be in `docs/_build/html/`. Open `docs/_build/html/index.html` in your browser to view it.

### Features Demonstrated

- Basic Sphinx project setup with `sphinx-quickstart`
- reStructuredText documentation
- Autodoc extension for Python API documentation
- Autosummary extension for generating API summaries
- Navigation with table of contents (toctree)
- Cross-references and links
- Code examples and syntax highlighting

