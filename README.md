# sphinx-tutorial
From: https://www.sphinx-doc.org/en/master/tutorial/index.html

This repository demonstrates the basic Sphinx documentation setup following the official Sphinx tutorial.

## Project Structure

- `lumache/` - Sample Python package for documentation
- `docs/` - Sphinx documentation source files
  - `conf.py` - Sphinx configuration
  - `index.rst` - Documentation home page
  - `usage.rst` - Usage documentation
  - `api.rst` - API reference
  - `Makefile` - Build commands for Unix/Linux/macOS
  - `make.bat` - Build commands for Windows

## Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Building Documentation

To build the HTML documentation:

```bash
cd docs
make html
```

The generated documentation will be in `docs/_build/html/`. Open `docs/_build/html/index.html` in your browser to view it.

## Features Demonstrated

- Basic Sphinx project setup with `sphinx-quickstart`
- reStructuredText documentation
- Autodoc extension for Python API documentation
- Autosummary extension for generating API summaries
- Navigation with table of contents (toctree)
- Cross-references and links
- Code examples and syntax highlighting

