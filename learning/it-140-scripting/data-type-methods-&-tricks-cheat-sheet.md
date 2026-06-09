# Python Data Type Methods & Tricks Cheat Sheet

A quick guide to common things you can do with Python data types.

---

# Universal / Works on Many Types

## `len()`

Gets the number of items.

```python
len(my_list)
len(my_string)
len(my_dict)
len(my_tuple)
len(my_set)
```

Works on:
- Lists
- Strings
- Dictionaries
- Tuples
- Sets

---

## `min()` and `max()`

Gets the smallest or largest value.

```python
numbers = [4, 9, 1, 7]

print(min(numbers))  # 1
print(max(numbers))  # 9
```

Works on:
- Lists
- Tuples
- Sets
- Strings
- Ranges

For strings, it checks alphabetically.

```python
names = ["Connor", "Alex", "Zach"]

print(min(names))  # Alex
print(max(names))  # Zach
```

---

## `sum()`

Adds numeric values.

```python
numbers = [1, 2, 3, 4]

print(sum(numbers))  # 10
```

Works on:
- Lists of numbers
- Tuples of numbers
- Sets of numbers
- Ranges

Does not work on strings.

---

## `sorted()`

Returns a sorted version without permanently changing the original.

```python
numbers = [3, 1, 4, 2]

print(sorted(numbers))  # [1, 2, 3, 4]
```

Reverse order:

```python
print(sorted(numbers, reverse=True))
```

Works on:
- Lists
- Tuples
- Sets
- Strings
- Dictionaries

---

## `in`

Checks if something exists.

```python
my_list = ["apple", "banana", "cherry"]

print("banana" in my_list)  # True
```

Works on:
- Lists
- Strings
- Dictionaries
- Tuples
- Sets

For dictionaries, it checks keys.

```python
person = {"name": "Connor", "age": 27}

print("name" in person)  # True
```

---

# Indexing and Slicing

## Indexing

Gets one item by position.

```python
my_list = ["a", "b", "c"]

print(my_list[0])  # a
print(my_list[1])  # b
print(my_list[-1]) # c
```

Works on:
- Lists
- Strings
- Tuples

---

## Slicing

Gets part of a sequence.

```python
my_list = [10, 20, 30, 40, 50]

print(my_list[1:4])   # [20, 30, 40]
print(my_list[:3])    # [10, 20, 30]
print(my_list[2:])    # [30, 40, 50]
print(my_list[::-1])  # [50, 40, 30, 20, 10]
```

Works on:
- Lists
- Strings
- Tuples

---

# List Methods

## `.append()`

Adds one item to the end.

```python
my_list = [1, 2, 3]

my_list.append(4)

print(my_list)  # [1, 2, 3, 4]
```

---

## `.insert()`

Adds an item at a specific position.

```python
my_list = ["a", "c"]

my_list.insert(1, "b")

print(my_list)  # ["a", "b", "c"]
```

---

## `.remove()`

Removes a specific value.

```python
my_list = ["red", "blue", "green"]

my_list.remove("blue")

print(my_list)  # ["red", "green"]
```

---

## `.pop()`

Removes and returns an item.

```python
my_list = ["a", "b", "c"]

item = my_list.pop()

print(item)     # c
print(my_list)  # ["a", "b"]
```

Remove by index:

```python
my_list.pop(0)
```

---

## `.sort()`

Sorts the list permanently.

```python
numbers = [3, 1, 4, 2]

numbers.sort()

print(numbers)  # [1, 2, 3, 4]
```

Reverse:

```python
numbers.sort(reverse=True)
```

---

## `.reverse()`

Reverses the list permanently.

```python
numbers = [1, 2, 3]

numbers.reverse()

print(numbers)  # [3, 2, 1]
```

---

## `.count()`

Counts how many times a value appears.

```python
numbers = [1, 2, 2, 3]

print(numbers.count(2))  # 2
```

---

## `.index()`

Finds the first position of a value.

```python
names = ["Alex", "Connor", "Sam"]

print(names.index("Connor"))  # 1
```

---

# String Methods

## `.lower()` and `.upper()`

Changes capitalization.

```python
name = "Connor"

print(name.lower())  # connor
print(name.upper())  # CONNOR
```

---

## `.strip()`

