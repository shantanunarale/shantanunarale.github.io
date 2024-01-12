---
author: shantanunarale
title: 1-Modules and Packages
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [Module, Packages]
---

In Python, till now we have been writting all the code in one single Python file. However, that becomes difficult to maintain and read. Also, code sharing becomes difficult as you would need to share the enitre code if some application wants to reuse a particular piece of code in your program. A real-life python code is not written in a single file. In fact Python supports the concept of *Modules* and *Packages*.

A Module in Python is basically a *.py* file. Any file with extension *.py* can be a module. The file that you are executing currently is called as **\_\_main\_\_** module. You can import as many modules as you want in Python. There is a variable **\_\_name\_\_** which gives the name of the module you are working in. By convention, Python module should follow *snake_case* . You can have number in the module name but not space, if you put space, Python would restrict importing the module. Below is the example of modules. 

```python
# Functions module with name functions.py

def foo():
    print ("Foo function....")

def bar():
    print("Bar Function....")

class Test:
    pass

if __name__ == '__main__':
    print("Inside Functions module....")
    
```
```python
# Main Python file with name mail_module.py

import functions

print(__name__) # Output: __main__
print(functions.__name__) # Output: functions

functions.foo()
functions.bar()
# Output: Foo function...
# Output: Bar function...

t = functions.Test()
print(type(t), type(t).__name__)
# Output : <class 'functions.Test'> Test
```

Here, we have created two separate files, one python file with name *functions.py* which has a function *foo* and *bar* and a class *Test*. This file is placed in the same directory from where we are running our program *main_module.py*. The *import* keyword allows us to import the module *functions*.

> One thing to note is, avoid naming the module with same name as built-in modules and packages. The same is applicable for packages as well.

Once, the functions module is imported, we can use methods and classes inside the functions module by using name of module like `functions.foo()`. One thing to note here is if we call `__name__` in the function module it prints *\_\_main\_\_*, if we use `__name__` on function module outside the functions module it prints *functions*. This is very important functionality that we can use for debugging, we can use if statement in *functions* module to execute certian block of code only when we are exexcutin module itself.

We can also use alias for module imported so that we don't need to use the complete module name as below.

```python
# import functions
import functions as f

print(__name__) # Output: __main__
print(f.__name__) # Output: functions

# functions.foo()
# functions.bar()
f.foo()
f.bar()
# Output: Foo function...
# Output: Bar function...

# t = functions.Test()
t = f.Test()
print(type(t), type(t).__name__)
# Output : <class 'functions.Test'> Test
```
When we alias an imported module like here wer alias with *f*, we can no longer use the original module name *functions*. However, we can do alias as well as import original module something lile below but it is a bad practise.

```python
import functions
import functions as f

f.foo()
functions.bar()
```

When we import a module, python runs that module once so that the functions and classes gets created. We can also import only specific functions and classes using *from* keyword like below. This is considered as good practise as we don't import each and every function or class in the module.

```python
# import functions
# import functions as f
from functions import foo, bar, Test

print(__name__) # Output: __main__
# print(f.__name__) # Output: functions

# functions.foo()
# functions.bar()
# f.foo()
# f.bar()
foo()
bar()
# Output: Foo function...
# Output: Bar function...

# t = functions.Test()
# t = f.Test()
t = Test()
print(type(t), type(t).__name__)
# Output : <class 'functions.Test'> Test
```
By doing so we don't need to use the module name like `functions.foo()`, instead we can directly access the *foo()* function as if it was written within the main module.

We can also do the following to import all the functions and classes from module, however, this is regarded as a bad practise as there can be a conflict if you have function with same name in your program.

```python
from functions import *
```

Packages in Python are special folders that contains related modules. Any folder would become package if it contains *\_\_init\_\_* file.

Say if a module b imports another module a and module a imports module b, in this case, Python would give cicular reference error. 

One thing to remember is, we need to import a specific module in order to start using code within that module, like we need to import the package.module name to start reusing the code. We can also use init file to import the modules within the packages as the init file runs once we import the module, however, please note that we would still need to import inidividual modules. Check module4.py.

Python also supports concept of reference import. However, reference import can be done within from only. One dot indicates the current folder, .. indicates parents paret and so on.