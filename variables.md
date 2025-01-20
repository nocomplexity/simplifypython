# Variables operator precedence

## Introduction

In this section some very basic operators explained.


## Evaluating expressions: simple operators

We can use Python like a calculator. Consider the simple expression $3 + 8$. We can evaluate and print this by:


```python
3 + 8
```




    11



Another simple calculation is the gravitational potential $V$ of a body of mass $m$ (point mass) at a distance $r$ from a body of mass $M$, which is given by

$$
V = \frac{G M m}{r}
$$

where $G$ is the *gravitational constant*. A good approximation is $G = 6.674 \times 10^{-11}$ N m$^{2}$ kg$^{-2}$.

For the case $M = 1.65 \times 10^{12}$ kg, $m = 6.1 \times 10^2$ kg and $r = 7.0 \times 10^3$ m, we can compute the  gravitational potential $V$:


```python
6.674e-11 * 1.65e12 * 6.1e2 / 7.0e3
```




    9.59625857142857



We have used 'scientific notation' to input the values. For example, the number $8 \times 10^{-2}$ can be input as `0.08` or `8e-2`. We can easily verify that the two are the same via subtraction:


```python
0.08 - 8e-2
```




    0.0



A common operation is raising a number to a power. To compute $3^4$:


```python
3**4
```




    81



The remainder is computed using the modulus operator '`%`':


```python
11 % 3
```




    2



To get the quotient we use 'floor division', which uses the symbol '`//`':


```python
11 // 3
```




    3



## Operator precedence

Operator precedence refers to the order in which operations are performed, e.g. multiplication before addition.
In the preceding examples, there was no ambiguity as to the order of the operations. However, there are common cases where order does matter, and there are two points to consider:

- The expression should be evaluated correctly; and 
- The expression should be simple enough for someone else reading the code to understand what operation is being 
  performed.

It is possible to write code that is correct, but which might be very difficult for someone else (or you) to check.

Most programming languages, including Python, follow the usual mathematical rules for precedence. We explore this through some examples.

Consider the expression $4 \cdot (7 - 2) = 20$. If we are careless, 


```python
4 * 7 - 2
```




    26



In the above, `4*7` is evaluated first, then `2` is subtracted because multiplication (`*`) comes before subtraction (`-`) in terms of precedence. We can control the order of the operation using brackets, just as we would on paper:


```python
4 * (7 - 2)
```




    20



A common example where readability is a concern is 

$$
\frac{10}{2 \times 50} = 0.1
$$

The code


```python
10 / 2 * 50
```




    250.0



is not consistent with what we wish to compute. Multiplication and division have the same precedence, so the expression is evaluated 'left-to-right'. The correct result is computed from 


```python
10 / 2 / 50
```




    0.1



but this is hard to read and could easily lead to errors in a program. Better is to use brackets to make the order clear:


```python
10 / (2 * 50)
```




    0.1



Here is an example that computes $2^{3} \cdot 4 = 32$ which is technically correct but not ideal in terms of readability:


```python
2 ** 3 * 4
```




    32



Better would be:


```python
(2**3) * 4
```




    32



## Variables and assignment

The above code snippets were helpful for doing some arithmetic, but we could easily do the same with a pocket calculator. Also, the snippets are not very helpful if we want to change the value of one of the numbers in an expression, and not very helpful if we wanted to use the value of an expression in a subsequent computation. To improve things, we need *assignment*.

When we compute something, we usually want to store the result so that we can use it in subsequent computations. *Variables* are what we use to store something, e.g.:


```python
c = 10
print(c)
```

    10


Above, the variable `c` is used to 'hold' the value `10`. The *function* `print` is used to print the value of a variable to the output (more on functions later).

Say we want to compute $c = a + b$, where $a = 2$ and $b = 11$:


```python
a = 2
b = 11
c = a + b
print(c)
```

    13


What is happening above is that the expression on the right-hand side of the assignment operator '`=`' is evaluated and then stored as the variable on the left-hand side. You can think of the variable as a 'handle' for a value.
If we want to change the value of $a$ to $4$ and recompute the sum, we would just replace `a = 2` with `a = 4` and execute the code (try this yourself by running this notebook interactively).

The above looks much like standard algebra. There are however some subtle differences. Take for example:


```python
a = 2
b = 11
a = a + b
print(a)
```

    13


This is not a valid algebraic statement since '`a`' appears on both sides of '`=`', but it is a very common statement in a computer program. What happens is that the expression on the right-hand side is evaluated (the values assigned to `a` and `b` are summed), and the result is assigned to the left-hand side (to the variable `a`). There is a mathematical notation for this type of assignment:

$$
a \leftarrow a +b 
$$

which says 'sum $a$ and $b$, and copy the result to $a$'. You will see this notation in some books, especially when looking at *algorithms*.

### Shortcuts

Adding or subtracting variables is such a common operation that most languages provide shortcuts. For addition:


```python
# Long-hand addition
a = 1
a = a + 4
print(a)

# Short-hand addition
a = 1
a += 4
print(a)
```

    5
    5


> In Python, any text following the hash (`#`) symbol is a 'comment'. Comments are not executed by the program; 
> they help us document and explain what our programs do. Use comments in your programs.

For subtraction:


```python
# Long-hand subtraction
a = 1
b = 4
a = a - b
print(a)

# Short-hand subtraction
a = 1
b = 4
a -= b
print(a)
```

    -3
    -3


Analogous assignment operators exist for multiplication and division:


```python
# Long-hand multiplication
a = 10
c = 2
a = c*a
print(a)

# Short-hand multiplication
a = 10
c = 2
a *= c
print(a)

# Long-hand division
a = 1
a = a/4
print(a)

# Short-hand division
a = 1
a /= 4
print(a)
```

    20
    20
    0.25
    0.25

