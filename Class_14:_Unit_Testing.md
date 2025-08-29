
---

# 📝 Unit Testing in Python – Easy Notes

## 🔹 What is Unit Testing?

* Unit testing means **testing small pieces of code (functions, classes, methods)** to make sure they work correctly.
* Think of it as checking if each LEGO block is fine before building the whole castle.

---

## 🔹 Why Do We Need Unit Testing?

* To **catch bugs early**.
* To make sure future code changes don’t break old code (**regression testing**).
* To improve **confidence** in your code.

---

## 🔹 Python’s Built-in `unittest` Module

Python gives us a testing tool called **`unittest`**.
It helps us:

* Write test cases
* Run them automatically
* Show results (✅ pass or ❌ fail)

---

## 🔹 Structure of a Unit Test File

A test file usually looks like this:

```python
import unittest   # Import the unittest module

# Code to test
def add_numbers(a, b):
    return a + b

# Test Class
class TestMathOperations(unittest.TestCase):
    
    # Test Case
    def test_add(self):
        self.assertEqual(add_numbers(2, 3), 5)   # 2+3 = 5
        self.assertEqual(add_numbers(-1, 1), 0)  # -1+1 = 0
        self.assertEqual(add_numbers(0, 0), 0)   # 0+0 = 0

# Boilerplate Code
if __name__ == '__main__':
    unittest.main()
```

---

## 🔹 Important Parts Explained

1. **`import unittest`**
   → We import Python’s test module.

2. **Code under test**

   ```python
   def add_numbers(a, b):
       return a + b
   ```

3. **Test Class**

   ```python
   class TestMathOperations(unittest.TestCase):
   ```

   → Always inherits from `unittest.TestCase`.

4. **Test Methods**

   ```python
   def test_add(self):
       self.assertEqual(add_numbers(2, 3), 5)
   ```

   → Method name must **start with `test_`**.
   → Use `assertEqual` to compare **expected vs actual**.

5. **Boilerplate**

   ```python
   if __name__ == '__main__':
       unittest.main()
   ```

   → Runs the test when file is executed directly.
   → `__name__ == '__main__'` means *run this file directly, not when imported.*

---

## 🔹 Common Assertions in `unittest`

* `assertEqual(a, b)` → checks if `a == b`
* `assertNotEqual(a, b)` → checks if `a != b`
* `assertTrue(x)` → checks if `x` is `True`
* `assertFalse(x)` → checks if `x` is `False`
* `assertIsNone(x)` → checks if `x` is `None`
* `assertIn(a, b)` → checks if `a` in `b`

---

## 🔹 Naming Convention for Test Files

* Test file names usually start with **`test_`**.
  Example:

  * `test_operations.py`
  * `test_math.py`
* This helps Python and tools like `pytest` detect tests automatically.

---

## 🔹 Running the Test

### ✅ Way 1: Run with Python

```bash
python test_operations.py
```

### ✅ Way 2: Run with `unittest` command

```bash
python -m unittest test_operations.py
```

### ✅ Way 3: Run all tests in a folder

```bash
python -m unittest discover
```

---

## 🔹 Output Example

```
.
----------------------------------------------------------------------
Ran 1 test in 0.001s

OK
```

* ✅ Dot (`.`) means test passed.
* ❌ `F` means test failed.

---
