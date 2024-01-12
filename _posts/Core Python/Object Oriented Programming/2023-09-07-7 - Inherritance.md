---
author: shantanunarale
title: 7-Inheritance
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Polymorphism, multi-level inheritance, duck typing]
pin: true
---

From coding perspective, it is always a best practice to re-use the existing code rather than duplicating the same logic. Inheritance lets us does the same. Inheritance is one of the fundamental construct of Object Oriented Programming that lets promotes code-reuse. In its most basic form, inheritance has at least two classes where in a functionality of one class can also be re-used and extended in its sub class. Below is the basic example of inheritance

```python
class Person:
    pass

class Employee(Person):
    pass

e = Employee()
```

In the above example, Employee class inherits Person class. There is another term associated with this that is called as Polymorphism. Poly means multiple and morphism means form. It states that one class can have multiple roles and is treated as per the context. In the above example, we can create an object of Person, however, it is also a base class for Employee and logic within this class is also re-used in Employee class.

> Python unlike many other programming languages also supports multiple inheritance.

Below is the basic syntax of Inheritance.

```python
# Inheritance

class Person:
    def __init__(self, fname, lname) -> None:
        self.first_name = fname
        self.last_name = lname

class Employee(Person):
    pass

e = Employee("Shantanu", "Narale")
print(e.first_name, e.last_name)
# Output: Shantanu Narale
```

As you can see in the above example, class Employee inherits from class Person. The reason for this is every employee in a company is a Person. The Person class has its own attributes *first_name* and *last_name*, if we would have not used the inheritance, we would have to define the attributes on the Employee class as well. Not only this, we can also re-use the methods in the Person class. 

In the above example, when we create object of Employee class we are passing in two parameters but these two parameters are of Person class and are needed whenever we create object of the subclass Employee.

```python
# Inheritance

class Person:
    def __init__(self, fname, lname) -> None:
        self.first_name = fname
        self.last_name = lname

    def test_method(self):
        print("Inside the test method.")

class Employee(Person):
    def test_employee(self):
        print("Inside Employee")

e = Employee("Shantanu", "Narale")
p = Person("Shantanu", "Narale")
e.test_method()
print(e.first_name, e.last_name)

e.test_employee()
# Output: Inside Employee
e.test_method()
# Output: Inside the test method.

p.test_method()
# Output: Inside the test method.
```

The above example has a method **test_method** which is in the Person class and the Employee class has another method **test_employee**. We can call **test_method** from Employee class's object but cannot call the **test_employee** from Person class's object. The flow is really unidirectional, the sub class can access base class functionality but base class cannot do so.

> Below terms are synonymous for Parent Class.
> - Base Class
> - Super class

> Below terms are synonymous for Child Class.
> - Sub class
> - derived class.

Many a times there might be a use case where we would need to re-define the logic that was written in the base class. At other times we might just need to extend the logic, this is called as method overriding, consider the below example.

```python
class Person:
    def __init__(self, fname, lname) -> None:
        self.first_name = fname
        self.last_name = lname

    def test_method(self):
        print("Inside the test method.")

    def print_credentials(self):
        print(f"First Name: {self.first_name}, Last Name: {self.last_name}")

class Employee(Person):
    def test_employee(self):
        print("Inside Employee")

    def print_credentials(self):
        print("----Employee----")
        super().print_credentials()
        print("----------------")

e = Employee("Shantanu", "Narale")
p = Person("Shantanu", "Narale")

p.print_credentials()
# Output : First Name: Shantanu, Last Name: Narale
e.print_credentials()
# Output : ----Employee----
# Output : First Name: Shantanu, Last Name: Narale
# Output : ----------------
```
In this example, class Employee inherrits from class Person. Class Person has a method *print_credentials*. When we are calling this method on Person object we are getting first_name and last_name of the person. However, this method is overriden in the *Employee* class. In the Employee class, we also print a line and then print the first and last names. The way we are able to do this is using **super()** keyword. Using `super().` gives access to all the methods and attributes of the Person class.

> It is also possible to not use *super* keyword inside the base class method and provide a complete separate implementation.

The *print_credentials* method in the *Employee* class can also be written in the below way.

```python
class Employee(Person):
    def test_employee(self):
        print("Inside Employee")

    def print_credentials(self):
        print("----Employee----")
        print(f"First Name: {self.first_name}, Last Name: {self.last_name}")
        print("----------------")
```

However, with this implementation we are not re-using the logic and is not a good practise.

Similar to methods, constructors can also be overriden. **In fact, Python madates that base class constructor must call `super().__init__()` method in its implementation**. This is necessarry since 

1. The methods inside the Parent class might not work if the constructor is not called as constructor might initialize the class attributes.
2. The exact logic written in the constructor might not be known.

```Python
class Person:
    def __init__(self, fname, lname) -> None:
        self.first_name = fname
        self.last_name = lname

    def test_method(self):
        print("Inside the test method.")

    def print_credentials(self):
        print(f"First Name: {self.first_name}, Last Name: {self.last_name}")

class Employee(Person):
    def __init__(self, fname, lname, salary) -> None:
        super().__init__(fname, lname)
        self.salary = salary

    def test_employee(self):
        print("Inside Employee")

    def print_credentials(self):
        print("----Employee----")
        super().print_credentials() 
        print(f"Salary: {self.salary}")       
        print("----------------")

e = Employee("Shantanu", "Narale", 5000)
p = Person("Shantanu", "Narale")

p.print_credentials()
# Output : First Name: Shantanu, Last Name: Narale
e.print_credentials()
# Output : ----Employee----
# Output : First Name: Shantanu, Last Name: Narale
# Output : Salary: 5000
# Output : ----------------
```
In the above example, *Employee* class also defines another attribute *salary* that is not defined in the *Person* class.

