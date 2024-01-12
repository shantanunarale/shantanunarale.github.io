---
author: shantanunarale
title: 5-Maps and Filters
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [map, filter]
pin: true
---

Python has two special functions map and filter that takes in itterable and a function and helps to map and filter the itterable. Below is a simple example of using map and filter function in Python.

```python
# Maps and Filters

def sum_fn(inp):
    return sum(inp)

lst = [[1, 2], [3, 4], [5, 6], [7, 8]]
ls1 = [1, 2, 3, 4]
ls2 = [3, 4, 5, 6]

new_map = map(sum_fn, lst)
for np in new_map:
    print(np, end=" ")
x = list(new_map)
print(*x)

new_map = map(lambda x, y: x + y, ls1, ls2)
x = list(new_map)
print(*x)

new_fil = list(filter(lambda x: x[1] % 2 == 0, lst))
print(new_fil)
```

The `map()` function takes in a function that take the element of itterable as an input and return a specific value. Map function will only map that value inplace of that element. This function returns a *map object* which is itterable, however, you can convert it to list if needed. There are multiple overloads of map, it can take many number of itterables, however, the function should also take those many inputs. We can also use lambda inplace of a function.

`filter()` function returns a *filter object* similar to a map object and takes in an itterable and a function as an input. The input function should accept the element of itterable as an input and must return *True* or *False*. The *filter object* contains only those elements for which the input function returned *True*. Similar to `map()`, `filter()` function can also accept lambda and the output can be converted to list.