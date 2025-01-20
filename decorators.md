# Decorators

Use of Python Decorators is **Not** prominently outlined in the most Python documentation and books. 

:::{admonition} What are decorators?
:class
Decorators are used for anything that you want to transparently "wrap" with additional functionality.
:::
Basic use cases:

* Timing functions
* Logging
* Synchronization

Writing decorators isn't simple at first. But it is not rocket science. It takes some effort to learn. Advanced programmers and professional Python programmers should use it.


Python decorators are a powerful and convenient way to modify or extend the behavior of a function or class method without permanently changing its definition. A decorator is essentially a function that wraps another function to add functionality or alter its behavior. 

:::{admonition} Relevant PEP
:class: tip, dropdown
For in depth information see:
[PEP 318 – Decorators for Functions and Methods](https://peps.python.org/pep-0318/)
Admonition with a custom header sample.
:::

## Key Concepts
1. **Functions are First-Class Objects**: In Python, functions can be passed as arguments, returned from other functions, and assigned to variables.
2. **Higher-Order Functions**: A function that accepts another function as an argument or returns a function is called a higher-order function.
3. **Closures**: A closure is a nested function that captures variables from its containing scope.

## How Decorators Work
A decorator is a function that takes a function as input and returns a new function with additional functionality.

## Basic Syntax

The `@decorator_name` syntax is used to apply a decorator to a function. It's equivalent to calling the decorator explicitly.

## Basic example


```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("\nHello NO|Complexity example!\n")

say_hello()
```

    Something is happening before the function is called.
    
    Hello NO|Complexity example!
    
    Something is happening after the function is called.



```python
# This is equivalent to:

def say_hello():
    print("\nHello NO|Complexity example!\n")    

say_hello = my_decorator(say_hello)
say_hello()

```

    Something is happening before the function is called.
    
    Hello NO|Complexity example!
    
    Something is happening after the function is called.


## Types of Decorators

### 1. **Function Decorators**
Function decorators are used to modify or extend the behavior of functions or methods.

Example: Logging the execution of a function:


```python
def log_execution(func):
    def wrapper(*args, **kwargs):
        print(f"Executing {func.__name__} with arguments {args} and {kwargs}")
        result = func(*args, **kwargs)
        print(f"Finished {func.__name__}")
        return result
    return wrapper

@log_execution
def add(a, b):
    return a + b

add(3, 5)
```

    Executing add with arguments (3, 5) and {}
    Finished add





    8



### 2. **Class Decorators**
Class decorators modify or enhance the behavior of classes.

Example: Adding attributes to a class:


```python
def add_class_attributes(cls):
    cls.greeting = "Hello, world!"
    return cls

@add_class_attributes
class MyClass:
    pass

print(MyClass.greeting)
```

    Hello, world!


### 3. **Built-in Decorators**
Python provides built-in decorators like:
- `@staticmethod`: Defines a static method.
- `@classmethod`: Defines a method that receives the class as its first argument.
- `@property`: Defines a property that can be accessed like an attribute.

## Using `functools.wraps`
When writing decorators, use `functools.wraps` to preserve the metadata (e.g., `__name__`, `__doc__`) of the original function.

Example:


```python
from functools import wraps

def my_decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print("Before the function call")
        result = func(*args, **kwargs)
        print("After the function call")
        return result
    return wrapper

@my_decorator
def nocx_hello(number=3):
    """simple print"""
    for i in range(number):
        print("\nHello NO|Complexity example!\n")   

nocx_hello()
```

    Before the function call
    
    Hello NO|Complexity example!
    
    
    Hello NO|Complexity example!
    
    
    Hello NO|Complexity example!
    
    After the function call


## Example: Timing a function



```python
import time

def timer(func):
    """
    A simple decorator to measure the execution time of a function.
    """
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"Execution time: {end_time - start_time:.4f} seconds")
        return result
    return wrapper

@timer
def my_slow_function():
    # Simulate a time-consuming operation
    sum_of_squares = 0
    for i in range(1000000):
        sum_of_squares += i * i
    return sum_of_squares

result = my_slow_function()
print(f"Result: {result}")
```

    Execution time: 0.0467 seconds
    Result: 333332833333500000


Explanation:

1. timer(func): This is the decorator function. It takes the func (the function to be timed) as an argument.
2. wrapper(*args, **kwargs): This is the inner function that will wrap the original function. It handles the timing logic.
3. @timer: This is the decorator syntax. It applies the timer decorator to the my_slow_function.

## Summary
Benefits of Decorators:

* Code Reusability: You can create reusable decorators for common tasks like logging, caching, authentication, etc.
* Improved Readability: Decorators can make your code more concise and easier to understand by separating concerns.
* Maintainability: Changes to the added functionality can be made in one place (the decorator) without modifying the original function.

So **Decorators add functionality** to existing functions or classes.
- They use higher-order functions and closures.
- The `@decorator_name` syntax makes them easy to use.
- Use `functools.wraps` to preserve the original function's metadata.
