# sphinx-tutorial

From: https://www.sphinx-doc.org/en/master/tutorial/index.html

## Manual setup

1. Install Sphinx

    ```nix
    let
    pkgs = import <nixpkgs> {};
    in with pkgs; mkShell {
    packages = [
        (python3.withPackages (python-pkgs: with python-pkgs; [ sphinx ]))
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

