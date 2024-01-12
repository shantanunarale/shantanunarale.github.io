---
author: shantanunarale
title: 6-Static Methods
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Static, static methods]
---

Python supports construct of static method. A static method is like a utility function within a class. A static method is similar to a class method except it does not even accept <u>**cls**</u> argument. Below is the example of static method.

```python
import datetime

class Person:
    number_of_people = 0

    @property
    def name(self):
        return self._name
    
    @name.setter
    def name(self, name):
        self._name = name if type(name) is str else ""

    @property
    def dob(self):
        return self._dob.strftime("%Y-%m-%d")            
    
    @dob.setter
    def dob(self, dob):
        var = dob.split("-")
        self._dob = datetime.date(int(var[0]), int(var[1]), int(var[2]))
    
    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, age):
        self._age = age
    
    def __init__(self, name, dob: str) -> None:
        self.name = name
        self.dob = dob
        self.age = Person.calculate_age(self._dob)

    @staticmethod
    def calculate_age(dob: datetime.date) -> int:
        today = datetime.datetime.now()
        age = max(0, today.year - dob.year - (1 if today.month > dob.month else 0))
        
        return age
    
p1 = Person("Shantanu", "1991-10-17")
print(Person.calculate_age(datetime.date(2023, 6, 1)))
print(p1.age)

```

As shown, we use decorator @staticmethod to define a static method. Static method cannot do anything beyond providing some utility.

> Theoratically, we can use static method and call class methods and class level attributes using class name like `Person.number_of_people` however, this is regarded as a bad practise.

A static attribute is same as class attribute and they are used interchanbly. Like class method a static method can be called from instance or by using the class name itself.