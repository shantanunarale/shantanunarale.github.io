---
author: shantanunarale
title: 10-Overloading
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Overload, dunder, magic method]
pin: true
---

All the operators within Python calls a specialized methods on the objects called as **dunder** methods or magic methods. If we override these methods we can define the way operators would work on our custom types. The important dunder methods are.

- \_\_add\_\_(self, other) : self is LHS and other is RHS. This overrides + operator
- \_\_sub\_\_(self, other) : self is LHS and other is RHS. This overrides - operator
- \_\_truediv\_\_ and \_\_floordiv\_\_ : truediv is for division / and floordiv for interger division //
- \_\_len\_\_ : This method is called in the len function
- \_\_str\_\_ : Provides string representation of the object
- \_\_repr\_\_ : similar to str, however, provides internal reprsentation of object
- \_\_eq\_\_ : overrides == operator, without this method python will only compare if two variables point to same object. If we override this, python starts to compare values based on the implementation.

```python
class Person:
    def __init__(self, fname, lname, age) -> None:
        self.first_name = fname
        self.last_name = lname
        self.age = age

    def __add__(self, other):
        return self.first_name  + " " + other.first_name + "|" + self.last_name + " " + other.last_name
    
    def __sub__(self, other):
        return f"The age difference is {self.age - other.age} years."
    
    def __len__(self):
        return len(self.last_name + self.first_name)
    
    def __str__(self):
        return self.first_name + " " + self.last_name + " " +str(self.age)
    
    def __repr__(self):
        return self.first_name + " " + self.last_name + " " +str(self.age) + str(id(self))
    
    def __eq__(self, other):
        return self.age == other.age
    
p1 = Person("Shantanu", "Narale", 32)
p2 = Person("Vibhuti", "Narale", 32)

print(p1 + p2)
print(p1 - p2)    
print(len(p1), len(p2))
print(p1, repr(p1), sep="\n")
print(p1 == p2)
```