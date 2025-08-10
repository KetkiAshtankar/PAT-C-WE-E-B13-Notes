````markdown
# Python Data Structures – Notes & Cheat Sheet

---

## 📌 1. LIST
- **Mutable** → can be changed after creation
- **Ordered** → elements maintain insertion order
- **Allows duplicates**
- Written with square brackets `[]`

### Example:
```python
my_list = [10, 20, 30, 40]
````

### Common Operations:

```python
my_list[0]           # Indexing → 10
my_list[1:3]         # Slicing → [20, 30]
my_list.append(50)   # Add at end
my_list.insert(2, 25) # Add at index 2
my_list.remove(20)   # Remove first occurrence
my_list.pop()        # Remove last item
my_list.pop(1)       # Remove index 1
my_list.sort()       # Sort in place
sorted(my_list)      # Returns new sorted list
my_list.reverse()    # Reverse in place
my_list.count(30)    # Count occurrences
len(my_list)         # Length
```

---

## 📌 2. TUPLE

* **Immutable** → cannot be changed after creation
* **Ordered**
* **Allows duplicates**
* Written with parentheses `()`

### Example:

```python
my_tuple = (10, 20, 30, 40)
```

### Common Operations:

```python
my_tuple[0]          # Indexing
my_tuple[1:3]        # Slicing
my_tuple.count(10)   # Count occurrences
my_tuple.index(30)   # Find index
len(my_tuple)        # Length
sorted(my_tuple)     # Returns a sorted list (tuple unchanged)
```

---

## 📌 3. SET

* **Mutable**
* **Unordered** → no indexing
* **No duplicates**
* Written with curly braces `{}`

### Example:

```python
my_set = {10, 20, 30, 40}
```

### Common Operations:

```python
my_set.add(50)       # Add an element
my_set.remove(20)    # Remove element (Error if not found)
my_set.discard(20)   # Remove element (No error if not found)
my_set.pop()         # Remove random element
my_set.clear()       # Empty set
len(my_set)          # Length

# Set Operations
set1 | set2          # Union
set1 & set2          # Intersection
set1 - set2          # Difference
set1 ^ set2          # Symmetric difference
```

---

## 📌 4. DICTIONARY

* **Mutable**
* **Unordered** (insertion order preserved from Python 3.7+)
* Stores **Key–Value pairs**
* Written with curly braces `{}`

### Example:

```python
my_dict = {"name": "John", "age": 25}
```

### Common Operations:

```python
my_dict["name"]              # Access value
my_dict.get("age")           # Safe access
my_dict["city"] = "NY"       # Add / Update key
my_dict.pop("age")           # Remove key, return value
my_dict.popitem()            # Remove last inserted key-value pair
del my_dict["name"]          # Delete a key
my_dict.clear()              # Empty dictionary
my_dict.keys()               # All keys
my_dict.values()             # All values
my_dict.items()              # All key-value pairs
len(my_dict)                 # Number of items
```

---

## 🎯 REMOVE / DELETE METHODS CHEAT SHEET

| Data Structure | Method        | Action                           |
| -------------- | ------------- | -------------------------------- |
| **List**       | `pop()`       | Remove last item (or at index)   |
|                | `remove(x)`   | Remove first occurrence of `x`   |
|                | `clear()`     | Remove all elements              |
|                | `del list[i]` | Delete element at index          |
| **Tuple**      | ❌ Immutable   | Cannot remove directly           |
| **Set**        | `remove(x)`   | Remove `x` (error if not found)  |
|                | `discard(x)`  | Remove `x` (no error if missing) |
|                | `pop()`       | Remove random element            |
|                | `clear()`     | Remove all elements              |
| **Dict**       | `pop(key)`    | Remove by key                    |
|                | `popitem()`   | Remove last inserted item        |
|                | `del dict[k]` | Delete by key                    |
|                | `clear()`     | Remove all items                 |

---

## 📊 QUICK COMPARISON

| Feature    | List | Tuple | Set  | Dictionary       |
| ---------- | ---- | ----- | ---- | ---------------- |
| Mutable    | ✅    | ❌     | ✅    | ✅                |
| Ordered    | ✅    | ✅     | ❌    | ✅                |
| Duplicates | ✅    | ✅     | ❌    | Keys ❌, Values ✅ |
| Indexing   | ✅    | ✅     | ❌    | Keys only        |
| Syntax     | `[]` | `()`  | `{}` | `{key: val}`     |

---
