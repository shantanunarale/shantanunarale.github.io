---
author: shantanunarale
title: 3-*args and **kwargs
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [args, kwargs, splatting]
pin: true
---


In many Object Oriented Programming languages like C#, Java and C++ there is a concept of Method/function Overloading. A method overloading is essentially using same method/function name to create multiple methods, however, using different method definitions. For example, there may be two add functions, one accepting two numbers and other accepting two strings.

Python does not support the concept of method/function overloading. Even if we try to do that, latest function definition would override the preveous one. As per the below example, the `add_fn(a1, a2, a3)` remains the only valid function in the program and hence calling it with two parameters throws *TypeError*.

```python
def add_fn(a1, a2):
    return a1 + a2

def add_fn(a1, a2, a3):
    return a1 + a2 + a3

x = add_fn(1, 2)
# Output : TypeError: add_fn() missing 1 required positional argument: 'a3'
print(x)
```

There are many alternatives to solve this issue, however, one of them is using special arguments *\*args* and *\*\*kwargs*.

When we use the argument *\*args* as part of the function definition, we can pass any number of positional arguments to the function. The arguments are available in the function in form of a tuple. For *\*\*kwargs*, we can pass any number of keyword arguments to the function and the arguments are available in form of a dictionary with key as the name of the argument and value holding the value passed to it.

> Note : Using name args and kwargs is not mandatory, you need to use \* for accepting any number of positional arguments and \*\* for keyword arguments. The names can be of your choice, however, best practise to stick to args and kwargs to avoid confusion.

```python
def add_fn(*args):
    return sum(args)

def return_param_list(**kwargs):
    return list(kwargs.items())

x = add_fn(1, 2)
# Output : TypeError: add_fn() missing 1 required positional argument: 'a3'
print(x)
# Output : 3
x = add_fn(1, 2, 3, 4, 5)
print(x)
# Output : 15

print(return_param_list(a = 4, b = "5", c = True))
# Output : [('a', 4), ('b', '5'), ('c', True)]
```
You can also combine *\*args* and *\*\*kwargs* in function definition, however, they must appear at the end. Also, the *\*args* must appear before *\*\*kwargs*. So the argument *\*\*kwargs* must appear the end.

```python
def sam_fn(p1, *args, **kwargs):
    print(p1, args, kwargs)

sam_fn(1)
# Output : 1 () {}
sam_fn(4, 4, 5, 6)
# Output : 4 (4, 5, 6) {}
sam_fn(4, 4, 5, 6, x = "a", z = "b")
# Output : 4 (4, 5, 6) {'x': 'a', 'z': 'b'}
```

There is another concept called as splatting in Python. Consider the below example, where we have `add_or_concat` function that takes three positional arguments and we need to pass the three arguments of our list.

```python
def add_or_concat(a, b, c):
    return a + b + c

lst = [1, 2, 3]
op = add_or_concat(lst[0], lst[1], lst[2])
print(op)
```

This works fine, however, if our function starts accepting say hundreds of parameter this becomes difficult to write in a program. In Python, you can use same \* and \*\* operator to unpack this list into individual parameters to pass it to this function as below.

```python
def add_or_concat(a, b, c):
    return a + b + c

lst = [1, 2, 3]
kdic = {"a": 1, "b": 2, "c": 3}
# op = add_or_concat(lst[0], lst[1], lst[2])
op = add_or_concat(*lst)
print(op)
# Output : 6
op = add_or_concat(**kdic)
print(op)
# Output : 6
```

The \* works on any iterable like list, tuple, set, string or dictionary, however with dictionary by default it will pass the keys, so you would have to specify that you need to pass values like `\*mydic.values()`. For \*\* kwargs, it works only with dictionaries and that too the name of the keys should match with the name parameter names of the function as this is a keyword argument.

This is a very useful way of passing every element of an iterable to the function in an efficient way and we can also combine them with *\*args* and *\*\*kwargs*. One primary use case of this is to print the individual elements of list.

```python
# Approach 1
mylst = [1, 2, 3, 4, 5]
st = ""
for ele in mylst:
    st += str(ele) + ","
print(st.rstrip(","))
# Output : 1,2,3,4,5

# Approach 2
print(*mylst, sep=",")
# Output : 1,2,3,4,5
```
Both the print functions print same values.