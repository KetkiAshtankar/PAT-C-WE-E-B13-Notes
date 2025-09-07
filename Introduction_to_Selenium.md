
---

# 📘 Introduction to Python Selenium Framework

## 1. What is Python Selenium Framework?

* **Definition:**
  A Selenium Framework is a structured way of writing, organizing, and maintaining Selenium test scripts using Python.
* Instead of writing messy test scripts, we use frameworks for:

  * **Reusability**: Write once, use multiple times.
  * **Maintainability**: Easy to update when the application changes.
  * **Scalability**: Handle large test suites.
  * **Integration**: Works with CI/CD tools like Jenkins.

👉 Think of it as a **blueprint** for automation testing that brings discipline and organization.

---

## 2. Why Selenium & Advantages

* **Why Selenium?**
  Selenium is the most popular open-source automation testing tool for web applications. It interacts directly with the browser, just like a real user.

* **Advantages:**
  ✅ Open Source (Free to use)
  ✅ Supports multiple programming languages (Python, Java, C#, Ruby, etc.)
  ✅ Cross-browser testing (Chrome, Firefox, Edge, Safari)
  ✅ Cross-platform support (Windows, Mac, Linux)
  ✅ Can run in parallel (Selenium Grid)
  ✅ Active community & regular updates
  ✅ Integrates with testing frameworks (Pytest, Robot, TestNG) and CI/CD tools

---

## 3. What are its Versions?

* **Selenium RC (Remote Control)** – Outdated, no longer used.
* **Selenium IDE** – Browser extension for recording tests (good for beginners).
* **Selenium WebDriver** – Core component, interacts directly with browsers (most widely used).
* **Selenium Grid** – Runs tests in parallel across multiple machines & browsers.
* **Latest Version (Selenium 4)** –

  * W3C standard compliance
  * Relative locators (`above`, `below`, `near`)
  * Better support for Chrome DevTools
  * Enhanced Selenium Grid

---

## 4. Supported OS, Browsers, and Programming Languages

* **Operating Systems (OS):**
  ✅ Windows
  ✅ macOS
  ✅ Linux

* **Browsers Supported:**
  ✅ Google Chrome
  ✅ Mozilla Firefox
  ✅ Microsoft Edge
  ✅ Safari (Mac only)
  ✅ Opera

* **Programming Languages Supported:**
  ✅ Python
  ✅ Java
  ✅ C#
  ✅ Ruby
  ✅ JavaScript (Node.js)
  ✅ Kotlin

👉 In our course, we’ll be using **Python + Selenium WebDriver**.

---

# 🖥️ First Small Automation Script (Python + Selenium)

This script will:

1. Open Chrome
2. Navigate to Google
3. Search for "Selenium Python"
4. Print the page title
5. Close the browser

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Step 1: Launch Chrome Browser
driver = webdriver.Chrome()

# Step 2: Open Google
driver.get("https://www.google.com")

# Step 3: Find the search box and type "Selenium Python"
search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Selenium Python")
search_box.send_keys(Keys.RETURN)   # Press Enter

# Step 4: Wait & Print Title
time.sleep(2)
print("Page Title:", driver.title)

# Step 5: Close the browser
driver.quit()
```

✅ Output Example:

```
Page Title: Selenium Python - Google Search
```

---

---

# 🔧 Installing Selenium in PyCharm

There are **two easy ways** to install Selenium in PyCharm.

---

## ✅ Method 1: Using PyCharm’s Package Manager

1. **Open PyCharm**

   * Launch your PyCharm IDE.

2. **Create / Open a Project**

   * Either create a new Python project or open an existing one.

3. **Open Settings/Preferences**

   * Windows/Linux: `File` → `Settings`
   * Mac: `PyCharm` → `Preferences`

4. **Go to Project Interpreter**

   * Navigate to: `Project: <your_project_name>` → `Python Interpreter`

5. **Add Selenium**

   * Click on the **“+” (Add Package)** button.
   * In the search bar, type **selenium**.
   * Select the latest version and click **Install Package**.

6. **Verify Installation**

   * Selenium should now appear in the package list.

---

## ✅ Method 2: Using Terminal inside PyCharm

1. **Open the Terminal** (bottom panel in PyCharm).

2. Run the command:

   ```bash
   pip install selenium
   ```

3. **Verify Installation**

   ```bash
   pip show selenium
   ```

   It should display details like version, location, etc.

---
