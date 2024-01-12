---
author: shantanunarale
title: 6-Function Closures
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [closure]
pin: true
---

In Python, everything is considered as an object. So a function is also an object of *class function*. That means we can store the function in a variable like we store other objects, pass it to other functions and can also return it as follows.

```python
# Function Closure
def foo():
    print("Inside foo....")

def bar(func):
    print("Inside bar")
    func()

my_func = foo
my_func()
# Output : Inside foo....
bar(my_func)
# Output : Inside bar
# Output : Inside foo...
```

Similar to this a function can also be nested like the one below.

```python
def outer_func(x):
    print("Inside outer function")
    def inner_func():
        print("Inside inner function")
        print(f"Value of y: {x}")
    inner_func()

outer_func("test")

# Output: Inside outer function
# Output: Inside inner function
# Output: Value of y: test
```
As you can see the inner function can also access the variable *x* which is defined in the outer function. 

If the outer function starts returning the inner function, the inner function can be accessed outside the scope of the outer function. That means even if the outer function is closed, we would be able to call the inner function. This type of inner function is called the closed function. The objects created inside the outer function still are accessible as part of the inner function. This is a very powerful feature of Python. Below is how the basic function closure looks like in Python.

```python
def outer_func(x):
    print("Inside outer function")
    def inner_func():
        print("Inside inner function")
        print(f"Value of y: {x}")
    # inner_func()
    return inner_func

my_func = outer_func("test")
my_func()

# Output: Inside outer function
# Output: Inside inner function
# Output: Value of y: test
```

The argument *test* that was passed to *outer_func* can be accessed even after the outer function was closed. Here is another example of function closure.

```python
def outer_func2(x):
    print("Inside Outer function...")
    def inner_func2(y):
        print("Inside Inner function...")
        return x * y
    return inner_func2

fval = outer_func2(5)
print(fval(1))
print(fval(2))
print(outer_func2(3)(3))

# Output: Inside Outer function...
# Output: Inside Inner function...
# Output: 5
# Output: Inside Inner function...
# Output: 10
# Output: Inside Outer function...
# Output: Inside Inner function...
# Output: 9
```
Here, we have created stored the result of `outer_func2(5)` in variable `fval`. The value of *5* that was assigned to variable *x* remains stored even if we execute the `inner_func2()` through `fval`. The last line demonstrates how we can chain the functions by passing value to both outer and inner function `outer_func2(3)(3)`. 

This gets intresting when we have a mutable type like *list* as shown below.

```python
def outer_func3():
    lst = []
    def inner_func3(valx):
        lst.append(valx)
        return lst
    return inner_func3

outer3 = outer_func3()
print(outer3(1))
print(outer3(2))
print(outer3(3))

# Output : [1]
# Output : [1, 2]
# Output : [1, 2, 3]
```

Here the functionality of class is replicated using a closure function. To do this in a class we would have to build it in the following way.

```python
class list_append:
    def __init__(self):
        self.lst = []

    def add_ele(self, valx):
        self.lst.append(valx)

obj = list_append()
obj.add_ele(1)
obj.add_ele(2)
print(obj.lst)

# Output : [1, 2]
```
As you can see in the above example, the function closure provides us the same functionality of class. Another thing to note is the inner function i.e. `inner_func3` in this case can modify the mutable type *lst*, this would change if there is a immutable type like int.

```python
def outer_im(x):
    print(f"Outer function, value of x {x}")
    def inner_im(y):
        print(f"Outer function, value of x {x}, value of y {y}")
        x += 1
    return inner_im

im = outer_im(1)
im(2)
# Output : UnboundLocalError: cannot access local variable 'x' where it is not associated with a value
```

Here, we are not able to set the value x which is defined inside the outer function `outer_im`. However, if we try to only read it that works. This has to do with mutability of the types. The immutable types when passed to function, python creates a new object and does not modify the existing one.

There is another keyword withing python **nonlocal** that can help us with this.

```python
def outer_im(x):
    print(f"Outer function, value of x {x}")
    def inner_im(y):
        nonlocal x
        x += 1
        print(f"Outer function, value of x {x}, value of y {y}")
    return inner_im

im = outer_im(1)
im(2)

# Output : Outer function, value of x 1
# Output : Outer function, value of x 2, value of y 2
```

When we use *nonlocal*, it means that variable x that was defined as part of the outer function `outer_im` can be accessed within the inner function.

> One thing to note here is when we use the nonlocal keyword, it would access the variable nearest to it. That means if we have three levels of nesting, the nonlocal with each function having same variable name. The nonlocal accesses the variable nearest to it.