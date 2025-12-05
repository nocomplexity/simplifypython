# Python Cheatsheet

## Main

```python
if __name__ == '__main__':    # If file is not imported, this will be executed
    main()
```

## Basic and necessary commands needed to execute a well-defined python code at the command line.

### Opening a python shell.

```python
$ python
```

### Installing a package

```python
$ pip install <package-name>
```

### Running a python script

```python
$ python <filename>.py
```

### Calculating the time of execution

```python
$ time python <filename>.py
```

### Importing a py script

```python
import <filename>
```

## Getting started with the language

### Basic I/O

- Input

```python
input("Input: ")
```

- Output
  Python automatically points the cursor to a new line.
  We need not specify explicitly.

```python
print("Output")
```

### Variables and Constants

In python, we need not specify the datatype of a variable.
The interpreter interprets the value and assigns a suitabe datatype for that.

```python
number = 0
org = "GitHub"
```

### Conditional Statements

In python, we do not write a block of code in a pair of paranthesis.
We write it after `:` followed by an indentation in the next line.

The conditional statements include `if`, `if-else`, `nested if` and so on...

```python
x,y = 0,1
if x < y:
  print("x is less than y")
else:
  print("x is not less than y")
```

Note that the colon (:) following <expr> is required.
Similarly, the `nested if` also works.

### Iterative statements

As other programming languages, we have

- `for loop`

```python
for i in range(5):
  print(i)
```

The `range` function starts off with 0 till the number(excluded).

- `while loop`

```python
i=0
while(i < 10):
  print("{} is less than 10".format(i))
  i += 1
```

### String formatting

There are a few ways to format a string in Python.

- Using the `%` operator
  Strings can be formatted using the % operator:

```python
>>> foo = 'world'
>>> 'Hello %s' % foo
'Hello world'
```

To subsitute multiple instances, wrap the right hand side in a Tuple:

```python
>>> foo = 'James'
>>> bar = 'Nancy'
>>> 'Hi, my name is %s and this is %s' % (foo, bar)
'Hi, my name is James and this is Nancy'
```

You can also do variable subsitutions with a dictionary:

```python
>>> dict = { "name": "Mike", "country": "Canada" }
>>> 'I am %(name)s and I am from %(country)s' % dict
'I am Mike and I am from Canada'
```

- `.format()`

Introduced in Python 3, but is available in Python 2.7+

```python
>>> 'Hello {}'.format('world')
'Hello world'
```

Similar to the above, subsitutions can be referred by name:

```python
>>> 'Hi {name}, your total is ${total}'.format(name='Bob', total=5.50)
'Hi Bob, your total is $5.5'
```

## f-Strings

Available in Python 3.6+. Works similar to the above, but is more powerful as arbitrary Python expressions can be embedded:

```python
>>> a = 5
>>> b = 10
>>> f'Five plus ten is {a + b} and not {2 * (a + b)}.'
'Five plus ten is 15 and not 30.'
```
More information: See the [section on f-strings in this Playbook](fstrings).

## Function

Function is a block of code which runs when it is called.  
Functions are declared using the `def` keyword. Function name must be a valid identifier.  
Function arguments can be literal values, variables (valid identifiers), and expressions.

```python
def sum(a, b) :
	return a + b

def subtract(a, b) :
	return a - b

def getPerson(name, age) :
	person = { "name": name, "age": age }
	return person
```

### Function Call

Functions can be called by passing the arguments according to the declaration.

```python
a = 20
b = 50
c = sum(a, b)
d = sum(b, 50)
e = subtract(b, a)
p = getPerson("Joe", 25)

# OUTPUT:
print( "Sum - {} plus {}: {}" . format( a, b, c ) ) # Sum - 20 plus 50: 70
print( "Sum - {} plus 50: {}" . format( b, d ) ) # Sum - 50 plus 50: 100
print( "Subtraction - {} minus {}: {}" . format( b, a, e ) ) # Subtraction - 50 minus 20: 30
print( "Person - {}" . format( p ) ) # Person - {'name': 'Joe', 'age': 75}
```

### Function as Object

All data in a Python is represented by objects. There’s nothing particularly special about functions. They’re also just objects.

```python
def yell(text):                   # Define function yell
	return text.upper() + '!'


>>> bark = yell                   # Declare an object "bark" that contains the function "yell"
>>> bark('woof')                  # You could now execute the "yell" function object by calling bark
'WOOF!'
```

### Nested Function

Functions can be defined inside other functions. These are often called nested functions or inner functions.

```python
def speak(text):                          # Define function speak
	def wisper(t):                    # Function wisper does not exist outside speak
		return t.lower() + '...'
	return wisper(text)


>>> speak('Hello, World')
'hello, world...'
```

## Lambda

The lambda keyword in Python provides a shortcut for declaring small anonymous functions.

