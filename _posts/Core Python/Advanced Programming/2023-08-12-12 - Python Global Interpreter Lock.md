---
author: shantanunarale
title: 12-Python Global Interpreter Lock
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [Python Theory]
---

A Python has something called as a Global Interpreter. When you create a python program with multiple threads and run the python program, python attaches something called as Interpreter to your program. The thing is this Interpreter is shared between all the threads within your processes. 

When one thread is being executed by the Interpreter it puts a lock called as *mutex* and locks itself so that other thread cannot access the Interpreter at the same time. This behavior is specific to Python. Most other programming languages would allow parallel execution of Interpreters however, python does not do that, instead it locks the Interpreter. Thus parallel programming is not possible in Python, so we need to work with concurrent programs. The reason Python does this is due to.
- Simplicity
- Efficiency/Speed
- Performance

The thing is when we create a program and run that process in our computer, it gets some storage inside the RAM to store its variables and other data structures. This storage is accessible by multiple threads within the process that means multiple threads can access and modify the same variable. This can give some weird outputs and bugs those are very hard to debug. The way Python resolves it is using the mutex that is placed directly on the Interpreter itself. This makes the Python Interpreter more simpler.

Now, there are other programming languages that can place *mutex* on shared objects so that other tread cannot access it till the first thread is done, however, with doing so you would have to maintain multiple locks. Those locks would have to be release and acquired for multiple shared objects making the Interpreter more slower and locks would also need memory making it less efficient. However, this would allow us running Parallel processes. 

Also, there are some C extensions that run in Python for performance intensive algorithms those works best when the Interpreter has a *mutex*.

Python also has something called as *reference count* which is similar to *garbage collector* in other languages. So in Python, we actually keep track of number of references that we hold for the object. Something like two variables hold same object the reference count would hold value of 2. This would cleanup the objects those are not used in background that do not have any references. Managing this reference count becomes more tricky with parallel processes, this is because if we remove a object if it is still referenced within some other thread this would result program to crash.

> Hence, the bottom line is Python does not support Parallel programs, you can run concurrent programs by creating multiple threads and running them one at a time. There are some Python interpreters that do not have *mutex*, however, they are slower,