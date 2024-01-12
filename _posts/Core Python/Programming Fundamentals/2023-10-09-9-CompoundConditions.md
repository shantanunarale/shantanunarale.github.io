---
author: shantanunarale
title: 9-Compound Conditions
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [compount, conditions, logical conditions]
pin: true
---

Python Supports logical operators like and, or and not that can operate on the conditional operators to create complex conditions.

```python
x = 5
y = 7
cond = x + 2 == y and y - 2 == x # This is an example of complex condition
```
Python only supports three logical operators on conditions.
- and
- or
- not

The precedence goes as follows
1. Conditional/Comparison Opertor
2. Not
3. And
4. Or

The below condition works fine in Python.

```Python
a = True
b = False
cond = not a == b # condition a == b evaluate to false and not of False is True so output is True.
```

Hoeverver, below condition would fail in Python as condition is evaluated before applying not and gives a syntax error.

```Python
a = True
b = False
cond = a == not b # Generates syntax error here, to resolve use (not b)
```

> Below section is not part of the course

There are also some other type of operators that Python supports which are listed over here briefly.

## Bitwise operators
These operators work on int and bool. The bitwise operators do the logical operation on individual bit level. Below are the bitwise operators.

- ~ (Bitwise Not)
- ^ (Bitwise xor)
- & (Bitwise and)
- | (Bitwise or)
- \>\> (Bitwise rightshift) : Add zeros to the left. May increase the length of the number.
- << (Bitwise leftshift) : Right shift by number of digits.

On top of this, the bitwise operator (except bitwise not ~) and arithmetic operator can be combined with assignment operator to operate on the same variable as below.

```python
a = 5
a += 5
a -= 5
a >>= 2
a &= 2
a ^= 3
a //= 4
```
Also, when you add True to any int or False to any int you add 1 or 0 to it. Complete operator precedence is as below.

1. Parathesis or brackets ()
2. Exponent **
3. Unary operators +x, -x, ~x
4. Multiplication, Division / or // and modulas %
5. Addition + or Substraction -
6. Left shift or right shift << >>
7. Bitwise and &
8. Bitwise xor ^
9. Bitwise or |
10. Comparison, identity and membership like ==, != <=, is, is not, in, not in
11. Logical not
12. Logical and
13. Logical or