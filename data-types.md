# Data Types in Python

| data type | description | composite | mutable |
|-----------|-------------|-----------|---------|
| int       | integer numbers        | no | no |
| float     | floating-point numbers | no | no |
| string    | characters             | no | no |
| bool      | `True` or `False`      | no | no |
| list      | sequence of items      | yes | yes |
| tuple     | immutable sequence     | yes | no |
| dict      | lookup table           | yes | yes |
| set       | collection of unique items | yes | yes |
| NoneType  | just nothing           | no | no |

## Basic and composite data types

**Basic** means that a data type does not contain any other types. **Composite** means that a data type contains other types.

## Immutable and mutable data types

In Python there are basic and composite data types. The values of basic data types cannot be changed, they are **immutable**. Most of the composite data types are **mutable**.

The immutable data types in Python are:

* Boolean (`True` / `False`)
* Integer (`0`, `1`, `-3`)
* Float (`1.0`, `-0.3`, `1.2345`)
* Strings (`'apple'`, `"banana"`) - both single and double quotes are valid
* None (aka an empty variable)
* Tuples (multiple values in parentheses, e.g. `('Jack', 'Smith', 1990)`)

The mutable data types are

* List [1, 2, 2, 3]
* Dictionary {'name': 'John Smith', 'year': 1990}
* Set `{1, 2, 3}`

## Numbers

### Integer numbers

Numerical values without decimal places are called **integers** or **ints**. In Python, integers are a predefined **data type**.

      a = 42
      a
    

### Floating-point numbers

Numbers with decimal places are called **floating-point numbers** or **floats**.


```python
b = 42.0
b
```




    42.0




```python
pi = 3.14159
pi

```




    3.14159



### Arithmetical Operators

The arithmetical symbols like `+ - * /` connecting two numbers are called **operators**. In addition to the standard arithmetics a few other operators are available:

    


```python
a = 7
b = 4
```


```python
c = a - b
c
```




    3




```python
d = a * b      
d
```




    28




```python
e = a / b      
e
```




    1.75




```python
f = a % b      # modulo, 3
f
```




    3




```python
g = a ** 2     # 49  
g
```




    49




```python
h = 7.0 // b   # floor division, 1.0
h
```




    1.0



If you perform arithmetics with integer numbers, the result is also an integer. If one of the numbers is a float, the result will also be a float.
When you perform a division, the result is always a floating-point number.

## Rounding and binary representation

Occasionally, seemingly simple floating-point calculations will result in strange results, e.g. instead of `0.3` you might see:


```python
    
0.1 + 0.2
0.30000000000000004
```




    0.30000000000000004



This is related to the underlying binary representation of floating-point numbers. The precision of floats is by default 16 digits, which is enough for most applications (be aware that it might not, if you are doing astrophysics or other high-precision calculations).

(This happens in all programming languages that use floats with limited precision, but they might round the floats automatically.)

## Strings

Text values are called **strings**. In Python, strings are defined by single quotes, double quotes, triple-single or triple-double-quotes:


```python
    first = 'Emily'
    first
```




    'Emily'




```python
    first = "Emily"
    first
```




    'Emily'




```python
    first = '''Emily'''
    first
```




    'Emily'




```python
    first = """Emily"""
    first
```




    'Emily'




```python
last = 'Lastname String'
```

### Special characters

Some characters in Python require special attention:

| character | meaning |
|-----------|---------|
| `\n`      | Newline character |
| `\t`      | tabulator |
| `\\`      | normal, single backslash |

Additionally, Python 3 encodes **Unicode** characters including German Umlauts, Chinese and Arab alphabets by default. However, they may not be interpreted in the same way in different environments. Just be a bit careful when using them.

### String concatenation

The operator `+` also works for strings, only that it concatenates the strings. It does not matter whether you write the strings as variables or as explicit values.

With 


```python
first = 'Emily'
```

and


