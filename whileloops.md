# Conditional loops with while

Another control flow statement is the **conditional loop** with `while`. While loops combine the properties `for` and `if`. The loop is executed as long as the conditional expression at the beginning holds. The conditional expressions work in exactly the same way as in `if` statements.

## Counting until a certain value

A simple usage of while is to count until an exit condition is met. The following loop calculates the sum of all numbers from 1 through 10:




```python
    i = 0
    total = 0
    while i < 10:
        print(i)
        i = i + 1
        total = total + i
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9


Another example:


```python
print("Start of while statement")
x = -2
while x < 5:
    print(x)
    x += 1  # Increment x
print("End of while statement")
```

    Start of while statement
    -2
    -1
    0
    1
    2
    3
    4
    End of while statement


###  break

Sometimes we want to break out of a for or while loop. Maybe in a for loop we can check if something is true, and then exit the loop prematurely, e.g.


```python
for x in range(10):
    print(x)
    if x == 5:
        print("Time to break out")
        break

```

    0
    1
    2
    3
    4
    5
    Time to break out


### continue

Sometimes we want to go prematurely to the next iteration in a loop, skipping the remaining code in the loop body. For this we use continue. Here is an example that loops over 20 numbers (0 to 19) and checks if the number is divisible by 4. If it is divisible by 4 it prints a message before moving to the next value. If it is not divisible by 4 it advances the loop.




```python
for j in range(20):
    if j % 4 == 0:  # Check remained of j/4
        continue  # jump to next iteration over j
    print("Number is not divisible by 4:", j)

```

    Number is not divisible by 4: 1
    Number is not divisible by 4: 2
    Number is not divisible by 4: 3
    Number is not divisible by 4: 5
    Number is not divisible by 4: 6
    Number is not divisible by 4: 7
    Number is not divisible by 4: 9
    Number is not divisible by 4: 10
    Number is not divisible by 4: 11
    Number is not divisible by 4: 13
    Number is not divisible by 4: 14
    Number is not divisible by 4: 15
    Number is not divisible by 4: 17
    Number is not divisible by 4: 18
    Number is not divisible by 4: 19


### pass

Sometimes we need a statement that does nothing. It is often used during development where syntactically some code is required but which you have not yet written. For example:




```python
for x in range(10):
    if x < 5:
        # TODO: implement handling of x < 5 when other cases finished 
        pass
    elif x < 9:
        print(x*x)
    else:
        print(x)
```

    25
    36
    49
    64
    9


## Searching through data

With a `while` loop you can perform search operations - although many times the methods on lists and dictionaries will give you a shortcut.

The following loop finds the first name starting with an `'E'`:


```python
    data = ['Alice', 'Bob', 'Charlie', 'Emily', 'Fred']
    i = 0
    while i < len(data) and not data[i].startswith('E'):
        i += 1
    print(i)
```

    3


## Waiting for user input

A `while` loop is also useful to let a user stop the program:

    


```python
    number = 0
    while input('press [Enter] to continue or [x] to exit') != 'x':
        number = number +1
        print(number)
```

    press [Enter] to continue or [x] to exit 2


    1


    press [Enter] to continue or [x] to exit 3


    2


    press [Enter] to continue or [x] to exit 4


    3


    press [Enter] to continue or [x] to exit x


## Endless loops

With `while` it is possible to build loops that never stop. Most of the time this happens by accident. In the following loop, the instruction to decrease `a` is missing. It runs endlessly:

    
    a = 10
    b = 1
    while a > 0:
        b = 1 - b
        print(b)
