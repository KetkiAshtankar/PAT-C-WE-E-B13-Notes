# 📘 Advanced Python

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



---

## 🟢 Basics of Regex

| Symbol  | Meaning                               | Example   | Matches                           |
| ------- | ------------------------------------- | --------- | --------------------------------- |
| `.`     | Any single character (except newline) | `p.t`     | `pat`, `pet`, `p9t`               |
| `^`     | Start of string                       | `^Hello`  | `Hello World` ✅, `Hi Hello` ❌     |
| `$`     | End of string                         | `world$`  | `Hello world` ✅, `world peace` ❌  |
| `*`     | 0 or more repetitions                 | `a*`      | `""`, `a`, `aa`, `aaaa`           |
| `+`     | 1 or more repetitions                 | `a+`      | `a`, `aa`, `aaaa` (but not empty) |
| `?`     | 0 or 1 occurrence (optional)          | `colou?r` | `color`, `colour`                 |
| `{n}`   | Exactly `n` times                     | `a{3}`    | `aaa`                             |
| `{n,}`  | At least `n` times                    | `a{2,}`   | `aa`, `aaa`, `aaaa...`            |
| `{n,m}` | Between `n` and `m` times             | `a{2,4}`  | `aa`, `aaa`, `aaaa`               |

---

## 🟡 Character Classes (Matching Groups of Characters)

| Pattern       | Meaning                      | Example     | Matches                    |
| ------------- | ---------------------------- | ----------- | -------------------------- |
| `[abc]`       | Match `a` or `b` or `c`      | `b[aeiou]g` | `bag`, `beg`, `big`, `bug` |
| `[^abc]`      | NOT `a`, `b`, or `c`         | `[^0-9]`    | Any non-digit              |
| `[a-z]`       | Any lowercase letter         | `[a-z]{3}`  | `abc`, `xyz`               |
| `[A-Z]`       | Any uppercase letter         | `[A-Z]{2}`  | `AB`, `XY`                 |
| `[0-9]`       | Any digit                    | `\d`        | `5`, `9`                   |
| `[a-zA-Z0-9]` | Letters + digits             | `\w`        | `hello123`                 |
| `.`           | Any character except newline | `c.t`       | `cat`, `cut`, `c9t`        |

---

## 🔵 Predefined Character Classes (Shortcuts)

| Symbol | Meaning                                      | Example | Matches          |
| ------ | -------------------------------------------- | ------- | ---------------- |
| `\d`   | Digit (0–9)                                  | `\d{3}` | `123`            |
| `\D`   | Non-digit                                    | `\D+`   | `abc`, `XYZ`     |
| `\w`   | Word character (letters, digits, underscore) | `\w+`   | `hello_123`      |
| `\W`   | Non-word character                           | `\W+`   | `!@#`, spaces    |
| `\s`   | Whitespace (space, tab, newline)             | `a\sb`  | `a b`            |
| `\S`   | Non-whitespace                               | `\S+`   | `hello`, `pizza` |

---

## 🟣 Groups & Alternation

