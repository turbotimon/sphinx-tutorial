# sphinx-tutorial

From: https://www.sphinx-doc.org/en/master/tutorial/index.html

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


