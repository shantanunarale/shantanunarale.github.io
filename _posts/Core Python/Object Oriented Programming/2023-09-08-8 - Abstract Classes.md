---
author: shantanunarale
title: 8-Abstract Classes
date: 2024-01-12 00:36:00 +0530
categories: [Core Python, Object Oriented Programming]
tags: [Classes, Abstract]
---

An Abstract class is the one that cannot be instantiated but can act as a base class for other class. Abstract Class usually consists of abstract methods. An abstract method is something that does not have method implementation but has only method definition. The real use of Abstract class is to achieve enforce every inherting class to implement its method thus enforcing abstraction.

Python does not have a notion of Abstract class. We can create a class and treat it as abstract if the class name is prefixed with **Abstract** word.

```python
import random

class AbstractGame:
    def start(self):
        print("Game has begun...")
        self.play()

    def end(self):
        self.reset()
        print("Game Ended")

    def play(self):
        raise NotImplemented("Base class needs to implement this.")
    
    def reset(self):
        raise NotImplemented("Base class needs to implement this.")
    
class RandomNumberGuesser(AbstractGame):
    def __init__(self) -> None:
        super().__init__()
        self.random = random.randint(1, 10)
        self.attempts = None
        self.reset()

    def reset(self):
        self.attempts = 1

    def play(self):
        while True:
            num = int(input("Enter a number: "))
            if num != self.random:
                self.attempts += 1
            else:
                break

        print(f"You took {self.attempts} attempts to guess correct number.")

gm = RandomNumberGuesser()
gm.start()
gm.end()
```

As you can see in the above example, the AbstractGame class has two abstract methods. Since Python, does not support notion of abstract class, it does not have abstract method as well. Hence to mimick, we have raised *NotImplemented* Error in the abstract method. With this we still can instantiate abstract class but the method call will throw the error.