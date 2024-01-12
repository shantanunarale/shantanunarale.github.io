---
author: shantanunarale
title: 7-Type Conversions
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [casting, type cast, type, conversion]
---

To convert the value you can use functions like int(), float(), str() and bool() functions.

If you convert an empty string to Boolean it will evaluate to False. If string is not empty it will evaluate to True.

Similarly, bool(0) or bool(0.0) evaluate to false but any non zero value evaluate to True.

If the type conversion is not possible it will give ValueError. Like below gives ValueError
```python
y = int("4.7")
```

However, the below will result into int.
```python
y = int(4.7) # The answer is 4
```


If you convert Boolean to str, it gives string True or False.
```python
y = str(True) # Ouptut is True as string
```