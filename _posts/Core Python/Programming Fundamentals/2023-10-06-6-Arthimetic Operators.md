---
author: shantanunarale
title: 6-Arithmetic Operators
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [operators, arithmetic]
---

These are the operators that are used on numbers.
- Add +
    - When you add int to float and result is a whole number like 1.0 + 2. The result will be float 3.0 (higher fiedility Data Type)
- Sub -
    - When you substract int to float and result is a whole number like 1.0 + 2. The result will be float 3.0 (higher fiedility Data Type)
- Mul *
    - When you multiply int to float and result is a whole number like 1.0 + 2. The result will be float 3.0 (higher fiedility Data Type)
- Div /
    - When you divide no matter whatever the operads are, the result will always be float.
    - If you divide by zero you get division by zero error.
- Exponential **
    - Raises the power of x by y.
- Integer Division //
    - This gives the Integer result of the division. The output is the integer result of division by stripping **(not  rounding)** the result.
    - If the left handside of Integer division is float then answer is float.
    - Division by zero gives <u>**ZeroDivisionError**</u>
- Modulas Operator %
    - Gives the remainder of the division.

### Operator Precedence in Python
Example :
```python
x = 11
y = 2
result = x % y + 4 - 7 ** (2 /3)
```
The precedence is
1. Brackets/parenthesis
2. Exponents
3. multiplication and division and mod
4. addition substraction.

>For the operators with same precendence, whatever comes first gets executed in the order they appear.

If you try to use incorrect types in operator you get TypeError. Example.

```python
answer = 4.5 + "5"
```

However, if you use float/int with Boolean (True or False) will be evaluated as True evalutes to one and False to zero internally. So
```python
result = 4 + True
print(result)
```
will give the output of 5