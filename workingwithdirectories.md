# Working with directories

## Importing the os module

Here, we will for the first time use a function that is not readily available in Python - it needs to be imported:


```python
    
    import os
```

`os` is the name of a module that is automatically installed with Python. It is simply not kept in memory all the time. This is why we need to import it.


## Listing files in a directory:

The function


```python
    y = os.listdir("/home/")
    y
```




    ['maikel']



gives you a list of all files in the directory `my_folder` and stores it in the variable `y`.


## Changing directories

With the os module, you can change the current directory:


```python
    import os
    os.chdir('../')
```

## Check whether a file exists


```python
    print(os.path.exists('my_file.txt'))
```

    False


## Check file modification time


```python
    import time

    t = os.path.getmtime('/home/maikel/.bashrc')
    gmt = time.gmtime(t)
    time.strftime("%Y-%m-%d, %H:%M:%S", gmt)
```




    '2021-11-09, 20:46:30'



## Overview

The table lists some frequently used functions in `os`:

| function | description |
|----------|-------------|
| `os.listdir(path)` | returns list of file names in `path` |
| `os.remove(path) ` | removes a file |
| `os.getcwd()     ` | returns current working directory |
| `os.path.exists(path)` | checks whether the given file or directory exists |
| `os.path.isdir(path) ` | checks whether the given path is a directory |
| `os.path.isfile(path) ` | checks whether the given path is a file |
| `os.path.getsize(path)` | returns file size |
| `os.path.getmtime(path)` | returns modification time |
| `os.path.split(path)` | cuts off the last dir/file name |
| `os.path.join(d1, d2, d3, ..)` | connects names by path separator |
| `os.environ[key]` | dictionary of environment variables |
| `os.system(cmd)` | executes shell command |
