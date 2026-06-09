# Python Data Type Methods & Tricks Cheat Sheet (Search-Optimized)

> Designed for fast Ctrl+F searching.
>
> Search tags:
> LEN, MIN, MAX, SUM, SORTED, APPEND, EXTEND, INSERT, REMOVE, POP, COUNT, INDEX, SPLIT, JOIN, GET, ITEMS, ENUMERATE, RANGE, COPY, SLICE

---

# TABLE OF CONTENTS

- LEN
- MIN / MAX
- SUM
- SORTED
- IN
- INDEXING
- SLICING
- COPY LIST
- APPEND
- EXTEND
- INSERT
- REMOVE
- POP
- SORT
- REVERSE
- COUNT
- INDEX METHOD
- LOWER / UPPER
- STRIP
- REPLACE
- SPLIT
- JOIN
- FIND
- STARTSWITH / ENDSWITH
- ISALPHA / ISDIGIT / ISALNUM
- DICTIONARY GET
- KEYS / VALUES / ITEMS
- TUPLES
- SETS
- RANGE
- TYPE CONVERSION
- ENUMERATE
- COMMON LOOPS
- BEGINNER POWER COMBOS
- ZYBOOKS QUICK ANSWERS

---

# LEN

```python
len(my_list)
len(my_string)
len(my_dict)
```

Purpose: Count items.

---

# MIN / MAX

```python
min(numbers)
max(numbers)
```

Purpose: Smallest / largest value.

---

# SUM

```python
sum(numbers)
```

Purpose: Add numeric values.

---

# SORTED

```python
sorted(numbers)
sorted(numbers, reverse=True)
```

Returns a NEW sorted copy.

---

# IN

```python
"apple" in fruits
"name" in person
```

Checks whether a value exists.

---

# INDEXING

```python
my_list[0]     # first
my_list[-1]    # last
my_list[-2]    # second-to-last
```

---

# SLICING

```python
my_list[1:4]
my_list[:3]
my_list[2:]
my_list[::-1]
```

`[::-1]` = reverse

---

# COPY LIST

```python
copy_list = my_list[:]
```

Creates a copy.

DO NOT CONFUSE WITH:

```python
copy_list = my_list
```

That points to the same list.

---

# APPEND

```python
my_list.append(value)
```

Add ONE item to end.

---

# EXTEND

```python
my_list.extend([3, 4])
```

Add MULTIPLE items to end.

```python
[1,2].extend([3,4])
# [1,2,3,4]
```

---

# INSERT

```python
my_list.insert(index, value)
```

Insert before index.

Common:

```python
my_list.insert(0, value)
```

Insert at front.

---

# REMOVE

```python
my_list.remove(value)
```

Remove first matching value.

Errors if value not found.

---

# POP

```python
my_list.pop()
```

Remove and return last item.

```python
my_list.pop(0)
```

Remove and return item at index 0.

---

# SORT

```python
my_list.sort()
```

Sort ORIGINAL list.

```python
my_list.sort(reverse=True)
```

Descending.

---

# REVERSE

```python
my_list.reverse()
```

Reverse ORIGINAL list.

---

# COUNT

```python
my_list.count(value)
```

Count occurrences.

---

# INDEX METHOD

```python
my_list.index(value)
```

Find first position.

---

# LOWER / UPPER

```python
text.lower()
text.upper()
```

Change capitalization.

---

# STRIP

```python
text.strip()
```

Remove spaces from beginning/end.

---

# REPLACE

```python
text.replace("old", "new")
```

Replace text.

---

# SPLIT

```python
sentence.split()
```

String → List

```python
date.split("/")
```

Custom separator.

---

# JOIN

```python
" ".join(words)
```

List → String

```python
", ".join(items)
```

Important: items must be strings.

---

# FIND

```python
text.find("word")
```

Returns position or -1.

---

# STARTSWITH / ENDSWITH

```python
file.endswith(".txt")
url.startswith("https")
```

---

# ISALPHA / ISDIGIT / ISALNUM

```python
"abc".isalpha()
"123".isdigit()
"abc123".isalnum()
```

---

# DICTIONARY GET

```python
person.get("name")
person.get("email", "Unknown")
```

Safe lookup.

---

# KEYS / VALUES / ITEMS

```python
person.keys()
person.values()
person.items()
```

Loop:

```python
for key, value in person.items():
    print(key, value)
```

---

# TUPLES

```python
my_tuple = (1, 2, 3)
```

Can:
- Index
- Slice
- Loop

Cannot:
- Modify

---

# SETS

Add:

```python
my_set.add(value)
```

Remove:

```python
my_set.remove(value)
```

Safe remove:

```python
my_set.discard(value)
```

Union:

```python
a | b
```

Intersection:

```python
a & b
```

Difference:

```python
a - b
```

---

# RANGE

```python
range(5)
range(1, 6)
range(0, 10, 2)
```

(start, stop, step)

---

# TYPE CONVERSION

```python
str(x)
int(x)
float(x)
list(x)
set(x)
```

---

# ENUMERATE

```python
for index, value in enumerate(my_list):
    print(index, value)
```

Index + value together.

---

# COMMON LOOPS

List:

```python
for item in my_list:
    print(item)
```

Indexes:

```python
for i in range(len(my_list)):
    print(i, my_list[i])
```

Dictionary:

```python
for key, value in my_dict.items():
    print(key, value)
```

---

# BEGINNER POWER COMBOS

## Remove Duplicates

```python
unique = list(set(my_list))
```

## Reverse String

```python
word[::-1]
```

## Sort Copy

```python
new_list = sorted(old_list)
```

## Sort Original

```python
old_list.sort()
```

## String → Words

```python
words = sentence.split()
```

## Words → String

```python
sentence = " ".join(words)
```

## Safe Dictionary Lookup

```python
person.get("email", "No email")
```

---

# ZYBOOKS QUICK ANSWERS

## First Item

```python
my_list[0]
```

## Last Item

```python
my_list[-1]
```

## Copy List

```python
my_list[:]
```

## Count Value

```python
my_list.count(value)
```

## Find Position

```python
my_list.index(value)
```

## Remove Largest Value

```python
my_list.sort()
my_list.pop()
```

## Insert At Front

```python
my_list.insert(0, value)
```

## Add To End

```python
my_list.append(value)
```

---

# MEMORY KEYS

```text
len()      = how many?
min()      = smallest?
max()      = biggest?
sum()      = add them up

sorted()   = sorted copy
sort()     = sort original

append()   = add one
extend()   = add many
insert()   = add at spot

remove()   = remove by value
pop()      = remove by index

count()    = how many?
index()    = where is it?

split()    = string -> list
join()     = list -> string

get()      = safe dictionary lookup

[:]        = copy
[::-1]     = reverse

[0]        = first item
[-1]       = last item
```
