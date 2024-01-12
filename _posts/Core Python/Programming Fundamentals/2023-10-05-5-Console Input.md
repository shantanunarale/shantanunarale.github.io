---
author: shantanunarale
title: 5-Console Input
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [Console, input]
---

input() function takes the prompt and prints that prompt and gets the input from user.

- Input function does not add the space, so you have to do it yourself if you need. Example

```python
input("Number: ")
```
- All the values returned from input are strings. So if you return a number, it is still a string. Example
```python
number = input("Enter a number: ") # User inputs 5
print(type(number)) # returns <class 'str'>
```
- You can only pass one argument to input function and no commas. So to concatenate the string use
```python
name = print("Enter Name : ")
age = input("Hello, " + name + " what is your age ")
```