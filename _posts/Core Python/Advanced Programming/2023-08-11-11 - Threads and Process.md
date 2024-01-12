---
author: shantanunarale
title: 11-Threads and Process
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [Python Theory]
---

A process is a program that is executing on a computer. A process is made up of multiple threads that runs certain parts of programs. There is atleast one thread in a porgram. Processes can split the code execution between multiple threads. Reason we have multiple threads is so that CPU can alternate between multiple processes at one time.

A morden day CPU has multiple cores. Number of cores is equal to number of processes a processor can execute in parallel. Also, the modern CPUs are Hyperthreaded so that introduces us to a logical and physical core. If Hyperthreading is enabled a single physical core is split into two logical cores so a 4 core CPU with hyperthreading enabled acts as 8 logical cores and can run 8 parallel processes.

In CPU, a program thread is run. The way this works is as soon as the thread hangs (eg. if it waits on harddisk or other device) it is kicked out of CPU and other thread from other process is given CPU. The scheduling is very complex and is handled by OS.

There are two things in programming.

- Concurrency : This refers to program having multiple threads, however, only one thread runs at a time and CPU can switch if thread is not working. You may divide your program in multiple threads that may execute one at a time.
- Parallelism : This refers to program having multiple threads that are taking up different CPU cores and executing at the same time.