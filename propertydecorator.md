# The `@property` Decorator

## Introduction

See also [https://docs.python.org/3/library/functions.html#property](https://docs.python.org/3/library/functions.html#property)


The `property` is a [built-in Python function](https://docs.python.org/3/library/functions.html#built-in-functions).

The `@property` decorator in Python is used to define getter methods in a class, allowing attribute access to be controlled without breaking encapsulation. It enables us to define a method that can be accessed like an attribute, making the code more readable and maintainable.


## Why Use `@property`?
- **Encapsulation**: Protects class attributes from direct modification while allowing controlled access.
- **Readability**: Allows method calls to look like attribute access.
- **Dynamic Properties**: Computes values dynamically without changing the interface.

## Basic Example


```python
class Person:
    def __init__(self, name, age):
        self._name = name
        self._age = age

    @property
    def age(self):
        return self._age

p = Person("Alice", 30)
print(p.age)  # Accesses the method like an attribute
```

    30


## Using `@property` with Setter and Deleter

### Adding a Setter
We can define a setter method using `@<property_name>.setter` to allow modification of the property.


```python
class Person:
    def __init__(self, name, age):
        self._name = name
        self._age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age cannot be negative")
        self._age = value

p = Person("Alice", 30)
p.age = 35  # Updates age
print(p.age)  # Output: 35
```

    35


### Adding a Deleter
We can also define a deleter method using `@<property_name>.deleter`.


```python
class Person:
    def __init__(self, name, age):
        self._name = name
        self._age = age

    @property
    def age(self):
        return self._age

    @age.deleter
    def age(self):
        print("Deleting age...")
        del self._age

p = Person("Alice", 30)
del p.age  # Calls the deleter
```

    Deleting age...


## Read-Only Property
If we only define the `@property` method and do not include a setter, the attribute becomes read-only.


```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        return self._radius

c = Circle(5)
print(c.radius)  # Allowed
# c.radius = 10  # Raises AttributeError
```

    5


## Computed Properties
`@property` can be used to compute values dynamically.


```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height

    @property
    def area(self):
        return self.width * self.height

rect = Rectangle(4, 5)
print(rect.area)  # Output: 20
```

    20


## Summary

The `@property` decorator in Python is a powerful feature that enhances encapsulation, maintains a clean API, and allows computed properties. 

It helps to write clean and maintainable code.
