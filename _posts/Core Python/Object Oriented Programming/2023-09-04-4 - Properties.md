---
author: shantanunarale
title: 4-Properties
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Class Properties, Properties, New Property syntax, Property Syntax]
pin: true
---

Although, you can directly access an attribute of a class outside the class, it is not a recomended way of working. It should be done through specialized methods called as getters and setters as shown in the below example.

```python
class Employee:
    def __init__(self, name, salary) -> None:
        self._name = name
        self._salary = salary

    def set_salary(self, salary):
        self._salary = 0 if salary < 0 else salary

    def get_salaray(self):
        return round(self._salary)

e1 = Employee("Shantanu", 10000)
e1._salary = -100 # This is a bad practise and shold be avoided
e1.set_salary(20000)
print(e1.get_salaray())
# Output : 20000
```
The class defined above has two attributes _name and _salary. These attributes can also be modified outside the class like we can set _salary to -100, however, this is not a valid salary. The logic for setting the salary is encapsulated within set_salary method and it should be used while setting the salary.

> In other programming languages, we have a notion of access modifier like private, public etc. A private attribute is something that can be accessed only within the class and not available outside the class. Python does not support access modifiers as such but we use convention _ before variable to denote that its a private attribute and should not be modified outside class.

The getter and setter methods are helping to encapsulate the logic that makes valid salary for the employee. However, we might not want to call these methods each time to access salary, instead want a way to set the salary like we set variable. This can be achieved through property.

There are two ways of creating properties. Below is the example of old way.

```python
class Employee:
    def __init__(self, name, salary) -> None:
        self._name = name
        self._salary = salary

    def set_salary(self, salary):
        self._salary = 0 if salary < 0 else salary

    def get_salaray(self):
        return round(self._salary)
    
    """This creates a property with name salary that has get_salary as getter and set_salary as setter."""
    salary = property(get_salaray, set_salary)

e1 = Employee("Shantanu", 10000)
e1._salary = -100 # This is a bad practise and shold be avoided
e1.set_salary(20000)
print(e1.get_salaray())
# Output : 20000

e1.salary = -100
print(e1.salary)
# Output : 0
```

Here we created a property name salary. The property keyword takes in two arguments getter method and setter method that we need to pass in to this argument.

Below is newer syntax to create property.

```python
class Employee_2:
    def __init__(self, name, salary) -> None:
        self._name = name
        self._salary = salary

    @property
    def salary(self):
        return round(self._salary)
    
    @salary.setter
    def salary(self, salary):
        self._salary = 0 if salary < 0 else salary

e2 = Employee_2("Shantanu", 10000)
e2.salary = -1000
print(e2.salary)
# Output : 0
```

The new syntax needs you to define the getter first and then use decorator @property. The setter should have same name as getter and should use @\<propertyname\>.setter decorator.

**A property encapsulates the logic to access a private attribute of a class.**