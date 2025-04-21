# Packaging and distribution

## Packaging

Distributing Python tools to a broader audience can be time consuming and complex. But there is a large set of FOSS tools available to help you with packaging and distribution. 


Packaging of python programs is a well known way of distributing your python tools. 


Distribution of source code is very different from distribution of a working program. 

:::{admonition} Go for simple distribution whenever possible!
:class: tip, dropdown

Cases when simple distribution of your python source code is enough:
* Users are able to run python code.
* Users are novice or advanced python engineers that can use your code in their own programs or build new functionality for it.
 

Simple distribution of Python code can be done: (from simple to complex):
* Place your code in a gist.
* Place your code in a git repository on the internet and create a README file how to run the code.
* Use a notebook to distribute your code. 

:::

:::{tip}
Using a notebook for distribution of some code is simple. With JupyterLite only a web browser is needed. See [Mastering JupyterLab](https://nocomplexity.com/documents/jupyterlab/intro.html) for more information.
:::

### Directory structure for packaging

To package your code follow this simple directory structure:
```
project_name/
│
├── project_name/        # Main package
│   ├── __init__.py      # Makes the directory a Python package
│   ├── module1.py       # Core modules
│   ├── module2.py       # Core modules
│   ├── utils.py         # Helper functions
│   └── ...              # Additional package files
│
├── tests/               # Test suite
│   ├── __init__.py      # Optional, makes it a package
│   ├── test_module1.py  # Tests for module1
│   ├── test_module2.py  # Tests for module2
│   └── ...              # Additional test files
│
├── scripts/             # Command-line scripts or utilities
│   ├── script1.py
│   ├── script2.py
│   └── ...
│
├── docs/                # Documentation
│   ├── index.md
│   └── ...              # Additional documentation files
│
├── setup.py             # Package installation configuration (if publishing)
├── pyproject.toml       # Modern build configuration file (PEP 518)
├── requirements.txt     # List of dependencies
├── README.md            # Project overview
├── LICENSE              # License file
├── .gitignore           # Git ignore file
└── .env                 # Environment variables (optional)
```

:::{note}
* For Small Projects: Use `project_name/` to keep things simple.
* For Large or Complex Projects: Use `/src/` to prevent accidental import issues and align with best practices for distribution.
* For Distributable Libraries: Follow the `/src/` structure as recommended by the Python Packaging Guide.
:::


:::{admonition} Use the Python Packaging Guide for help!
:class: tip

[Python Packaging User Guide](https://packaging.python.org/en/latest/)

This guides gives you the guarantee that you are packaging and distribute your Python code with the latest tools as developed and supported by the PSF. This guide is well maintained. 
:::


A lot of FOSS packages are distributed using pip. Source code is often on on a git repository, but downloading a package gives you the source code.

If you want to adjust a FOSS package for your own use case:
1- Clone the repository.
2- Make your adjustments on the now local project source by doing: 
```
pip install -e path/to/SomeProject
```

The pip `-e` option is to install a project in editable mode from a local project path.


:::{tip}
A nice open access learning book involving all process steps for packaging a Python module is:
[pyOpenSci Python Package Guide](https://www.pyopensci.org/python-package-guide/index.html)

It covers not only packaging, but also how to create test scripts and documentation. And it uses `Hatch`, the new modern standard tool to create packages.
:::


:::{tip}
Besides using the Python default tools there are other ways and great tools for packaging. Check e.g.:
* [HATCH](https://hatch.pypa.io/latest/) Hatch is a modern, extensible Python project manager. Standardized build system with reproducible builds by default.
*  [Mamba](https://mamba.readthedocs.io/en/latest/) or
* [uv](https://docs.astral.sh/uv/) A fast package and dependency manager created in RUSTlang. Imho hard to maintain or create an easy fix for non-rust lang developers. But try it out.
* [pex](https://docs.pex-tool.org/index.html). Tool to create Python Executables.
* [Shiv](https://shiv.readthedocs.io/en/latest/). Shiv is a command line utility for building fully self-contained Python zipapps as outlined in PEP 441 with all their dependencies included. Shiv’s primary goal is making distributing Python applications fast & easy.

:::

## Distribution

Sooner or later you must bundle your work and make it easily usable  for others. Even people with no python knowledge.

Some options are:
* Bundle your software and make it installable using pip.
* Bundle your software and make it installable using conda
* Distribute your python executable(s) with a simple instruction on how it can be run.

Sometimes you make bug fixes to your software or enhancements. People who already have installed and configured your software should have an easy way to upgrade. And without losing all their specific configurations.

:::{tip}
Python upgrades can be handled automatically by `pip` and `conda`.
:::


