---
author: shantanunarale
title: 2-Creating classes
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Classes, Class]
---

A class is basically a blueprint. When we instantiate a class we basically create an object of that class as example below.

```python
#2 - Creating classes

class Person:
    pass

p1 = Person()
p2 = Person()
print(p1)
# Output : <__main__.Person object at 0x000001D8E639EB10>
```
In the above example we created a class with name Person. p1 and p2 variables hold the object of Person. The way we instantiate a class (create object of class) is by using classname and followed by double parenthesis.
> In Python, classes follow Camel case naming convention like Person, BasketFruit etc.

In the output, as \_\_main\_\_ refers to the main file (the file we are working with) and also prints the memory address at which the object is created.

To intialize a class a special method called constructor is called. This method exists in the class even if you don't create one. We can create our own constructor like below.

```python
class Person_1:
    def __init__(self):
        pass

p3 = Person()
```
We have created `__init__` method (aka the constructor). This method would always take an argument self which refers to the object that is instantiated. 

> In Python, the methods that start with __ and ends with __ are called dunder methods. They have special purpose.

> **self** is just a naming covention of the first argument in all the instance methods in Python that refers to method taking instance of object as parameter. You can name anything other than self but its a best practise to name it self.

The above two classes are of not much use since we do not store any data. We would typically want to store the instance specific data in the attributes of a class. Below is the example of that.

```python
# Class with attribute

class Person_2:
    def __init__(self, name) -> None:
        self.name = name    
    
p4 = Person_2("Shantanu")
print(p4.name)
# Output: Shantanu
```

Here we have created an attribute name which is initialized when we instantiate the class. There are two things to notice with the above example.

- We do not need to pass any argument for self.
- We are able to access the attribute name outside the class as well.

We can also set the name outside the class as below or create a new attribute on the instance of the class. Howevem, doing this is not a preferred way and not a best practise and should be avoided.

```python
p4.name = "New Name"
p4.random = "Random"
print(p4.name, p4.random)
# Output : New Name Random
```