---
author: shantanunarale
title: 4-Variables and Printing
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [Printing, Print, Using Variable]
---

You can use print() function to print values on console in Python. For Example.

```python
print("hello")
print("hello", 5) # Op as hello 5
print("hello", 5, True) # Op as hello 5 True to a new line
```

- Multiple values in print are separated by space.
- At the end of print will print \n (new line char).
- To override \n and tell python to not print \n at end of print use end=
- To override seprator use sep=
- All the lines are executed sequentially in python one after the other.
```python
print(5, True, end=" | ")
print("tim")
# op is 5 True | tim

```
**While you define a variable in python you donn't need to specify the type like in C#**

To define a variable just write the name and value. Below is the proper pythonic way of declaring the variable.

```python
x = 3
print(x)
```

In the below example, when y is set to "hello" and num to y and when we change the value of y, the value of y is copied in num so output is hello 3

```python
x = 3
y = "hello"
num = y

print(x, y)
print (num)

y = x

print(y, num)
```

Rules for naming variables.

- [x] Name the variable appropriately with value that it will hold. Not with names like x1, x2, x3 etc.
- [x] Variable has to start with letter or _
- [x] Only number, _ or letter in variable name
- [x] In Python snake case (max_len) is preferred over Camel case (maxLen).
- [x] Do not start variable with upper case as classes start with upper case.
- [x] Variables are case sensetive.

```python
name = "Shantanu"
Name = "Shan"

print(name, Name)

''' Output is
Shantanu Shan
'''
```
