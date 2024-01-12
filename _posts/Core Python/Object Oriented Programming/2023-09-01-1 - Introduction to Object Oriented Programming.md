---
author: shantanunarale
title: 1-Introduction to Object Oriented Programming
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Introduction to OOPS, OOPs, OOPS intro]
---

The concept of Object Oriented Programming is not specific to Python, infact, there are many languages like C, C++, C# that use same construct. 

**At its core Object Oriented Programming refers to interaction of objects in a program.** In Python, every thing is a object. For example a simple declaration like `x = 1` x variable is actually holding an object. The type of the object is int. 

```python
x = 1
print(type(x))
# Output: <class 'int'>
```

Everything in Python like string, list, tuple, None and even the function we create are objects of a specific class.

```python
def func():
    print("Do Nothing")

print(type(func))
# Output: <class 'function'>
```

A class is basically a blueprint of an object. It contains attributes and methods. Class in itself does not store any data, only when we **instantiate** (i.e. creating an instace of a class) and create an object of class it is stored in the memory.

```python
class Person:
    pass

p1 = Person()
p2 = Person()
print(type(p1))
# Output: <class '__main__.Person'>
print(id(p1), id(p2))
#Output: 2185743756624 2185743756688
```
Here, p1 and p2 are instances of Person class and in real world can respresent two different people.

In the above example, `type(p1)` gives output <class '\_\_main\_\_.Person'>. Here, \_\_main\_\_ refers file that we are executing.

In order to check if variable is of specific type you can use below code.

```python
print(type(p1) is Person)
# Output : True
```