```python
last = 'Smith'
```

the following three statements have the same result:


```python
    name = first + last
    name
```




    'EmilySmith'




```python
    
    name = first + "Smith"
    name
```




    'EmilySmith'




```python
    name = "Emily" + "Smith"
    name
```




    'EmilySmith'



## Accessing single characters

Using square brackets, any character of a string can be accessed. This is called **indexing**. The first character has the index `[0]`, the second `[1]` and the fourth has the index `[3]`.


```python
    name[0]
```




    'E'




```python
    name[3]
```




    'l'



With negative numbers, you can access single characters from the end, the index `[-1]` being the last, `[-2]` the second last character and so on:


```python
    
    name[-1]
```




    'h'




```python
    name[-2]
```




    't'



Note that none of these modify the contents of the string variable.


## Creating substrings

Substrings can be formed by applying square brackets with two numbers inside separated by a colon (slices). The second number is not included in the substring itself.


```python
    
    name = 'Emily Smith'
```


```python
    name[0:5]
```




    'Emily'




```python
    name[1:4]
```




    'mil'




```python
    name[6:11]
```




    'Smith'




```python
    name[:3]
```




    'Emi'




```python
    name[-4:]
```




    'mith'



## String methods

Every string in Python brings a list of functions to work with it. As the functions are contained within the string they are also called **methods**. They are used by adding the `.` to the string variable followed by the method name.

Below you find a few of the available methods:

### Changing case


```python
    name = 'Manipulating Strings \n'
```


```python
    name.upper()
```




    'MANIPULATING STRINGS \n'




```python
    name.lower()
```




    'manipulating strings \n'



### Removing whitespace at both ends


```python
    name.strip()
```




    'Manipulating Strings'



### Cutting a string into columns


```python
    
    name.split(' ')
```




    ['Manipulating', 'Strings', '\n']



### Searching for substrings



```python
    name.find('ing')
    
```




    9



The method returns the start index of the match. The result -1 means that no match has been found.

### Replacing substrings

    


```python
    name.replace('Strings','text')
    
```




    'Manipulating text \n'



### Checking beginning and end of a string

Both of the following functions return a boolean:

    


```python
    name.startswith('Man')
```




    True




```python
    name.endswith('ings')
```




    False



## Tuples

A tuple is a sequence of elements that cannot be modified. They are useful to group elements of different type.


```python
        person = ('Emily', 'Smith', 23)
```

In contrast to lists, tuples can also be used as **keys** in dictionaries.


### Indexing tuples

Elements of tuples can be indexed in the same way as lists:


```python
    person[0]
```




    'Emily'




```python
    person[-2]
```




    'Smith'




```python
    person[1:]
```




    ('Smith', 23)



### Iterating over tuples

You can run a `for` loop over a tuple:


```python
for elem in person:
    print(elem)
```

    Emily
    Smith
    23


### Packing and unpacking tuples

Enumerating multiple values separated by a comma implictly creates tuples:


```python
        person = 'Emily', 'Smith', 23
```

Tuples can be unpacked to multiple variables:


```python
    first, last, age = person
```


```python
person
```




    ('Emily', 'Smith', 23)



It is even possible to swap the value of variables that way:


```python
    first, last = last, first
```


```python
person
```




    ('Emily', 'Smith', 23)



## Lists

A list is a Python data type representing a sequence of elements. You can have lists of strings:


```python
    names = ['Hannah', 'Emily', 'Madison', 'Ashley', 'Sarah']
    names
```




    ['Hannah', 'Emily', 'Madison', 'Ashley', 'Sarah']



and also lists of numbers:


```python
    numbers = [25952, 23073, 19967, 17994, 17687]
    numbers
```




    [25952, 23073, 19967, 17994, 17687]



### Accessing elements of lists

Using square brackets, any element of a list and tuple can be accessed. The first character has the index 0.


```python
print(names[0])    
print(numbers[3])
```

    Hannah
    17994


