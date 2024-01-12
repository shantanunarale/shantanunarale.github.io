---
author: shantanunarale
title: 9-Generators
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [yield]
pin: true
---

A Generator is a special type of object that is similar to an iterator. A generator can do almost everything similar to iterator. A function is called as a generator function if it has a `yield` keyword within it. When you have a `yield` keyword, the function would return a *generator* object. The Generator object is iterable and can be used within a for loop and with `next()` function. Below is the example.

```python
# Generators

def generator_fn():
    yield 1
    yield 2
    yield 3

print(type(generator_fn()))
# Output : <class 'generator'>

for i in generator_fn():
    print(i)

# Output : 1 2 3

z = generator_fn()
print(next(z))
print(next(z))
print(next(z))


# Output : 1 2 3
```

> Iterator is a legacy syntax. The newer syntax is generator.

The `yield` returns the value and pauses the execution of generator function till the next function call. On the next call, the execution will continue from where it left. 

Generators are good to use where you want to generate or iterate on large set of objects but dont need to store the individual element. For example, we need to print fabonacii series but don't need to store individual element. Without generator this would have to be done with a list which requires memory. Below is how we can achieve the same using generator.

```python
def fab(n):
    a, b = 0, 1

    while a < n:
        yield a
        a, b = b, a + b

x = fab(100)
for ele in x:
    print(ele, sep=" ")
```