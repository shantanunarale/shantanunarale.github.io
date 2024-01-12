---
author: shantanunarale
title: 10-Conditionals
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [if, elif, else]
---

Python supports if, elif and else statement that can be used to implement conditional programing. The syntax is based on the indentation. Below is the syntax of if in Python.

```python
x = int(input("Enter an integer: "))

if x < 5:
    print("Too Small....")
elif x < 10:
    print("Small...")
elif x < 15:
    print("Average...")
else:
    print("Good")
```

The syntax is based on the indentation. After if, the next line needs to have 4 spaces (or a tab). We can add nesting of multiple if statements but all the if statements should follow the indentation as desired. There also is a shorthand version of if statement as below.

```python
x = int(input("Enter an integer: "))

y = "Good..." if x > 10 else "Bad"
print("Good...") if x > 10 else print("Bad...")
```

This syntax is mostly used for assignment but can also be used standalone. Below are few more things related to if.

- There can be multiple elif statements.
- else after elif is optional.
- we can also have standalone if statement.