Removes spaces from the beginning and end.

```python
text = "   hello   "

print(text.strip())  # "hello"
```

---

## `.replace()`

Replaces part of a string.

```python
text = "I like cats"

print(text.replace("cats", "dogs"))
```

---

## `.split()`

Splits a string into a list.

```python
sentence = "red blue green"

words = sentence.split()

print(words)  # ["red", "blue", "green"]
```

Split by something specific:

```python
date = "06/09/2026"

parts = date.split("/")

print(parts)  # ["06", "09", "2026"]
```

---

## `.join()`

Combines a list of strings into one string.

```python
words = ["red", "blue", "green"]

sentence = " ".join(words)

print(sentence)  # red blue green
```

Join with commas:

```python
items = ["apple", "banana", "cherry"]

print(", ".join(items))  # apple, banana, cherry
```

Important: `.join()` only works with strings.

---

## `.find()`

Finds the position of text.

```python
message = "hello world"

print(message.find("world"))  # 6
```

Returns `-1` if not found.

---

## `.startswith()` and `.endswith()`

Checks the beginning or end of a string.

```python
file_name = "notes.txt"

print(file_name.endswith(".txt"))  # True
```

---

## `.isalpha()`, `.isdigit()`, `.isalnum()`

Checks what kind of characters are in a string.

```python
"abc".isalpha()    # True
"123".isdigit()    # True
"abc123".isalnum() # True
```

---

# Dictionary Methods

## Access by key

```python
person = {
    "name": "Connor",
    "age": 27
}

print(person["name"])  # Connor
```

---

## `.get()`

Safely gets a value by key.

```python
print(person.get("name"))     # Connor
print(person.get("height"))   # None
```

With a backup value:

```python
print(person.get("height", "Unknown"))
```

---

## `.keys()`

Gets all keys.

```python
print(person.keys())
```

---

## `.values()`

Gets all values.

```python
print(person.values())
```

---

## `.items()`

Gets key-value pairs.

```python
for key, value in person.items():
    print(key, value)
```

---

## Add or update a value

```python
person["age"] = 28
person["city"] = "Dawsonville"
```

---

## `.pop()`

Removes a key and returns its value.

```python
age = person.pop("age")

print(age)
```

---

# Tuple Tricks

Tuples are like locked lists.

```python
my_tuple = (1, 2, 3)
```

You can index them:

```python
print(my_tuple[0])
```

You can loop through them:

```python
for item in my_tuple:
    print(item)
```

You cannot change them:

```python
# my_tuple[0] = 99
# This causes an error
```

---

# Set Methods

## `.add()`

Adds one item.

```python
my_set = {"apple", "banana"}

my_set.add("cherry")
```

---

## `.remove()`

Removes an item.

```python
my_set.remove("banana")
```

Causes an error if the item does not exist.

---

## `.discard()`

Removes an item safely.

```python
my_set.discard("orange")
```

No error if the item does not exist.

---

## Set Union

Combines sets.

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)  # {1, 2, 3, 4, 5}
```

---

## Set Intersection

Gets items that appear in both sets.

```python
print(a & b)  # {3}
```

---

## Set Difference

Gets items in one set but not the other.

```python
print(a - b)  # {1, 2}
```

---

# Range Tricks

## Basic range

```python
for number in range(5):
    print(number)
```

Output:

```python
0
1
2
3
4
```

---

## Start and stop

```python
for number in range(1, 6):
    print(number)
```

Output:

```python
1
2
3
4
5
```

---

## Start, stop, step

```python
for number in range(0, 10, 2):
    print(number)
```

Output:

```python
0
2
4
6
8
```

---

# Type Conversion

## Convert to string

```python
age = 27

text = str(age)
```

---

## Convert to integer

```python
number = int("25")
```

---

## Convert to float

```python
price = float("19.99")
```

---

## Convert to list

```python
letters = list("hello")

print(letters)  # ["h", "e", "l", "l", "o"]
```

---

## Convert to set

```python
numbers = [1, 2, 2, 3]

unique_numbers = set(numbers)

print(unique_numbers)  # {1, 2, 3}
```

---

# Common Loop Patterns

## Loop through a list

```python
names = ["Alex", "Connor", "Sam"]

for name in names:
    print(name)
