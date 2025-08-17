## 🔹 1. Functions

### ✅ What is a Function?

* A **function** is a block of organized, reusable code that performs a specific task.
* Functions help in breaking a program into smaller, manageable parts.

### 🧠 Why use Functions?

* **Reusability** → write once, use multiple times.
* **Readability** → makes code cleaner.
* **Maintainability** → easier to fix/update.

### 🖥 Example 1 – Simple Function

```python
def greet(name):
    """This function greets the person passed as argument"""
    return f"Hello, {name}!"

print(greet("Ketki"))   # Hello, Ketki!
print(greet("Rahul"))   # Hello, Rahul!
```

### 🖥 Example 2 – Function with Default Arguments

```python
def power(base, exponent=2):
    return base ** exponent

print(power(3))     # 9 (3^2)
print(power(2, 3))  # 8 (2^3)
```

### 🖥 Example 3 – Function Returning Multiple Values

```python
def calculate(a, b):
    return a + b, a - b, a * b

add, sub, mul = calculate(10, 5)
print(add, sub, mul)   # 15 5 50
```

---

## 🔹 2. Closure Functions

### ✅ What is a Closure?

* A **closure** is a function that “remembers” variables from the scope where it was created, **even after that scope has finished executing**.
* It is created when:

  1. A function is defined inside another function.
  2. The inner function references variables from the outer function.
  3. The outer function returns the inner function.

### 🖥 Example – Closure

```python
def outer_function(msg):
    def inner_function():
        print("Message:", msg)
    return inner_function

# Outer function executed, but inner still remembers 'msg'
closure = outer_function("Hello from Closure!")
closure()   # Message: Hello from Closure!
```

🔑 Even though `outer_function` has finished, the inner function keeps the value of `msg`.

### 🖥 Example – Practical Use of Closure

```python
def make_multiplier(n):
    def multiplier(x):
        return x * n
    return multiplier

double = make_multiplier(2)
triple = make_multiplier(3)

print(double(5))  # 10
print(triple(5))  # 15
```

✔️ Closures are useful for creating **customized functions**.

---

## 🔹 3. Callback Functions

### ✅ What is a Callback Function?

* A **callback function** is a function passed as an **argument** to another function.
* The receiving function can call it (or “call back”) later.
* Widely used in **event handling, async programming, GUI apps**.

### 🖥 Example – Simple Callback

```python
def process_data(data, callback):
    result = data.upper()
    callback(result)

def print_result(output):
    print("Processed:", output)

process_data("hello", print_result)
# Output: Processed: HELLO
```

### 🖥 Example – Callback with Lambda

```python
def calculate(a, b, callback):
    return callback(a, b)

# Using different callbacks
print(calculate(5, 3, lambda x, y: x + y))  # 8
print(calculate(5, 3, lambda x, y: x * y))  # 15
```

✔️ Here, the callback decides **how the calculation happens**.

---

## 🔹 4. File Handling

### ✅ What is File Handling?

* File handling in Python allows us to **create, read, update, and delete files**.
* Uses the built-in `open()` function.

### 📂 Modes of Opening Files

| Mode  | Meaning                                         |
| ----- | ----------------------------------------------- |
| `"r"` | Read (default) – error if file doesn’t exist    |
| `"w"` | Write – creates new file or overwrites existing |
| `"a"` | Append – adds to end of file                    |
| `"x"` | Create – creates new file, error if exists      |
| `"b"` | Binary mode (e.g., `"rb"`, `"wb"`)              |
| `"t"` | Text mode (default)                             |

---

### 🖥 Example 1 – Writing to a File

```python
file = open("example.txt", "w")
file.write("Hello, this is a test file!")
file.close()
```

### 🖥 Example 2 – Reading a File

```python
file = open("example.txt", "r")
content = file.read()
print(content)
file.close()
```

### 🖥 Example 3 – Reading Line by Line

```python
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())
```

### 🖥 Example 4 – Append to a File

```python
with open("example.txt", "a") as file:
    file.write("\nThis line is appended.")
```

### 🖥 Example 5 – Handling Binary Files (like images)

```python
with open("photo.jpg", "rb") as file:
    data = file.read()
    print("File size:", len(data), "bytes")
```

---

# 📝 Summary

| Concept           | Meaning                                           | Example Use Case                  |
| ----------------- | ------------------------------------------------- | --------------------------------- |
| **Function**      | Reusable block of code                            | `def greet(name): return ...`     |
| **Closure**       | Inner function remembering outer variables        | Configurable multiplier functions |
| **Callback**      | Function passed to another function, called later | Event handling, async ops         |
| **File Handling** | Reading/writing files                             | Saving logs, configs, user data   |