Negative indices start counting from the last character.


```python
   print(names[-1])
```

    Sarah


### Creating lists from other lists:

Lists can be sliced by applying square brackets in the same way as strings.

    


```python
names = ['Hannah', 'Emily', 'Sarah', 'Maria', 'Maikel']
names[1:3]
```




    ['Emily', 'Sarah']




```python
names[0:2]      
```




    ['Hannah', 'Emily']




```python
names[:3]
```




    ['Hannah', 'Emily', 'Sarah']




```python
names[-2:]
```




    ['Maria', 'Maikel']



### Copying a list

You can use slicing to create a copy:


```python
    girls = names[:]
    girls
```




    ['Hannah', 'Emily', 'Sarah', 'Maria', 'Maikel']



### Adding elements to a list

Add a new element to the end of the list:


```python
    names.append('Marilyn')
    names
```




    ['Hannah', 'Emily', 'Sarah', 'Maria', 'Maikel', 'Marilyn']



### Removing elements from a list

Remove an element at a given index:

    


```python
names.remove('Sarah')
```


```python
names
```




    ['Hannah', 'Emily', 'Maria', 'Maikel', 'Marilyn']



Remove the last element:


```python
   names.pop()
```




    'Marilyn'



### Replacing elements of a list

You can replace individual elements of a list by using an index in an assignment operation:

 


```python
names = ['Hannah', 'Emily', 'Sarah', 'Maria', 'Maikel']
print(names)
```

    ['Hannah', 'Emily', 'Sarah', 'Maria', 'Maikel']



```python
names[4] = 'Fiona'
print(names)
```

    ['Hannah', 'Emily', 'Sarah', 'Maria', 'Fiona']


### Sorting a list

 


```python
    names.sort()
```

The `itemgetter` module allows you to sort lists by a specific column.
E.g. to sort names by the 3rd  character:


```python
from operator import itemgetter
names.sort(key=itemgetter(2))
print(names)
```

    ['Emily', 'Hannah', 'Fiona', 'Maria', 'Sarah']


### Counting elements

    


```python
    names = ['Hannah', 'Emily', 'Sarah', 'Emily', 'Maria']
    names.count('Emily')
```




    2



### List comprehension

A powerful construct in modern languages, including Python, is list comprehension. It is a way to succinctly build lists from other lists. It can be very useful, but should be applied sensibly as it can sometimes be difficult to read. There is an optional extension exercise at the end of this notebook that uses list comprehension.

Say we have a list of numbers and we wish to create a new list that squares each number in the original list and adds 5. Using list comprehension:



```python
x = [4, 6, 10, 11]
y = [a*a + 5 for a in x]

print(x)
print(y)

```

    [4, 6, 10, 11]
    [21, 41, 105, 126]




To understand the meaning, read the statement left-to-right.

As another example, say we have a list of names and we want to

    build a new list of names that contains only the names with more than 5 characters; and
    for these names we want to add a full stop at the end.

Using list comprehension:



```python
lab_group1 = ["Roger", "Rachel", "Amer", "Caroline", "Colin"]
print(lab_group1)

group = [name + "." for name in lab_group1 if len(name) > 5]
print(group)

```

    ['Roger', 'Rachel', 'Amer', 'Caroline', 'Colin']
    ['Rachel.', 'Caroline.']


## Dictionaries

Dictionaries are unordered, associative arrays. They consist of key/value pairs. They are very versatile data structures, but more difficult to use than lists if you are new to Python. As the name implies, dictionaries are good for looking up things, or **searching** in general.


### Creating dictionaries

A Python dictionary (dict) is declared using curly braces or also called winged brackets. On the left side of each entry is the **key**, on the right side the **value**:


```python
    ratios = {
        'Alice': 0.75,
        'Bob': 0.55,
        'Charlie': 0.80
        }
```


