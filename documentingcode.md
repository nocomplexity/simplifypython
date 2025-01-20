# Documenting Code 

Documenting code is vital. For yourself and maybe for others. 

The basic rule is:

:::{tip}
More is better. And simple short is better than extensive.
:::


The key is to follow [PEP 257](https://peps.python.org/pep-0257/) for Docstring Conventions.

## Functions and Methods

Python uses docstrings to document code. A docstring is a string that is the first statement in a package, module, class or function. These strings can be extracted automatically through the __doc__ member of the object and are used by pydoc. (Try running pydoc on your module to see how it looks.) Always use the three double-quote """ format for docstrings (per PEP 257). A docstring should be organized as a summary line (one physical line not exceeding 80 characters) terminated by a period, question mark, or exclamation point. When writing more (encouraged), this must be followed by a blank line, followed by the rest of the docstring starting at the same cursor position as the first quote of the first line. 

Two popular styles for documenting are Google style and NumPy style. The [Sphinx Napoleon plugin](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/index.html) supports two styles of docstrings: Google and NumPy. The main difference between the two styles is that Google uses indention to separate sections, whereas NumPy uses underlines. 

Use Google style. It's simple and more readable.

```python
def func(arg1, arg2):
    """Summary line.

    Extended description of function.

    Args:
        arg1 (int): Description of arg1
        arg2 (str): Description of arg2

    Returns:
        bool: Description of return value

    """
    return True
```
