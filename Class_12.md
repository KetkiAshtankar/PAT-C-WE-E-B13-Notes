# 📘 Python Concepts – Detailed Notes

## 🔹 1. Lambda Function

A **lambda function** is a **small, anonymous function** (no name).
It’s often used when you need a function **for a short period of time**.

📌 Syntax:

```python
lambda arguments: expression
```

### 🍕 Pizza Example ( ):

Instead of writing a big function to calculate the **price with toppings**, we can use a lambda.

```python
# Normal function
def add_cheese(price):
    return price + 20

# Lambda function
add_cheese = lambda price: price + 20

print(add_cheese(100))  # Output: 120
```

💡 Think of lambda as a **one-line chef** who makes only one type of pizza topping quickly.

---

## 🔹 2. Map() and Filter() Functions

### ✅ `map()`

`map()` applies a function to **each element** of a list (or any iterable).

📌 Syntax:

```python
map(function, iterable)
```

### 🍕 Example:

```python
prices = [100, 200, 300]
# Add 20 cheese topping to each pizza
new_prices = list(map(lambda x: x + 20, prices))
print(new_prices)  # [120, 220, 320]
```

---

### ✅ `filter()`

`filter()` is used to **filter elements** based on a condition (True/False).

📌 Syntax:

```python
filter(function, iterable)
```

### 🍕 Example:

```python
prices = [100, 200, 300, 400]
# Only keep pizzas with price > 250
expensive = list(filter(lambda x: x > 250, prices))
print(expensive)  # [300, 400]
```

💡 Think:

* `map()` → transform everything
* `filter()` → pick only what’s needed

---

## 🔹 3. Iterator

An **iterator** is an object you can **loop through**.
It remembers its position, so it **doesn’t restart unless reset**.

📌 Example:

```python
nums = [1, 2, 3]
it = iter(nums)

print(next(it))  # 1
print(next(it))  # 2
print(next(it))  # 3
```

### 🍕 Pizza Example:

Iterator is like a **pizza slicer** – each `next()` call gives you **one slice** until no slices are left.

---

## 🔹 4. Generator

A **generator** is like an iterator but **easier to write**.
We use `yield` instead of `return`.

📌 Example:

```python
def pizza_slices():
    yield "🍕 Slice 1"
    yield "🍕 Slice 2"
    yield "🍕 Slice 3"

for slice in pizza_slices():
    print(slice)
```

✅ Output:

```
🍕 Slice 1
🍕 Slice 2
🍕 Slice 3
```

💡 **Difference with Iterator**:

* Iterator → we create manually with `iter()` & `next()`.
* Generator → Python creates iterator automatically using `yield`.

---

## 🔹 5. Decorators

A **decorator** is like a **wrapper around a function**.
It adds extra toppings (features) without changing the function itself.

📌 Example:

```python
def add_toppings(func):
    def wrapper():
        print("🌶️ Adding chili flakes!")
        func()
    return wrapper

@add_toppings
def make_pizza():
    print("🍕 Making a plain pizza.")

make_pizza()
```

✅ Output:

```
🌶️ Adding chili flakes!
🍕 Making a plain pizza.
```

💡 Think:
Function = pizza base
Decorator = extra topping (without changing base)

---

## 🔹 6. Introduction to Regex

**Regex (Regular Expressions)** = A way to **search and match text patterns**.

📌 Importing:

```python
import re
```

### 🔹 Common Patterns:

* `.` → any character
* `\d` → digit (0–9)
* `\w` → word (letters, numbers, underscore)
* `\s` → whitespace
* `^` → start of string
* `$` → end of string

---

### 🍕 Examples with Pizza & Numbers:

```python
import re

# Find all prices
text = "Pizza 100, Burger 80, Pizza 200"
prices = re.findall(r"\d+", text)
print(prices)  # ['100', '80', '200']

# Match pizza word
print(re.findall(r"Pizza", text))  # ['Pizza', 'Pizza']
```

💡 Regex is like a **pizza delivery address filter** – you define a **pattern**, and it finds all matching addresses.

---

# 🎯 Quick Comparison

| Concept       | What It Does (Pizza 🍕 Example)            |
| ------------- | ------------------------------------------ |
| **Lambda**    | Quick one-line recipe (extra cheese)       |
| **Map**       | Apply topping to all pizzas                |
| **Filter**    | Select only expensive pizzas               |
| **Iterator**  | Eat slices one by one                      |
| **Generator** | Chef gives slices one by one using `yield` |
| **Decorator** | Add toppings automatically                 |
| **Regex**     | Find pizza names/numbers in text           |