```python
>>> add = lambda x, y: x + y
>>> add(5, 3)
8
```

You could declare the same add function with the def keyword, but it would be slightly more verbose:

```python
def add(x, y):
	return x + y
>>> add(5, 3)
8
```

## Data Structures

### Lists

```python
# These are all inplace operations returns a None value

<list>.append(<ele>)            # Add an element to the end of the list
<list>.sort()                   # Sorts the given list
<list>.pop([<ele>])             # Removes the last element if no argument else removes the element at the index given
<list>.clear()                  # Makes it an empty list
<list>.insert(<index>, <ele>)   # Adds the element before the index
<list>.extend(<iterator>)
<list>.reverse()                # Reverse a given list
```

```python
# These are not inplace operations and has a return value

<list>.copy()                   # Makes a shallow copy of the list
<list>.index(<ele>)             # Returns the index of the given element
<list>.count(<ele>)             # Returns the number of occurrences of the element
```

### Dictionaries

key-value pairs.

```python
<dict> = {'Google':100, 'Facebook':80, 'Apple':90}

<dict>['Amazon'] = 85                           # Adding a key along with the value

# Accessing the dictionary
for key in <dict>:
  print("{key} -> {x}".format(key=key, x=<dict>[key]))

<dict>.keys()                                   # Print all the keys
<dict>.values()                                 # Print all the values
len(<dict>)                                     # Find the length of the dictionary
<dict>.pop(<key>)                               # Removes the item with the specified key name
<dict>.copy()                                   # Make a copy of a dictionary
```

A dictionary can also contain many dictionaries, this is called nested dictionaries.

### Dictionary unpacking

A double asterisk `**` denotes dictionary unpacking. Its operand must be a mapping. Each mapping item is added to the new dictionary. Later values replace values already set by earlier dict items and earlier dictionary unpackings.

Originally proposed by [PEP 448](https://peps.python.org/pep-0448/).


#### Simple Dictionary Unpacking Example

1. Define the Function

```python
def make_sandwich(protein, cheese, sauce, extras=None):
    """Prints the ingredients of a customized sandwich."""
    
    sandwich = f"A {protein} sandwich"
    
    if cheese:
        sandwich += f" with {cheese}"
    
    if sauce:
        sandwich += f" and {sauce} on it"
        
    if extras:
        sandwich += f" (plus {extras})"
        
    print(sandwich)
```


2. Define the Configuration Dictionary

We create a **dictionary** where the **keys** match the **keyword argument names** of the function (`protein`, `cheese`, `sauce`, etc.).

```python
# Our sandwich configuration stored in a dictionary
sandwich_settings = {
    'protein': 'turkey',
    'cheese': 'provolone',
    'sauce': 'mayo',
    'extras': 'lettuce and tomato'
}
```

3. Use the Unpacking Operator (`**`)

We call the function and use `**` to unpack the dictionary. The `**` operator turns the dictionary's key-value pairs into individual keyword arguments.

```python
# Unpack the dictionary into keyword arguments
make_sandwich(**sandwich_settings)
```

**Output:**

```
A turkey sandwich with provolone and mayo on it (plus lettuce and tomato)
```

**What the `**` Does**

The line `make_sandwich(**sandwich_settings)` is functionally equivalent to writing:

```python
make_sandwich(
    protein='turkey',
    cheese='provolone',
    sauce='mayo',
    extras='lettuce and tomato'
)
```

The `**` operator is a clean way to pass a dynamic or pre-configured set of arguments to a function.


### Tuple

A tuple is a collection which is ordered, indexed and unchangeable. In Python tuples are written with round brackets.

```python
this_tuple = ('books', 'pen', 'paper')          # Defined a tuple

# Accessing Tuple Items
print(this_tuple[2])                            # paper
```

#### Changing Tuple Values

Tuples are immutable, which means they cant to changed once they are created.  
If a value inside tuple needs to be changed, the tuple must be converted to a list.  
Newly created list can be converted back to tuple after updating changes.

```python
desk_tuple = ("pen stand", "plant", "marker")
desk_list = list(desk_tuple)
desk_list[2] = "highlighter"
desk_tuple = tuple(desk_list)

print(desk_tuple[2])                            # highlighter
```

#### Creating tuple with one item

To create a tuple with only one item, you have to add a comma after the item, otherwise Python will not recognize it as a tuple.

```python
this_tuple = ("Python",)
print(type(this_tuple))                         # tuple

# NOT a tuple
this_tuple = ("Python")
print(type(this_tuple))                         # str
```

#### Deleting a tuple

Tuples are unchangeable, so you cannot remove items from it, but you can delete the tuple completely:

```python
this_tuple = ('books', 'pen', 'paper')
del this_tuple
print(this_tuple)                               # ERROR: this_tuple is not defined