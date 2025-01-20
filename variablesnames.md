# Naming variables

It is good practice to use meaningful variable names in a computer program. Say you used  '`x`' for time, and '`t`' for position, you or someone else will almost certainly make errors at some point.
If you do not use well-considered variable names:

1. You're much more likely to make errors.
1. When you come back to your program after some time you will have trouble recalling and understanding 
   what the program does.
1. It will be difficult for others to understand your program - serious program development is almost always a team effort.

Languages have rules for what characters can be used in variable names. As a rough guide, in Python variable names can use letters and digits, but cannot start with a digit.

Sometimes for readability it is useful to have variable names that are made up of two words. A convention is
to separate the words in the variable name using an underscore '`_`'. For example, a good variable name for storing the number of days would be 
```python
num_days = 10
```
Python is a case-sensitive language, e.g. the variables '`A`' and '`a`' are different. Some languages, such as
Fortran, are case-insensitive.

Languages have reserved keywords that cannot be used as variable names as they are used for other purposes. The reserved keywords in Python are:


```python
import keyword
print(keyword.kwlist)
```

    ['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']


If you try to assign something to a reserved keyword, you will get an error.

Python 3 supports Unicode, which allows you to use a very wide range of symbols, including Greek characters:


```python
θ = 10
α = 12
β = θ + α
print(β)
```

    22


Greek symbols and other symbols can be input in a Jupyter notebook by typing the LaTeX command for the symbol and then pressing the `tab` key, e.g. '`\theta`' followed by pressing the `tab` key.
