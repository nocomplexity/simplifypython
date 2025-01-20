# f-Strings

Variables and strings can be combined, using **f-strings**. f-strings contain placeholders with variable names and format characters. 

## What are f-strings?

f-strings are a powerful and convenient feature in Python that enhance the readability and maintainability of your code. They are the recommended method for string formatting in modern Python.

* Introduced in Python 3.6, f-strings allow you to easily format strings by including variables and expressions directly within the string using curly braces `{}`.
* They provide a concise and readable way to embed expressions within string literals.

Python **f-strings** (formatted string literals) provide a simple and concise way to embed expressions inside string literals. 

**Key advantages:**

* **Readability:** f-strings are more readable than older string formatting methods like `%` formatting or `str.format()`.
* **Conciseness:** They offer a more concise and elegant syntax.
* **Flexibility:** You can use arbitrary expressions within the curly braces, including:
    * Variables
    * Function calls
    * Arithmetic operations
    * Conditional expressions


## Syntax:

To use an f-string, prefix the string with the letter **`f`** or **`F`** and enclose the expressions or variables you want to include within curly braces `{}`.

```python
f"string with {expression}"
```

Details for using f-strings can be found in [PEP 701 – Syntactic formalization of f-strings](https://peps.python.org/pep-0701/)


## Examples

### Basic Usage
```python
name = "Alice"
age = 30

# Using f-strings to format the string
greeting = f"My name is {name} and I am {age} years old."

print(greeting)
```
Output:
```
My name is Alice and I am 30 years old.
```



```python
a=1
b=" a text string"
print(f'See how this works {a} and {b}')
```

    See how this works 1 and  a text string



```python
name = 'Roger'
number = 42
pi = 3.14159
```


```python
    print(f'Hello {name}')
```

    Hello Roger



```python
    print(f'Result: {number:6d}')
```

    Result:     42



```python
    print(f'{number:06d}')
```

    000042



```python
    print(f'{name:>20} {name:20}')
```

                   Roger Roger               




### Embedding Expressions
You can embed any valid Python expression inside the curly braces.

```python
x = 5
y = 10

# f-string with expressions
result = f"{x} + {y} = {x + y}"

print(result)
```

Output:

```
5 + 10 = 15
```

### Formatting Numbers
You can format numbers inside f-strings by adding formatting options after a colon `:` inside the curly braces.

```python
pi = 3.14159

# Limiting float to 2 decimal places
formatted_pi = f"Value of pi: {pi:.2f}"

print(formatted_pi)
```

Output:
```
Value of pi: 3.14
```

### Using f-strings with Dictionaries or Lists
You can also access elements from dictionaries and lists inside f-strings.

```python
person = {"name": "Alice", "age": 30}

# Accessing dictionary values in f-string
info = f"{person['name']} is {person['age']} years old."

print(info)
```

Output:
```
Alice is 30 years old.
```


```python
name = "Alice"
age = 30

greeting = f"Hello, my name is {name} and I am {age} years old." 
print(greeting)  # Output: Hello, my name is Alice and I am 30 years old.
```



### Complex expressions

```python
import math

radius = 5
area = math.pi * radius**2

print(f"The area of the circle is: {area:.2f}")  # Output: The area of the circle is: 78.54
```

## Remark

The older method .format() (prior to Python 3.6) is sometimes used for string formatting:

```
    a= 23.3
    b= 1.3
    print('{:6.3f}/{:6.3f}'.format(a, b))

23.300/ 1.300
```