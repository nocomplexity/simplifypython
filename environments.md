# Environments

Use [Conda](https://docs.conda.io/projects/conda/en/latest/index.html). It can do everything and more! Its mature, maintained, secure and battle tested at large!
Conda provides package, dependency, and environment management for any language. So not only Python.

Conda provides many commands for managing packages and environments. 

The default Python way for managing environments is [venv — Creation of virtual environments](https://docs.python.org/3/library/venv.html). Its part of the standard library. The venv module supports creating lightweight “virtual environments”, each with their own independent set of Python packages installed in their site directories. 

Whenever you check online for the best way of creating and managing environments for Python you will get an opionated answer. There is no best way. Every method has pro's and cons. It depends of you use case and what works best for you!

I use mostly `Conda`. `Conda` is well supported in all IDEs and has some extra advantages over the default Python 'venv` library. Especially for hacking on ML applications. Also many large FOSS Python projects use Conda.

:::{tip}
[Use the Conda Cheatsheet](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)
:::



## Background 

Some background info on common used tool and their differences: Conda, pip, virtualenv and venv:

* Conda: A powerful and versatile tool for managing both Python and non-Python packages and environments across various platforms. Excellent for data science and machine learning projects.
* pip: The standard package installer for Python. Primarily used for installing packages from PyPI.
* virtualenv: A popular third-party tool for creating isolated Python environments.
* venv: The built-in Python module for creating virtual environments, often considered a more modern and streamlined option.

| Feature | Conda | pip | virtualenv | venv |
|---|---|---|---|---|
| **Primary Function** | Package and environment management for any software | Package installer for Python packages | Creates isolated Python environments | Built-in Python module for creating virtual environments |
| **Focus** | Cross-platform package and environment management | Python-specific package management | Python-specific environment isolation | Python-specific environment isolation |
| **Package Sources** | Conda repositories (Anaconda, conda-forge) | Python Package Index (PyPI) | Primarily relies on PyPI | Primarily relies on PyPI |
| **Environment Creation** | Creates isolated environments for different projects or dependencies | Can be used within virtual environments to install packages | Creates isolated environments for different projects or dependencies | Creates isolated Python environments |
| **Dependencies** | Handles dependencies for both Python and non-Python packages | Primarily focuses on Python package dependencies | Primarily focuses on Python package dependencies | Primarily focuses on Python package dependencies |
| **Cross-platform Support** | Excellent cross-platform support (Windows, macOS, Linux) | Excellent cross-platform support | Excellent cross-platform support | Excellent cross-platform support |
| **Common Use Cases** | Data science, machine learning, deep learning (due to support for libraries like TensorFlow, PyTorch, NumPy) | General Python development, web development, scripting | General Python development, avoiding conflicts between projects | General Python development, avoiding conflicts between projects |

