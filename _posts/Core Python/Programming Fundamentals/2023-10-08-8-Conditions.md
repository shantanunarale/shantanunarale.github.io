---
author: shantanunarale
title: 8-Conditions
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [conditions]
---

Condition is an expression that evaluate to True or False. In the below example.

```python
cond = 2 == 3 # == is conditional and = is assignment operator
```

In Python, below would evaluate to True, first value is float and second is int. 
```python
cond = 3.0 == 3
```
> In most programming languages this would evaluate to False, Python only cares of the literal value and this evaluates to True.

In Python != is a not equat to operator

Comparison Operators in Python.
- == Comparison
- != Not Equal to
- < Less Than Operator
- \> Greater Than Operator
- <= Less Than Equal to
- \>= Greater than Equal to

When you try to compare Int and String using \> or < operator, we get an error but == and != will evaluate to True or False.

```python
cond = 9 == "6"
print(cond) # This is False
cond = 9 != '6'
print(cond) # This is True
```

When you compare two strings, it is a case sensetive comparison.

```python
str1 = "Hello"
str2 = "hello"

cond = str1 == str2
print(cond) # Result is False
```
When you compare strings using \> or < operator, it makes an ascii comparison. To get the ASCII value of character, Python has ord() function and chr() functions.
- ord() function (stands for ordinal) returns the ascii of the charcter passed in.
- chr() function (stands for char) returns the char of ascii number.
```python
print(ord('H')) # Output is 72
print(chr(72)) # Output is H
```

When you compare two strings with \> or <, the charachter by character comparison happens, if first char of string is same, we compare next, once they are not equal, the output of True or False is printed.

Example

```python
x = "ABc"
y = "ABC"

cond = x > y
'''In this case, start the comparison of A, they are same, then move on to B, then move on to c, since ascii of c is greater than C, the result is True'''
```

Strange Comparison.
- In Python, 1 == True is True and 0 == False is False. Similarly any number other than 1 like 5 == True is false
- In Python, 0 == "" is False and so is 1 == "" as they are different data types.
- In Python, True == "True" is False as they are different types.