# Python Collection Types Cheat Sheet

## List

### Syntax
```python
my_list = [1, 2, 3]
```

### General Use
A list stores multiple items in order. Lists are mutable (changeable), allow duplicates, and are the most commonly used collection type in Python.

Use a list when you need a group of items that may change over time.

---

## Dictionary

### Syntax
```python
my_dict = {
    "name": "Connor",
    "age": 27
}
```

### General Use
A dictionary stores data as key-value pairs. Instead of looking up values by position, you look them up by name (key).

Use a dictionary when data needs labels or when you want fast lookups.

---

## Tuple

### Syntax
```python
my_tuple = (1, 2, 3)
```

### General Use
A tuple stores multiple items in order, just like a list. However, tuples are immutable (cannot be changed after creation).

Use a tuple when the data should remain fixed.

---

## Set

### Syntax
```python
my_set = {1, 2, 3}
```

### General Use
A set stores unique values only. Duplicate values are automatically removed.

Use a set when you care about uniqueness or need to quickly check whether a value exists.

---

## Array

### Syntax
```python
from array import array

my_array = array("i", [1, 2, 3])
```

### General Use
An array stores items of the same data type more efficiently than a list.

Arrays are uncommon in beginner Python. Most of the time, lists are used instead.

---

## String

### Syntax
```python
my_string = "hello"
```

### General Use
A string stores text. Strings are immutable and behave like a sequence of characters.

```python
print(my_string[0])  # h
```

Use strings whenever working with text.

---

## Range

### Syntax
```python
my_range = range(5)
```

### General Use
A range generates a sequence of numbers without storing them all in memory.

Most commonly used in loops.

```python
for number in range(5):
    print(number)
```

---

## Boolean

### Syntax
```python
is_logged_in = True
is_admin = False
```

### General Use
A boolean stores either True or False.

Used for conditions, comparisons, and decision-making.

---

## NoneType

### Syntax
```python
value = None
```

### General Use
None represents the absence of a value.

Think of it as Python's way of saying "nothing is here."

---

# Capability Comparison

| Type | Syntax | Ordered | Mutable | Duplicates Allowed | Indexed | Main Use |
|--------|--------|--------|--------|--------|--------|--------|
| List | `[ ]` | Yes | Yes | Yes | Yes | General-purpose collection |
| Dictionary | `{key: value}` | Yes | Yes | Values: Yes | By key | Labeled data / lookups |
| Tuple | `( )` | Yes | No | Yes | Yes | Fixed data |
| Set | `{ }` | No | Yes | No | No | Unique values |
| Array | `array()` | Yes | Yes | Yes | Yes | Same-type data |
| String | `" "` | Yes | No | Yes | Yes | Text |
| Range | `range()` | Yes | No | No | Yes | Number sequences |
| Boolean | `True/False` | N/A | No | N/A | N/A | Conditions |
| NoneType | `None` | N/A | No | N/A | N/A | No value |

# Quick Memory Key

- List = Normal collection
- Dictionary = Labeled collection
- Tuple = Locked list
- Set = No duplicates
- Array = Efficient same-type list
- String = Text
- Range = Loop numbers
- Boolean = True or False
- None = Nothing / Empty value

# Most Common on a Typical Python Program

1. String
2. Integer
3. Float
4. Boolean
5. List
6. Dictionary
7. Tuple
8. Set

If you're in an intro Python course like IT-140, you'll spend about 90% of your time working with:

- Strings
- Integers
- Floats
- Booleans
- Lists
- Dictionaries

Everything else is useful but appears less frequently.
