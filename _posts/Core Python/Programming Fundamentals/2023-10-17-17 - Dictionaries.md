---
author: shantanunarale
title: 17-Dictionaries
date: 2024-01-11 00:36:00 +0530
categories: [Core Python, Programming Fundamentals]
tags: [key-value-pairs, built-in types, core python types]
---

Dictionary is a mutable type available in Python. A Dictionary is essentially a collection of a name value pair. Below is how a basic form of dictionary looks like.

```python
dic = {1: "First", 2: "Second", 3: "Third", 4: "Fourth", True: "True", 3.5: "Float", "string": "stringer", (1, 2): "Tuple"}

# Result : {1: 'First', 2: 'Second', 3: 'Third', 4: 'Fourth', 3.5: 'Float', 'string': 'stringer', (1, 2): 'Tuple'}
```

The first part of the dictionary is a key. A key can be any immutable data type like an int, float, bool, str or tuple. Mutable data types like list cannot be a part of key. The second part separated by : is a value. A value can be anything mutable or immutable like int, str, float, list, tuple or another dictionary. If you try to assign mutable type as a list, you get a TypeError as below.

> TypeError: unhashable type: 'mutable_type'

None can be a key in a dictionary as below.

```python
dic_com = {1: "One", "List": [1, 2, 3], "Dic": {1: "One", 2: "Two"}, None: "None"}
print(dic_com)

#Result: {1: 'One', 'List': [1, 2, 3], 'Dic': {1: 'One', 2: 'Two'}, None: 'None'}
```

One fundamental aspect of a dictionary is that keys in the dictionary need to be unique. If you try to define a key that already exists, python will simply overwrite the value of that key. For example,
 
 ```python
 dic = {1: "First", 2: "Second", 3: "Third", 4: "Fourth", True: "True", 3.5: "Float", "string": "stringer", (1, 2): "Tuple", 1: "One"}
print(dic)

#Result: {1: 'One', 2: 'Second', 3: 'Third', 4: 'Fourth', 3.5: 'Float', 'string': 'stringer', (1, 2): 'Tuple'}
```

As you can see in the above example, Key 1 appears twice, in the result we see it only once with the latest value 'One'. Similary, setting the value of a key that exists after defining the dictionary will also result into the same result.

**A dictionary is an unordered collection of objects unlike lists. The order in which you insert elements may not be same in which they are stored or printed**. Python uses hashing algorithm to store the keys of dictionary. 

> You can consider a dictionary as a list where keys are user defined. Since, the keys are user defined, they need to be unique, the same happens in the list. Only one and only one element exists on a key in the list.

The main appication of a dictionary is where the order of the element does not matter but we need to store some extra information related to that element and need very fast searches. One example is to count frequency of words in a given file or a string. We would need to store number of times a character occured as well as store number of times it occured as a value. A list can also be used to store this type of information, however, if we need to search a frequency of a particular character or a word, we need to iterate on the entire list every time. With dictionaries, this operation is simple and very fast as keys are hashed. Below is a simple implementation of the above example.

```python

# Application of dictionary to count the frequency of words in the string.

inp = input("Enter a string of your choice: ")
dic = {}

for ele in inp:
    dic[ele] = dic.get(ele, 0) + 1

print("Below is the frequency of occurence of every word in string.\n")
for idx, ele in dic.items():
    print(f"{idx} - {ele}")

```

### Accessing and setting Dictionary

To access an element in the dictionary, we need to use [] and pass the key, similar to how we pass an index in the list. The result is the value for that particular key.

To add an item or update value of existing key. We need to follow the same syntax of square brackets like we do in the list. If the key exists, the value is updated, else a new key(value in the square bracket is the key) is added and value is assigned.

A blank dictionary can be defined by using either a dict() function or two curly braces {}.

```python
# Basic way to define a dictionary.

dic = dict()
dic = {}

dic = {1: "First", 2: "Second", 3: "Third", 4: "Fourth", True: "True", 3.5: "Float", "string": "stringer", (1, 2): "Tuple", 1: "One"}
print(dic)
# Adding same key twice will overwrite the value of the key. Key has to be unique.

# Accessing the dictionary
print(dic[(1, 2)])
print(dic[1])

# Setting the element of a dictionary

dic[0] = "Zero" # Add the element zero, since it does not exist
dic[1] = "First"

```

If you iterate on the dictionary as mentioned in the example below, you start getting the keys as the output.

```python
dic = {1: "First", 2: "Second", 3: "Third", 4: "Fourth"}

# Iteration on keys by default
for ele in dic:
    print(ele, sep=" ")

# Result : 1 2 3 4

```
### Methods in the dictionary

Dictionary supports many methods like values, items, keys etc. Below is the brief description of these methods.

- values() : This method returns a special object dict_values which is the collection of all the values in the dictionary. You cannot access the values in this object with [] as the object is not subscriptable but you can iterate on it using for loop. You can always convert it to a list using list[] function.

- keys() : This method is similar to the values except returns all the keys in dict_keys object. It is not subscriptable but iterable.

- items() : This returns dict_items object that is not subscriptable but iterable. You can use it in for loop similar to enumerate keyword. It returns both key and the value.

```python

print("Iteration of Dic items")
# Iteration on dic_items is possible cause its iterable
for idx, ele in dic_items:
    print(idx, ele, sep=" - ")
```
- get(key, default_value) : This method accepts two parameters, a key and a default value. If key is found in the dictionary, it returns the key, else the default value.