| Pattern | Meaning                               | Example          | Matches                |       |              |
| ------- | ------------------------------------- | ---------------- | ---------------------- | ----- | ------------ |
| `(abc)` | Grouping                              | `(ab)+`          | `ab`, `abab`, `ababab` |       |              |
| `\1`    | Backreference (repeat previous group) | `(ha)\1`         | `haha`                 |       |              |
| \`a     | b\`                                   | OR (alternation) | \`cat                  | dog\` | `cat`, `dog` |

---

## 🟤 Practical Examples

### 🍕 Pizza Examples (Layman’s Way)

1. **Find any pizza topping that ends with “oni”**
   Regex: `\w+oni`
   Matches: `pepperoni`, `zucchini` (but not `cheese`).

2. **Find pizzas with “extra cheese” or “extra sauce”**
   Regex: `extra (cheese|sauce)`
   Matches: `extra cheese`, `extra sauce`.

3. **Find numbers in menu prices**
   Regex: `\d+`
   Matches: `250`, `499`, `1000`.

---

### 🔢 Numbers & Words

* Find **all 3-digit numbers**:
  Regex → `\b\d{3}\b`
  Matches: `123`, `456`

* Find **words starting with capital letter**:
  Regex → `\b[A-Z][a-z]+\b`
  Matches: `Hello`, `Pizza`, `Regex`

---

### 📧 Emails

Regex → `^[\w\.-]+@[\w\.-]+\.\w{2,3}$`
Matches:
✅ `test123@gmail.com`
✅ `hello.world@company.org`
❌ `invalid@com`

---

### 📞 Phone Numbers

Regex → `^\+?[0-9]{10,13}$`
Matches:
✅ `9876543210`
✅ `+919876543210`
❌ `98765-43210`

---

### 🔐 Passwords (At least 8 chars, 1 number, 1 uppercase, 1 special char)

Regex → `^(?=.*[0-9])(?=.*[A-Z])(?=.*[@#$%^&+=!]).{8,}$`
Matches:
✅ `Hello@123`
❌ `hello123` (missing uppercase + special char)

---

### 🌍 URLs

Regex → `https?://[^\s/$.?#].[^\s]*`
Matches:
✅ `http://example.com`
✅ `https://google.com`

---

## 📝 Summary

* Use **regex** when you want to **search, extract, or validate patterns** in text.
* It’s like giving your program **super-search powers** 🔍.
* Start small (`.`, `\d`, `[a-z]`) → then move to **groups, backreferences, and lookaheads**.

---

# 🐍 Python `re` (Regular Expressions) Functions

The `re` module in Python provides all the important functions to **search, match, split, replace, and validate** text using **patterns**.

Import first:

```python
import re
```

---

## 🔹 1. `re.match(pattern, string)`

* **Checks ONLY at the beginning** of the string.
* Returns a match object if found, else `None`.

```python
import re

text = "pizza is tasty"

match = re.match(r"pizza", text)
print(match.group())   # pizza ✅

match = re.match(r"tasty", text)
print(match)   # None ❌ (not at start)
```

---

## 🔹 2. `re.search(pattern, string)`

* **Searches anywhere** in the string.
* Returns the **first match**.

```python
text = "I love pizza with cheese"

res = re.search(r"pizza", text)
print(res.group())  # pizza ✅

res = re.search(r"cheese", text)
print(res.group())  # cheese ✅
```

---

## 🔹 3. `re.findall(pattern, string)`

* Returns **all matches** as a list.

```python
text = "My order: 2 pizzas, 3 burgers, and 4 pizzas more"

numbers = re.findall(r"\d+", text)  
print(numbers)  # ['2', '3', '4'] ✅

words = re.findall(r"pizza", text)
print(words)  # ['pizza', 'pizza']
```

---

## 🔹 4. `re.finditer(pattern, string)`

* Returns an **iterator** with match objects.
* More powerful than `findall` (you get position + match).

```python
text = "pizza pizza burger"

for m in re.finditer(r"pizza", text):
    print(m.group(), "at position", m.start())
```

**Output:**

```
pizza at position 0
pizza at position 6
```

---

## 🔹 5. `re.sub(pattern, repl, string)`

* Replace all matches with something else.

```python
text = "I eat pizza, pizza, pizza!"

new_text = re.sub(r"pizza", "burger", text)
print(new_text)  
# I eat burger, burger, burger!
```

---

## 🔹 6. `re.subn(pattern, repl, string)`

* Same as `sub`, but returns a tuple:
  `(new_string, number_of_replacements)`

```python
text = "pizza pizza pizza"

res = re.subn(r"pizza", "pasta", text)
print(res)  # ('pasta pasta pasta', 3)
```

---

## 🔹 7. `re.split(pattern, string)`

* Split string by regex pattern.

```python
text = "one,two;three four"

parts = re.split(r"[,; ]", text)
print(parts)  
# ['one', 'two', 'three', 'four']
```

---

## 🔹 8. `re.compile(pattern)`

* Compiles regex into an object for **reuse**.

```python
pattern = re.compile(r"pizza")

print(pattern.findall("pizza burger pizza"))  
# ['pizza', 'pizza']
```

---

## 🔹 9. Match Object Methods

If a match is found, you can use:

```python
text = "Order: 2 pizzas"

m = re.search(r"\d+", text)

print(m.group())   # 2 (matched text)
print(m.start())   # 7 (start index)
print(m.end())     # 8 (end index)
print(m.span())    # (7, 8)
```

---

## 🔹 10. Flags in Regex (`re.I`, `re.M`, `re.S`)

You can add **flags** to change regex behavior.

```python
text = "Pizza\nis tasty"

# Case insensitive
print(re.findall(r"pizza", text, re.I))  
# ['Pizza']

# Multiline (^ matches start of each line)
print(re.findall(r"^is", text, re.M))  
# ['is']

# Dot matches newline
print(re.findall(r".+", text, re.S))  
# ['Pizza\nis tasty']
```

---

# 🍕 Layman Example: Pizza Ordering

```python
order = "2 pizzas, 1 burger, 3 pizzas, 5 cokes"

# Find all numbers
print(re.findall(r"\d+", order))  
# ['2', '1', '3', '5']

# Replace pizza with pasta
print(re.sub(r"pizzas?", "pasta", order))  
# 2 pasta, 1 burger, 3 pasta, 5 cokes

# Find pizza count
for m in re.finditer(r"pizzas?", order):
    print("Found", m.group(), "at", m.span())
```

---

✅ With these 10 functions + flags, you can handle **95% of regex use cases in Python**.