> Python does not throws error if `super().__init__()` is not called in the base class constructor, however, due to reasons mentioned above it must be called always.

> One thing to note is Python allows overriding static and class methods, however, inside static method in base class you cannot use `super()`. This throws RuntimeError. So you need to re-write the logic in static methods. In case of class methods, you can use `super()`.

```python
class Person:
    def __init__(self, fname, lname) -> None:
        self.first_name = fname
        self.last_name = lname

    def print_credentials(self):
        print(f"FirstName: {self.first_name}, LastName: {self.last_name}")

    def print_person_credentials(self):
        print(f"Person: {self.first_name} {self.last_name}")

    @staticmethod
    def print_something():
        print("In class Person")

    @classmethod
    def print_something_class(cls):
        print("In class method of Person")

class Employee(Person):
    def __init__(self, fname, lname, salary) -> None:
        super().__init__(fname, lname)
        self.salary = salary      

    def print_credentials(self):
        print("----Employee----")
        super().print_credentials()  
        print(f"Salary: {self.salary}")
        print("----------------")

    @staticmethod
    def print_something():
        print("In class Employee")

    @classmethod
    def print_something_class(cls):
        print("In class method of Employee")
        super().print_something_class()

class Manager(Employee):
    def __init__(self, fname, lname, salary, dept) -> None:
        super().__init__(fname, lname, salary)
        self.dept = dept

    def print_credentials(self):
        print("----***Manager***----")
        super().print_credentials()
        print("---------------------")
        super().print_person_credentials()

p = Person("Jane", "Belega")
e = Employee("Richard", "Nixon", 5000)
m = Manager("Rick", "Flare", 8000, "Sales")

p.print_credentials()
e.print_credentials()
m.print_credentials()

# Output : FirstName: Jane, LastName: Belega
# Output : ----Employee----
# Output : FirstName: Richard, LastName: Nixon
# Output : Salary: 5000
# Output : ----------------
# Output : ----***Manager***----
# Output : ----Employee---- 
# Output : FirstName: Rick, LastName: Flare
# Output : Salary: 8000
# Output : ----------------
# Output : ---------------------
# Output : Person: Rick Flare
```

In case of multilevel inherritance, *super* can access the element of immidiate parent. In case the method is not available in immidiate parent it looks into Parent's Parent. The same is illustrated in the above example.

The *print_credentials* method in the *Manager* class calls the *print_credentials* in *Employee* class and not in the *Person* class. However, when *print_person_credentials* method is called from *Manager* class using *super*, it calls the method from *Person* class.

In OOPS, the inherritance must follow **is a** rule. The rule states that, all the instances of base class should functionally be of type of parent class. For example, all Employees are people and all Managers are also people and Employees at the same time. Hence, it is valid to follow below hierarchy.
> Person -> Employee -> Manager

However, if we had to create an owner class, it should not inherit from *Manager* or *Employee* because all the owners might not be Managers and are neither Employees, however, they are people and hence should inherit from *Person* class.

Unlike most of the other programming languages, Python supports construct of Multiple Inheritance. What that means is a class can inherit from more than one base classes as shown below.

```python
# Multiple Inheritance

class A:
    def __init__(self, att1) -> None:
        self.att1 = att1
    
    def print_method(self):
        print("Class A")
    
    def print_method_classA(self):
        print("Only Class A")        

class B:
    def __init__(self, att2) -> None:
        self.att2 = att2
    
    def print_method(self):
        print("Class B")

    def print_method_classB(self):
        print("Only Class B")

class D(A):

    def print_method_classD(self):
        print("Only Class D")

class C(D, B):
    def __init__(self, att1, att3) -> None:
        super().__init__(att1)
        self.att3 = att3

    def print_method(self):
        super().print_method()        
    

c = C(1, 3)
C.print_method(c)
print(isinstance(c, A))
# Output : Class A
# Output : True
```

As shown in the above example, *Class C* inherrits from *Class D* and *Class B*. This construct is not available in many other programming languages. When we are using *super* inside *Class C* there is a unique way in which Python would access the Parent method which is called **Method Resolution Order**. Till Python 2.2 the MRO was resolved through DLR algorithm **(Depth First Left to Right)** after Python 3, there is a new algorithm i.e. **C3 Linearization**, however, for most cases DLR is still valid. The way this works is Python looks at the first Parent Class (or True Parent) if not found then in Parent's Parent and still not found then in second Parent. So in above case, the order will be by removing duplicates.

> Class C -> Class D -> Class A -> Class B

There is a special class level attribute *\_\_mro\_\_* that can be used to get the method resolution order eg. `print(C.__mro__)`.

Python also has an *isinstance* method. The method takes object and the class name and returns true if the object is instance of a class.

Since Python is not a strongly typeed language, there is a possibility of **Duck Typing** that is unique to Python. Consider a below example.

```Python
# Duck Typing
class Whale:
    def swim(self):
        print("Whale can swim....")

class Duck:
    def swim(self):
        print("Ducks can swim....")

    def fly(self):
        print("Ducks can fly....")

an_list = [Duck(), Duck(), Whale()]

for ele in an_list:
    ele.swim()
    ele.fly()

# Output :
# Ducks can swim....
# Ducks can fly....
# Ducks can swim....
# Ducks can fly....
# Whale can swim....
# Traceback (most recent call last):
#   File "d:\ProgrammingExpert\2 - Object Oriented Programming\7 - Inheritance\7 - Inherritance_4.py", line 21, in <module>       
#     ele.fly()
#     ^^^^^^^
# AttributeError: 'Whale' object has no attribute 'fly'
```

The *an_list* holds the object for *Duck* and *Whale*, in a strongly typed languages, you would not be able to call *fly* method. However, Python allows that and this results in error. This is called **Duck Typing**.