# Steps for Packaging and Releasing

Creating an installable package should be done for:
* Distribution and
* Testing. Using a default structure for projects and using `python pip install -e.` ensures that the module you want under `pytest` is available in the namespace. This prevents messing with difficult imports when creating and running test for created modules.
* Installing from a remote repository like `gitlab` or `github`. OR:
* Installing from `pypy.org` 

## Basic Steps

Simple steps to start creating a structured project for packaging an existing Python project module.


### 1. Create an environment. 

This can be done with `hatch`. However I still prefer using `conda`.

   So do a:

   `conda create -n [PROJECTNAME] python=3.13` 
+++
   
   Recommended is to use the latest Python version.

   

### 2. Make pip up-to-date

After creating an environment make sure `pip` is up-to-date. So do a:

```
python3 -m pip install --upgrade pip
```

   

### 3. Install Hatch in the created environment

Within the created environment install `hatch`. So do:

```
   pip install hatch
```

   This will instal hatch only for the created environment. 

### 4. Create a standard directory structure (if needed)

Create a standard directory structure or do it **SIMPLE** by using `hatch new`:

   * **ONLY FOR NEW Projects**: Use `hatch new`  to create a small standard project directory.

   or create a directory manual. This is KISS without any overhead!

Using [Hatch new](https://hatch.pypa.io/latest/intro/): Start this command from the directory where the project_dir must be created. Typically `~/projects/` or `~/projects/python/`
```
hatch new -i PROJECTNAME
```


So the `hatch new` command created the directory and structure for this directory!

   The basic project directory should look like:

```
   pyospackage/
└─ pyproject.toml
└─ src/
   └── pyospackage/
       ├── __init__.py
       ├── add_numbers.py
```

So create an empty `__init__.py` file in the directory with the package name under `/scr`! Creating the file `__init__.py` is recommended because the existence of an `__init__.py` file allows users to import the directory as a regular package.

The `__init__.py` should contain a module-level docstring (enclosed in triple quotes """) that describes the package’s purpose. This docstring is displayed when using `help(my_package)` or accessing `my_package.__doc__`.

Optional is to use the Cookiecutter template. E.g. a nice one is `https://github.com/FlorianWilhelm/the-hatchlor` 

#### When using an existing directory:


 Use: `hatch new --init` to use a already created directory as packaging directory.
 
Hatch new will only create a project.toml file

When a toml file exist you can do a `pip install -e .` to install the package locally and/or use it in another Python programs.

**BUT this only works** after adjusting the `pyproject.toml` file!


Some defaults for `hatch` can and **should** be changed. The `hatch new` method can be customized by changing content in the hatch configuration file `config.toml`. Location: `/home/[username]/.config/hatch` - 

For customizing HATCH for other default, e.g. you SHOULD use `GPL` for a new project license instead of the `MIT` default.
So change in `config.toml`:
```
[template.licenses]
headers = true
default = [
    "GPL-3.0-or-later",
]
```

Check: https://hatch.pypa.io/latest/config/hatch/ 


## FAQ

### Why use Hatch?
With hatch, you no longer need to deal with files like requirements.txt, Pipfile or environment.yml, just configure everything in pyproject.toml. Thus, hatch is a sophisticated alternative to pipenv, poetry, conda, or direct virtualenv usage. Just think of hatch as a tool that allows you to easily define many isolated development environments, e.g. virtual but also docker environments, and helps you to manage them. A bit like what tox does for testing environments but for all kinds of environments, e.g. testing, linting your code, buildings your docs, and whatever you want.

### Adjusting PYPROJECT.TOML file

See: https://www.pyopensci.org/python-package-guide/tutorials/installable-code.html#step-4-modify-metadata-in-your-pyproject-toml-file 


### Does python pip install needs a pyproject.toml file?

No, `pip install` does *not* require a `pyproject.toml` file.  While `pyproject.toml` is becoming increasingly important in the Python packaging ecosystem, especially for specifying build-time dependencies and other metadata, it's not mandatory for simply *installing* packages.


* **Installing from PyPI (or other indexes):**  When you run `pip install some-package`, pip downloads the package from the Python Package Index (PyPI) (or a specified index) and installs it.  The package itself might have a `pyproject.toml` (if it uses a modern build system like Poetry or Hatch), but your *current* project (the one you're running `pip install` in) does *not* need one for the installation to succeed.

* **Installing from a local directory:** If you're installing from a local directory containing a package, pip will look for a `setup.py` file (the older standard) or a `pyproject.toml` (if the package uses a modern build system).  Again, your *current* project doesn't need a `pyproject.toml` for this.

* **Installing from a requirements.txt file:** `pip install -r requirements.txt` will install the packages listed in the `requirements.txt` file.  This file doesn't involve `pyproject.toml` at all.

* **When `pyproject.toml` is used:** `pyproject.toml` becomes relevant when you are *building* a package (creating a distribution like a wheel or sdist).  It's used to specify:
    * Build dependencies (what's needed to build the package itself).
    * Build system (e.g., setuptools, Poetry, Hatch).
    * Other metadata about the package.

**BUT** when a package is not yet made avaialable on pypi.org or somewehere else:  `pip install -e .` **needs** a pyproject.toml file. Else a package, even for local usuage can not be created!

**Summary:**  You can happily use `pip install` to install packages without having a `pyproject.toml` file in your project.  `pyproject.toml` is primarily for package *authors* who want to define how their packages are built and distributed.  It's not a requirement for package *users* who are simply installing packages.




### how to test with pytest when the test script is in a separate directory of the application

**1. Project Structure**

*   **my_application/:**
    *   `__init__.py`
    *   `module1.py`
    *   `module2.py`
    *   ... 
*   **tests/:**
    *   `__init__.py`
    *   `test_module1.py`
    *   `test_module2.py`
    *   ...

**2. `tests/test_module1.py`**

```python
import pytest
from my_application import module1 

def test_function1():
    # Arrange
    input_data = ... 
    expected_output = ...

    # Act
    actual_output = module1.function1(input_data) 

    # Assert
    assert actual_output == expected_output

def test_function2():
    # ... similar structure as test_function1 ...
```

**3. Running Tests with pytest**

*   Open your terminal and navigate to the root directory of your project (the directory containing `my_application` and `tests`).
*   Run the following command:

```bash
pytest
```

*   pytest will automatically discover and run all test files in the `tests` directory.

**Explanation**

*   **Import:**
    *   `from my_application import module1`: This imports the `module1` from the `my_application` package.
*   **pytest:** The `pytest` framework is used for writing and running tests.
*   **Test Functions:**
    *   Test functions are defined using the `def test_*()` naming convention.
    *   They follow the Arrange-Act-Assert pattern.
*   **Assertions:**
    *   Use `assert` statements to verify the expected behavior.

**Key Considerations**

*   **pytest.ini (Optional):** Create a `pytest.ini` file in the root directory to configure pytest behavior (e.g., markers, plugins).
*   **Test Coverage:** Use a coverage tool (e.g., `pytest-cov`) to measure how much of your code is covered by tests.
*   **Fixtures:** Use fixtures (`@pytest.fixture`) to share setup and teardown code across multiple tests.

This approach provides a clean and efficient way to organize and run your tests when they are in a separate directory from your application code.


To import just a single function from a package, you need to know which module inside the package defines that function. For example, if your package structure looks like this:

```
linkaudit/
├── __init__.py
└── utils.py  # contains the function 'check_links'
```

and you want to import the `check_links` function from `utils.py`, you can do it like this:

```python
from linkaudit.utils import check_links
```

If your function is defined in a module with the same name as the package (for example, `linkaudit/linkaudit.py`), you can import it with:

```python
from linkaudit.linkaudit import check_links
```

In either case, you're only importing that one function, not the entire package.

## Release Steps

### 1. Versioning

Just use hatch. This is simple and will not introduce other dependencies. Afterall: Releasing is a manual task, unless using e.g. automatic CI-CD tools on github and integration with `pypi`.

Tagging the git repository on a release can be done simple by by setting a `tag` in git. 

Set a tag in git:
```
git tag -a 0.0.1 -m "public beta release"
```

Push tags to remote (e.g. github, gitlab):
```
git push origin --tags 
```

Other more complicated ways in git, as setting a release are also possible.

Doing versioning in `Hatch` correct means adjusting `pyproject.toml`: So in when using `Hatch`, adjust `pyproject.toml`:

```
[project]
name = "linkaudit"
dynamic = ["version"]  # This tells Hatch that version is dynamically determined
```

**Also** Set in the file: ` __init__.py` :
```
from ._version import __version__
```


By default version information is stored in the file that is configured in `pyproject.toml` in Hatch. This is:
```
[tool.hatch.version]
path = "src/simplerss/__about__.py"
```
So version info is by default stored in this file. But this can be changed.
E.g to use `_version.py`, create this file and change the config to:

```
[tool.hatch.version]
path = "src/linkaudit/_version.py"
```

So a file _version.py is written with version info.


To retrieve the version by a CLI command -v do:
```
from linkaudit import __version__ 
```

And a function to the code if needed. E.g.:
```python
def display_version():
   """Prints the module version"""
   version = f'SimpliedNLP version: {__version__}'
   return version
```
Will do.

To set a new versionID after a fix or update:
Usage: 
`hatch version [OPTIONS] [DESIRED_VERSION]` 

See for for options : [https://hatch.pypa.io/latest/version/#display](https://hatch.pypa.io/latest/version/#display)

Common use and simple is: minor, fix or release



### 2. Security validation with Bandit

A minimal static security check is the least what is needed! For more complex modules more is needed!
A simple tool to use is [Bandit](https://nocomplexity.com/documents/securitysolutions/generatedfiles/bandit.html) is simple and straigtforward.

Installed bandit in a separate environment. With Python=3.13 version.
After installing:

```
bandit -r [SOURCEDIR] 
```

For a html output report:
```
bandit -r -f html [SOURCEDIR] > [module_name_check].html
```

Note: Bandit is not perfect, but no tool is! 

### 3. TEST Coverage

Simple is use the Pytest plugin. There are many other options available on PyPI, but this is the one I choose (for now). KISS and I already use Pytest

https://github.com/pytest-dev/pytest-cov 

To use this pytest plugin, install it first!
```
pip install pytest-cov
```
Or see: https://pypi.org/project/pytest-cov/ 

To get a report on test coverage:
```
pytest --cov=linkaudit tests/ 
```

To get a HTML report do:
```
pytest --cov=linkaudit --cov-report html:cov_html tests/
```



### 4. DEAD code checker

Simple way to check on code that can and **SHOULD** be removed is recommended.

Simple way is to use [Vulture](https://github.com/jendrikseipp/vulture)

So install this and run it on the code that is to be released as package.

```
pip install vulture
```

To run it, make sure the right directory for checking is given. E.g.:
```
vulture [SOURCE_DIR_TO_CHECK]
```



### 5. Create and Build Documentation

All public released software **SHOULD** have some minimal documentation.

#### The simple readme

If creating extensive documentation is too much work, or not yet needed. A **MUST** have is a readme.
A minimal readme file should contain:
* Installation
* Usage
* License
* Contributing
Recommended is to have a file `SECURITY.md` as separate file that outlines security aspects. If none apply, just state that.
An example of a simple [README file](https://github.com/nocomplexity/ultrafastrss/blob/main/README.md)


#### API Documentation

Building API documentation and create an online manual is little work.
Using [Jupyer Book](https://jupyterbook.org/en/stable/intro.html) does the heavy lifting. API documentation can be created using Sphinx. 

So Build the API documentation for all modules using:

```
sphinx-apidoc -o . /home/maikel/projects/pythondev/linkaudit/src/linkaudit
```

[Example of documentation created for a package that includes API documentation](https://nocomplexity.com/documents/linkaudit/intro.html)


### 6. Publish

A safe step is to first publish the package to TestPyPI:
* Make sure the version is correctly set. Else do `hatch version fix` for minor changes.
* Do a hatch build:
```
hatch build
```

And then:
```
hatch publish -r test 
```

**Test if the package installs in a new environment!!!**

Some , or often most dependencies will **not** work when installing a package from TestPYPI. To cover this and test your packages from TestPyPI do:

```
pip [install your_package] --index-url https://test.pypi.org/[name]/ --extra-index-url https://pypi.org/[name]/

```


## Updating an existing package on PYPI

1. Commit changes to `git`

2. Create a new version: `hatch version fix` for a fix version

3. Just do: `hatch publish` from the correct directory.

Example when updating `linkaudit` package on PYPI:

```
hatch publish
dist/linkaudit-0.9.2.tar.gz ... already exists
dist/linkaudit-0.9.4-py3-none-any.whl ... success
dist/linkaudit-0.9.2-py3-none-any.whl ... already exists
dist/linkaudit-0.9.4.tar.gz ... success

[linkaudit]
https://pypi.org/project/linkaudit/0.9.4/

```
