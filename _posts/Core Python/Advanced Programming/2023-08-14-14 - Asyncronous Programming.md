---
author: shantanunarale
title: 14-Asynchronous Programming
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Advanced Programming]
tags: [Threading]
---


Till now, we have been looking at programs those were synchronously that means the programs are running as fast as the clock speed of the CPU. However, Python also supports something called as asynchronous programming. Now the asynchronous programming was introduced in Python as an alternative to Threading as threading is complex and since Python does not support Parallel programming threading does not help much. asynchronous programs execute mostly single threaded, are easier to understand and debug and solves most of the problems related to Threading. Python also has a very powerful event loop that allows us to schedule tasks independantly. Most of the things that we do with Threading are doable using asynchronous programming.

asynchronous programming needs `asyncio` module to be imported in order to run. Below is a very simple example.

```python
import asyncio

async def main():
    print("In the Main...")

print(main) # Output : <function main at 0x0000024062929080>
print(main()) # Output : <coroutine object main at 0x00000240648C16C0>
asyncio.run(main())
# Output : In the Main...
```

As soon as we use word `async` before the function definition, it becomes a **coroutine** (aka co-operative routine). This coroutine can run asynchronously in the program. In order to run the co-routine in the mainline code we need to use `asyncio.run(coroutine())`. Also, note that when we run this coroutine we get a runtime warning that *"RuntimeWarning: coroutine 'main' was never awaited"*. This is because the coroutine can run asynchronously and can take longer that the main line code, so the results need to be awaited.

There is also an `await` keyword that can be used only within the async function that can wait for the coroutine to finish. Below is the example.

> Note that, for asynchronous programming mostly the logic is implemented in the coroutine and the mainline code usually only executes the code using `asyncio.run()`.

```python
import asyncio

async def print_somethin():
    print("In print something")
    await asyncio.sleep(1)
    print("Priniting something")

async def main():
    print("In the main routine")
    await print_something()
    print("Ending main routine")

asyncio.run(main())
```

> Please note that when we need to introduce a delay with coroutine, use `asyncio.sleep()` as `time.sleep()` would not work correctly.

Here we first run the `main` coroutine which runs the `print_somethin` coroutine and waits for it to finish before executing the last line of code. However, sometimes we might want to let the `main` routine do its work till `print_something` routine is waiting. We can accomplish that using `task`.

```python
import asyncio

async def print_something():
    print("In print something")
    await asyncio.sleep(2)
    print("Priniting something")

async def main():
    print("In the main routine")
    task = asyncio.create_task(print_somethin())
    await asyncio.sleep(1)
    print("Ending main routine")
    await task

asyncio.run(main())
```

Here, as soon as we create a `task` we schedule a co-routine for future run. It can get picked up anytime whenever the `main` routine hangs. As soon as we execute the `print_somethin` coroutine, it will give yield the control back to `main` if it hangs somewhere. The last line `await task` is really the blocking line of the code that would wait till task is completed.

We can also schedule multiple tasks using gather and also collect the returned value.

```python
import asyncio

async def fn_A(val):
    print("In fn A")
    await asyncio.sleep(1)
    return val

async def main():
    print("In the main")
    val =  asyncio.gather(fn_A("Something"))
    print(f"Outside main ")
    vals = await val
    print(vals)
    
asyncio.run(main())
```

The `vals` is also referred as **futures** those are the values that would be populated in future. `asyncio.gather()` can collect and schedule all the tasks and while we `await` it returns list of all the values returned from the tasks. We can also use a for loop asynchronously.

```python
import asyncio

async def loop(num):
    cnt = 0
    while cnt < num:
        yield cnt
        cnt += 1
        await asyncio.sleep(1)

async def main():
    async for i in loop(10):
        print(i)

asyncio.run(main())
```

Note that the for loop must have `async` keyword to call the asynchronous generator.