```

---

## Loop through indexes

```python
names = ["Alex", "Connor", "Sam"]

for i in range(len(names)):
    print(i, names[i])
```

---

## Better way: `enumerate()`

```python
names = ["Alex", "Connor", "Sam"]

for index, name in enumerate(names):
    print(index, name)
```

---

## Loop through dictionary

```python
person = {
    "name": "Connor",
    "age": 27
}

for key, value in person.items():
    print(key, value)
```

---

# Quick Capability Table

| Tool / Method | Works On | What It Does |
|---|---|---|
| `len()` | list, string, dict, tuple, set | Gets number of items |
| `min()` | list, tuple, set, string, range | Gets smallest value |
| `max()` | list, tuple, set, string, range | Gets largest value |
| `sum()` | numeric lists, tuples, sets, ranges | Adds values |
| `sorted()` | list, tuple, set, string, dict | Returns sorted version |
| `in` | list, string, dict, tuple, set | Checks if value exists |
| `[x]` | list, string, tuple | Gets item by index |
| `[start:stop]` | list, string, tuple | Gets a slice |
| `.append()` | list | Adds item to end |
| `.remove()` | list, set | Removes item |
| `.pop()` | list, dict, set | Removes and returns item |
| `.sort()` | list | Sorts list permanently |
| `.split()` | string | Turns string into list |
| `.join()` | string method used on list of strings | Turns list into string |
| `.get()` | dict | Safely gets value by key |
| `.keys()` | dict | Gets dictionary keys |
| `.values()` | dict | Gets dictionary values |
| `.items()` | dict | Gets key-value pairs |
| `.add()` | set | Adds item to set |
| `.discard()` | set | Safely removes item from set |
| `enumerate()` | list, tuple, string | Gives index and value |
| `range()` | numbers / loops | Creates number sequence |
| `str()` | almost anything | Converts to string |
| `int()` | number-like values | Converts to integer |
| `float()` | number-like values | Converts to decimal |
| `list()` | iterable values | Converts to list |
| `set()` | iterable values | Removes duplicates |

---

# Quick Memory Key

- `len()` = How many?
- `min()` = Smallest?
- `max()` = Biggest?
- `sum()` = Add them up
- `sorted()` = Give me a sorted copy
- `.sort()` = Sort the original list
- `in` = Is it there?
- `[0]` = First item
- `[-1]` = Last item
- `[1:4]` = Get part of it
- `.append()` = Add to list
- `.pop()` = Remove and keep it
- `.remove()` = Remove by value
- `.split()` = String to list
- `.join()` = List to string
- `.get()` = Safe dictionary lookup
- `.items()` = Dictionary loop helper
- `set()` = Remove duplicates
- `enumerate()` = Index + value while looping

---

# Beginner Power Combos

## Remove duplicates from a list

```python
numbers = [1, 2, 2, 3, 3, 4]

unique_numbers = list(set(numbers))

print(unique_numbers)
```

---

## Count items in a list

```python
colors = ["red", "blue", "red", "green"]

print(colors.count("red"))  # 2
```

---

## Sort a list without changing original

```python
scores = [88, 92, 75]

sorted_scores = sorted(scores)
```

---

## Sort a list permanently

```python
scores = [88, 92, 75]

scores.sort()
```

---

## Turn a sentence into words

```python
sentence = "Python is awesome"

words = sentence.split()

print(words)
```

---

## Turn words into a sentence

```python
words = ["Python", "is", "awesome"]

sentence = " ".join(words)

print(sentence)
```

---

## Safely get dictionary data

```python
student = {
    "name": "Connor",
    "grade": 95
}

print(student.get("name", "Unknown"))
print(student.get("email", "No email listed"))
```

---

## Loop through a list with numbers

```python
names = ["Alex", "Connor", "Sam"]

for index, name in enumerate(names):
    print(index, name)
```

---

## Check if input is a number

```python
user_input = input("Enter a number: ")

if user_input.isdigit():
    number = int(user_input)
    print(number)
else:
    print("That is not a number.")
```

---

# Big Beginner Rule

If the method has a dot before it, like this:

```python
my_list.append(4)
```

It belongs to that object.

If it looks like this:

```python
len(my_list)
```

It is a built-in function that can work on different objects.