```python
room_allocation = {"Adrian": None, "Laura": 32, "John": 31, "Penelope": 28, "Fraser": 28, "Gaurav": 19}
print(room_allocation)
print(type(room_allocation))

```

    {'Adrian': None, 'Laura': 32, 'John': 31, 'Penelope': 28, 'Fraser': 28, 'Gaurav': 19}
    <class 'dict'>




Each entry is separated by a comma. For each entry we have a 'key', which is followed by a colon, and then the 'value'. Note that for Adrian we have used 'None' for the value, which is a Python keyword for 'nothing' or 'empty'.

Now if we want to know which room Fraser has been allocated, we can query the dictionary by key:




```python
frasers_room = room_allocation["Fraser"]
print(frasers_room)
```

    28



```python
# Create empty dictionary
room_allocation_inverse = {}

# Build inverse dictionary to map 'room number' -> name 
for name, room_number in room_allocation.items():
    # Insert entry into dictionary
    room_allocation_inverse[room_number] = name

print(room_allocation_inverse)

```

    {None: 'Adrian', 32: 'Laura', 31: 'John', 28: 'Fraser', 19: 'Gaurav'}


### Accessing elements in dictionaries

By using square brackets and a key, you can retrieve the values from a dictionary. At least if the key is present:


```python
ratios['Alice']    # 0.75
ratios['Ewing']    # KeyError!
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    Cell In[144], line 2
          1 ratios['Alice']    # 0.75
    ----> 2 ratios['Ewing']    # KeyError!


    KeyError: 'Ewing'


### Retrieving values in a fail-safe way:

With the `get()` method you can assign an alternative value if the key was not found.

    


```python
ratios.get('Alice')
ratios.get('Ewing', 'sorry not found')
```




    'sorry not found'



### Changing values in a dictionary

The contents of a dictionary can be modified. For instance if you start with an empty dictionary:


```python
    persons = {}
```

Now you can add values one key/value pair at a time:


```python
    persons['Emily'] = 1977
```

### Setting values only if they dont exist yet:


```python
persons.setdefault('Alice', 1980)
persons.setdefault('Emily', 1898)
# for 'Emily', nothing happens
```




    1977



### Getting all keys or values:

 


```python
    ratios.keys()
    ratios.values()
    ratios.items()
```




    dict_items([('Alice', 0.75), ('Bob', 0.55), ('Charlie', 0.8)])



### Checking whether a key exists

The `in` operators checks whether a key exists in the dictionary.


```python
    if 'Bob' in ratios:
        print('found it')
```

    found it


Note that you can use `in` for the same with a list as well. The dictionary is **much faster**!


### Loops over a dictionary

You can access the keys of a dictionary in a `for` loop.


```python
for name in ratios:
    print(name)
```

    Alice
    Bob
    Charlie


However, there is no stable order unless you sort the keys explicitly:


```python
    for name in sorted(ratios):
        print(name)    
```

    Alice
    Bob
    Charlie


## Create dictionaries from lists


```python
k = ['Toy', 'Game', 'Tiger']
v = ['Toys', 'Games', 'Tigers']

#create dict
dc = dict(zip(k, v))
print(dc)
# {'Game': 'Games', 'Tiger': 'Tigers', 'Toy': 'Toys'}

d = dict(enumerate(v))
print(d)
# {0: 'Toys', 1: 'Games', 2: 'Tigers'}

```

    {'Toy': 'Toys', 'Game': 'Games', 'Tiger': 'Tigers'}
    {0: 'Toys', 1: 'Games', 2: 'Tigers'}


### What data can I use as keys?

Valid types for keys are:

* integers
* floats
* strings
* tuples
* booleans

You may mix keys of different type in one dictionary. However, **mutable** data types such as lists and other dictionaries are not allowed as keys.

The concept behind this phenomenon is that dictionaries use a **hash function** to sort the keys internally.
The hash function is what allows to look up values very quickly.
