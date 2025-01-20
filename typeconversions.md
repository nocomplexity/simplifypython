# Type conversions

## Converting numbers to strings

If you have an integer or float number `i`, you can make a string out of it with `str(i)`:


```python
    text = str(2000)
```

Alternatively, you can insert variables into an f-string (since Python 3.6):


```python
number = 2000
text = f"the year is: {number}"
text
```




    'the year is: 2000'



## Type conversionsm

### Converting numbers to strings

If you have an integer or float number `i`, you can make a string out of it with `str(i)`:


```python
    text = str(2000)
```

Alternatively, you can insert variables into an f-string (since Python 3.6):


```python
    number = 2000
    text = f"the year is: {number}"
```

Format strings allow you to express floats with a given precision:

    


```python
    pi = 3.14159
    text = f"{pi:4.2f}"
```

### Converting strings to numbers

If you have a string `s`, you can make an integer out of it with `int(s)`:


```python
    number = int("2000")
    number
```




    2000



The same works for a float:

    


```python
    number = float("3.14159")
```

### Other type conversions

The functions `int()`, `float()` and `str()` change the type of the given data. They are therefore called **type conversions**. There is a *conversion functions* for each Python data type. Try the following:

    


```python
    int('5.5')
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[8], line 1
    ----> 1 int('5.5')


    ValueError: invalid literal for int() with base 10: '5.5'


Format strings allow you to express floats with a given precision:


```python
pi = 3.14159
text = f"{pi:4.2f}"
```



### Converting strings to numbers

If you have a string `s`, you can make an integer out of it with `int(s)`:


```python
number = int("2000")
number
```




    2000



The same works for a float:


```python
    number = float("3.14159")
```

### Other type conversions

The functions `int()`, `float()` and `str()` change the type of the given data. They are therefore called **type conversions**. There is a *conversion functions* for each Python data type. Try the following:

 


```python
    int('5.5')
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[14], line 1
    ----> 1 int('5.5')


    ValueError: invalid literal for int() with base 10: '5.5'



```python
    float(5)
```




    5.0




```python
    str(5.5)
```




    '5.5'




```python
    list("ABC")
```




    ['A', 'B', 'C']




```python
    tuple([1, 2, 3])
```




    (1, 2, 3)




```python
    dict([('A', 1), ('B', 2)])
```




    {'A': 1, 'B': 2}




```python
    set([1, 2, 2, 3])
```




    {1, 2, 3}


