# Python Tips

## The help function

You can get context-sensitive help to functions, methods and classes with help() function.

```python
import time
print(help(time.asctime))

Help on built-in function asctime in module time:

asctime(...)
    asctime([tuple]) -> string
    
    Convert a time tuple to a string, e.g. 'Sat Jun 06 16:26:11 1998'.
    When the time tuple is not present, current time as returned by localtime()
    is used.

None
```


`help()` utilizes the triple-quoted comments called **docstrings**, so that documentation you write for your own functions is also available through `help()`:


## Everything is an object

One consequence of the dynamic typing is that Python can treat everything it manages technically in the same way. **Everything is an object** is a common phrase describing how Python works. There is no fundamental difference between a function and an integer. Many advanced features of Python are built on this concept.


## Using the Python documentation

Even advanced programmers can not remember every little python function and usage by head. But a good programmer knows where to find the crucial information.

Of course the [Python Documentation](https://python.docs.org) are a good resource a faster way towards crucial documentation exist. 

It is `pydoc`. Pydoc usuage docstrings and since every good piece of python software makes use of docstrings using pdoc is the shortest path towards helpful information. 

The way to start pydoc for browsing documentation is:
```
pydoc -p [portnumber]

```
The pydoc module automatically generates documentation from Python modules. 

Pydoc command can be used within a notebook. But the most used way to display help of a function or module is typing:
```
help(function)
```
This invokes pydoc and displays the docstring (if used) on how a function should be used.



## Introspection

Introspection is a feature of Python by which you can examine objects (including variables, functions, classes, modules) inside a running Python environment (a program or shell session).

### Exploring the namespace

In Python all objects (variables, modules, classes, functions and your main program) are boxes called **namespaces**. You can imagine the namespace of an object as the data and functions inside than object. You can explore a namespace with the `dir()` function.

### Exploring the namespace of a variable

With a string object, you see all the string methods:

```python
s = "Emily"
print(dir(s))
```

Gives output:
```python
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```

### Exploring the namespace of a module:

The same works for a module you import:
```python
    import time
    print(dir(time))
```
Gives output:

```python
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```

## Listing the builtin functions

You also can view all builtin functions:

```python
print(dir(__builtins__))

['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException', 'BlockingIOError', 'BrokenPipeError', 'BufferError', 'BytesWarning', 'ChildProcessError', 'ConnectionAbortedError', 'ConnectionError', 'ConnectionRefusedError', 'ConnectionResetError', 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False', 'FileExistsError', 'FileNotFoundError', 'FloatingPointError', 'FutureWarning', 'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError', 'InterruptedError', 'IsADirectoryError', 'KeyError', 'KeyboardInterrupt', 'LookupError', 'MemoryError', 'ModuleNotFoundError', 'NameError', 'None', 'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError', 'OverflowError', 'PendingDeprecationWarning', 'PermissionError', 'ProcessLookupError', 'RecursionError', 'ReferenceError', 'ResourceWarning', 'RuntimeError', 'RuntimeWarning', 'StopAsyncIteration', 'StopIteration', 'SyntaxError', 'SyntaxWarning', 'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError', 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError', 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning', 'ValueError', 'Warning', 'ZeroDivisionError', '__IPYTHON__', '__build_class__', '__debug__', '__doc__', '__import__', '__loader__', '__name__', '__package__', '__spec__', 'abs', 'all', 'any', 'ascii', 'bin', 'bool', 'breakpoint', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'compile', 'complex', 'copyright', 'credits', 'delattr', 'dict', 'dir', 'display', 'divmod', 'enumerate', 'eval', 'exec', 'execfile', 'filter', 'float', 'format', 'frozenset', 'get_ipython', 'getattr', 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map', 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property', 'range', 'repr', 'reversed', 'round', 'runfile', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple', 'type', 'vars', 'zip']

```



## Get unique values from a list in python 

An all times hit on [Stackoverflow](https://stackoverflow.com/questions/12897374/get-unique-values-from-a-list-in-python) and on Google.




```python
# Suppose list is:
mylist = ['news', 'Security', 'Security', 'Blog', 'Blog', 'Foundation', 
          'MachineLearning', 'Blog', 'Blog', 'cc-by', 'cc-by', 'Security', 'Foundation', 
          'Security', 'Blog', 'MachineLearning', 'Blog', 'FOSS', 'Blog', 'FOSS', 'Blog', 'MachineLearning', 'Blog', 'Security', 'Foundation', 'Security', 
          'news', 'Security', 'Blog', 'ResearchBlog', 'Security']
```


```python
# The list sorted with unique values only is:
mylist = list(set(mylist)) # to make the list with unique values only!
```


```python
mylist
```




    ['news',
     'FOSS',
     'Foundation',
     'Security',
     'MachineLearning',
     'ResearchBlog',
     'cc-by',
     'Blog']

## Install a package from a local directory

It is not always needed to distribute a Python package on [https://pypi.org/](https://pypi.org/). There already too many packages published that are out-of-date or have never worked at all.


When you create a Python package for yourself or only to be used within your company you can easily install this package from a local directory. So distribution of a package can be done using git so anyone who is interested can just `git clone` your work.

To install a package from a local directory:
```python
pip install .  (or use the directory where it is installed)

Or do:

pip install -e . : for Edit mode, during package development.
```

This is a nice to make some local modifications of a cloned package.

Of course mind the environment you use for installation. 




## TIP: Update Python with conda for an environment

[Update Python Version using Conda](updatepython)
