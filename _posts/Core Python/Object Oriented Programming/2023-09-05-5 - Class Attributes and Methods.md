---
author: shantanunarale
title: 5-Class Attributes and Methods
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Cls, Class Methods, Class Attributes]
pin: true
---

Python supports the notion of class methods and class attributes. A class attribute is basically an attribute that is defined at the class level and is common to all the instances of the class. 

```python
class Person:
    # Class Attrinbute
    number_of_people = 0

    def __init__(self, name, age) -> None:
        self.name = name
        self.age = age

    @property
    def name(self):
        return self._name
    
    @name.setter
    def name(self, name):
        self._name = name.capitalize()

    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, age):
        self._age = age if type(age) is int else 0

```

In the above example, there is one class level attribute number_of_people which is initialized to zero. Take a note of how the attribute is not initialized inside the constructor but at the class level. The attribute is accessible across all the instances of class and can also be accessed using name of the class as shown below.

```python
# Access Class attribute using class
Person.number_of_people = 1
print(Person.number_of_people)
#Output : 1

# Accessing Class attribute using instance of a class
print(p1.number_of_people)
#Output : 1
print(p2.number_of_people)
#Output : 1
```

As you can see the class attribute is accessible by using the name of the class as well as using the instance created on the class p1 and p2. The attribute would show up the same value for each instance p1 and p2.

> Even thoough you can access class attribute using instance, it is advisable to access class attribute using class name as that is the preferred way in Python.

As a convention class attributes are always defined at the top of the class before any methods. If there is a class attribute and instance attribute with same name, the using the attribute name with instance would access the instance attribute and using attribute name with class name would access class attribute as below.

```python
class Person:
    # Class Attrinbute
    number_of_people = 0
    random = False

    def __init__(self, name, age) -> None:
        self.name = name
        self.age = age
        self.random = True


    @property
    def name(self):
        return self._name
    
    @name.setter
    def name(self, name):
        self._name = name.capitalize()

    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, age):
        self._age = age if type(age) is int else 0

p1 = Person("Shantanu", 32)
p2 = Person("Vibhuti", 32)
# Attribute with same name using class
print(Person.random)
# Output : False

# Attribute with same name using instance
print(p1.random)
# Output : True
print(p2.random)
# Output : True
```
Python allows you to modify the class attribute inside instance methods using class name. However, python also supports class methods to do the same operation.

```python
class Person:
    # Class Attrinbute
    number_of_people = 0
    random = False

    def __init__(self, name, age) -> None:
        self.name = name
        self.age = age
        self.random = True
        Person.number_of_people += 1

    @property
    def name(self):
        return self._name
    
    @name.setter
    def name(self, name):
        self._name = name.capitalize()

    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, age):
        self._age = age if type(age) is int else 0

print(Person.number_of_people)
# Output : 2
```

A class method is a specialized method that can be called using class name. Similar to class attribute you can use instance name as well to call the class method, however, using class name is the preferred way as below.

```python
import random

class Person:
    # Class Attrinbute
    number_of_people = 0
    random = None

    def __init__(self, name, age) -> None:
        self.name = name
        self.age = age
        self.random = True
        Person.number_of_people += 1

    @property
    def name(self):
        return self._name
    
    @name.setter
    def name(self, name):
        self._name = name.capitalize()

    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, age):
        self._age = age if type(age) is int else 0

    @classmethod
    def set_random(cls, num: int = None) -> None:
        if num == None:
            cls.random = random.randrange(0, 100)

        else:
            cls.random = num

Person.set_random()
p1.set_random()
print(Person.random)
#Output : random number
```

The first attribute for the class method is cls i.e. the class itself similar to self. You can access the class attribute using cls. You also need to decorate the class method using @classmethod decorator.

>cls is a convention other name can be given, however, preferred way is to use cls.

Class methods cannot access instance level attributes or methods, however, you can call a class method inside instance method.

Usage of class methods and class attributes is to store and operate on values those are common accross all the instances of the same class.