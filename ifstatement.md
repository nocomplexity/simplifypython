# Conditional if statements

The `if` statement is used to implement decisions and branching in a program. One or more instructions are only executed if a condition matches:


```python
name = 'Emily'
if name == 'Emily':
    studies = 'Physics'
studies
```




    'Physics'



There must be an `if` block, zero or more `elif`'s and an optional `else` block:    


```python
    if name == 'Emily':
        studies = 'Physics'
    elif name == 'Maria':
        studies = 'Computer Science'
    elif name == 'Sarah':
        studies = 'Archaeology'
    else:
        studies = '-- not registered yet --'
```

Below is an example that demonstrates the Python syntax for an if-else control statement. For a value assigned to a variable x, the program prints a message and modifies x; the message and the modification of x depend on the initial value of x:



```python
x = -10.0  # Initial x value

if x > 0.0:  
    print('Initial x is greater than zero')
    x -= 20.0
elif x < 0.0:  
    print('Initial x is less than zero')
    x += 21.0
else: 
    print('Initial x is not less than zero and not greater than zero, therefore it must be zero')
    x *= 2.5

# Print new x value
print("New x value:", x)

```

    Initial x is less than zero
    New x value: 11.0


## Code blocks

After an `if` statement, all indented commands are treated as a code block, and are executed in the context of the condition.

The next unindented command is executed in any case.


## Comparison operators

An `if` expression may contain comparison operators like:


```python
a =1
b =2
```


```python
    a == b
    
```




    False




```python
    a != b
```




    True




```python
    a < b
```




    True




```python
    a > b
```




    False




```python
    a <= b
```




    True




```python
    a >= b
```




    False



On lists and strings you can also use:


```python
b = [1,3]
c = 2
d = 1
a in b
```




    True



Multiple expressions can be combined with boolean logic (`and`, `or`, `not`):

    


```python
    a or b
```




    1




```python
    a and b
```




    [1, 3]




```python
    not a
```




    False




```python
    (a or b) and not (c or d)
```




    False



## Boolean value of variables

Each variable can be interpreted as a boolean (`True`/`False`) value. All values are treated as `True`, except for:


```python
    False
```




    False




```python
    0
```




    0




```python
    []
```




    []




```python
    ''
```




    ''




```python
    {}
```




    {}




```python
    set()    
```




    set()




```python
    None
```
