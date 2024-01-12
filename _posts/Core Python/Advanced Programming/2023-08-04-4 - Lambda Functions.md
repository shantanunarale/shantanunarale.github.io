---
author: shantanunarale
title: 4-Lambda Functions
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [lambda, anonymous function]
pin: true
---

Lambda functions are basically **one line anonymous** functions that provide the definition and implementation on the same line where they need to be used. Basically, it is a synactic sugar that avoids us typing the function which is doing a very small work.

```python
# Lambda Functions
def add_concat_fn(x, y):
    return x + y

func = lambda x, y: x + y
print(func(4, 5))
# Output : 9

func = add_concat_fn
print(func(4, 5))
# Output : 9
```

The `add_concat_fn` function can be re-written as lambda function. Here the variable *func* is not the name of the lambda function (lambda functions are anonymous), its just holding the function object. Instead of lambda we can also assign it a normal function.

You do not need to write *return* inside the lambda function, the first and only lines evaluation is returned by default. One specific use case of lambda is passing it to other function like `sorted()` as shown in the below example.

```python
mylst = [[1, 3], [2, 0], [3, -4], [4, 5]]
slist = sorted(mylst, key=lambda x: x[1])
print(slist)
```

As in case of every function, lambda has to return a value, even if you print something inside lambda it would return *None*. 

A lambda function can also return another lambda like below.

```python
func = lambda x : lambda y : x * y
mul1 = func(5)
print(mul1(6)) # Output : 30
print(mul1(7)) # Output : 35
print(func(6)(7)) # Output : 42
```
This is exactly similar to a function returning a function like below.

```python
def mulx(x):
    def muly(y):
        return x * y
    return muly

print(mulx(5)(8)) # Output: 40
```
This is called a closure function in Python and is used while creating decorators. This type of implementation is called function chaining and is another powerful feature of Python.