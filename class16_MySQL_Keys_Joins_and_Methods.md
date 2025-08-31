### **MySQL Keys Joins and Methods**

🔹 **What are Primary & Foreign Keys?**

  * **Primary Key:** A unique ID for each record in a table, just like your **Aadhar Number/SSN**.
  * **Foreign Key:** A link between two tables, like a **reference number on bills** connecting them to a customer.
* **Technical Explanation:**

  * **Primary Key** uniquely identifies a row and enforces uniqueness.
  * **Foreign Key** establishes a relationship between two tables.

🔹 **Demo: Creating Tables with Primary & Foreign Keys**

```sql
CREATE DATABASE SchoolDB;
USE SchoolDB;

CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100)
);

CREATE TABLE Enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (course_id) REFERENCES Courses(course_id)
);
```

---

## 🧠 Concept of Joins

Think of **joins** like combining information from **two tables** based on something in common.
To explain better, imagine:

* **Table A** → Boys and their skincare routines
* **Table B** → Girls and their skincare routines

We want to see:

* Who has similar skincare steps?
* Who has unique routines?

---

### Venn Diagram Explanation 🎨

1. **INNER JOIN**

   * Only the **common part** of both circles (intersection).
   * Example: If **both boys and girls use “Face Wash”**, it will appear.
   * ✅ Shows **only routines both follow**.

2. **LEFT JOIN**

   * Take **everything from Boys’ routines (left table)**, and add matching ones from Girls.
   * If no match, girl’s column shows **NULL**.
   * ✅ Shows **all boys’ routines**, with girl’s match if exists.

3. **RIGHT JOIN**

   * Take **everything from Girls’ routines (right table)**, and add matching ones from Boys.
   * If no match, boy’s column shows **NULL**.
   * ✅ Shows **all girls’ routines**, with boy’s match if exists.

4. **FULL OUTER JOIN** (if available)

   * Combines **all routines from both boys and girls**, matching where possible.
   * ✅ Shows **everything** from both sides.

---

## 🗄️ SQL Example with Database Creation

### Step 1: Create Database

```sql
CREATE DATABASE skincare_db;
USE skincare_db;
```

---

### Step 2: Create Tables

```sql
CREATE TABLE boys_routine (
    id INT PRIMARY KEY,
    step VARCHAR(50)
);

CREATE TABLE girls_routine (
    id INT PRIMARY KEY,
    step VARCHAR(50)
);
```

---

### Step 3: Insert Sample Data

```sql
INSERT INTO boys_routine VALUES
(1, 'Face Wash'),
(2, 'Moisturizer'),
(3, 'Sunscreen');

INSERT INTO girls_routine VALUES
(1, 'Face Wash'),
(2, 'Toner'),
(3, 'Sunscreen'),
(4, 'Serum');
```

---

### Step 4: Queries with Joins

#### 1. INNER JOIN → Common steps

```sql
SELECT b.step AS boy_step, g.step AS girl_step
FROM boys_routine b
INNER JOIN girls_routine g
ON b.step = g.step;
```

📌 Output:

* Face Wash | Face Wash
* Sunscreen | Sunscreen

---

#### 2. LEFT JOIN → All boys’ routines, girls if matching

```sql
SELECT b.step AS boy_step, g.step AS girl_step
FROM boys_routine b
LEFT JOIN girls_routine g
ON b.step = g.step;
```

📌 Output:

* Face Wash | Face Wash
* Moisturizer | NULL
* Sunscreen | Sunscreen

---

#### 3. RIGHT JOIN → All girls’ routines, boys if matching

```sql
SELECT b.step AS boy_step, g.step AS girl_step
FROM boys_routine b
RIGHT JOIN girls_routine g
ON b.step = g.step;
```

📌 Output:

* Face Wash | Face Wash
* NULL | Toner
* Sunscreen | Sunscreen
* NULL | Serum

---

#### 4. FULL OUTER JOIN → All routines from both (if DB supports, else use UNION of LEFT + RIGHT)

```sql
SELECT b.step AS boy_step, g.step AS girl_step
FROM boys_routine b
FULL OUTER JOIN girls_routine g
ON b.step = g.step;
```

If not supported (like in MySQL), do:

```sql
SELECT b.step, g.step
FROM boys_routine b
LEFT JOIN girls_routine g
ON b.step = g.step
UNION
SELECT b.step, g.step
FROM boys_routine b
RIGHT JOIN girls_routine g
ON b.step = g.step;
```

📌 Output:

* Face Wash | Face Wash
* Moisturizer | NULL
* Sunscreen | Sunscreen
* NULL | Toner
* NULL | Serum

---

✨ So in short:

* **INNER JOIN → only shared routines**
* **LEFT JOIN → all boys’ routines, girls if matching**
* **RIGHT JOIN → all girls’ routines, boys if matching**
* **FULL JOIN → everything from both**

---


---



### **Built-in methods**

* **GROUP BY** → Imagine a teacher sorting students by class. All 5th standard kids together, 6th standard together.
* **HAVING** → After grouping, you filter — e.g., “Show me only those classes with more than 10 students.”
* **DISTINCT** → When friends tell you their favorite fruit, some repeat “mango.” You just want the *unique list* of fruits.

---

### ** Database Setup**

```sql
-- Step 1: Create database
CREATE DATABASE employee_db;
USE employee_db;

-- Step 2: Create Employees table
CREATE TABLE Employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    age INT,
    salary INT
);

-- Step 3: Insert sample data
INSERT INTO Employees (emp_id, name, department, age, salary) VALUES
(1, 'Amit', 'HR', 25, 40000),
(2, 'Priya', 'HR', 28, 45000),
(3, 'Rahul', 'IT', 25, 50000),
(4, 'Sneha', 'IT', 30, 60000),
(5, 'Kiran', 'Finance', 28, 55000),
(6, 'Manoj', 'Finance', 28, 55000), -- duplicate salary for testing DISTINCT
(7, 'Anita', 'HR', 35, 70000);
```

---

### ** GROUP BY Demo**

1. **Count employees per department**

```sql
SELECT department, COUNT(*) AS total_employees
FROM Employees
GROUP BY department;
```

2. **Find average salary per department**

```sql
SELECT department, AVG(salary) AS avg_salary
FROM Employees
GROUP BY department;
```

👉 * *: Like calculating class-wise average marks.

---

### **HAVING Demo**

1. **Show departments with more than 2 employees**

```sql
SELECT department, COUNT(*) AS total_employees
FROM Employees
GROUP BY department
HAVING COUNT(*) > 2;
```

2. **Show departments where average salary is above 50,000**

```sql
SELECT department, AVG(salary) AS avg_salary
FROM Employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

👉 * *: First group by class, then filter only the classes with more than 10 students.

---

### **DISTINCT Demo**

1. **Show unique departments**

```sql
SELECT DISTINCT department FROM Employees;
```

2. **Show unique salaries**

```sql
SELECT DISTINCT salary FROM Employees;
```

👉 * *: Just like filtering duplicate fruits in a list, keeping only unique ones.

---

✅ **Wrap-Up Summary**

* **GROUP BY** → Categorize data.
* **HAVING** → Filter grouped data.
* **DISTINCT** → Remove duplicates.

---


---

# 🍴 Restaurant Normalisation Demo

## Step 0: The Messy Table (Unnormalised Data)

Imagine we store restaurant orders like this:

```sql
CREATE DATABASE restaurant_db;
USE restaurant_db;

CREATE TABLE messy_orders (
    order_id INT,
    customer_name VARCHAR(50),
    dishes VARCHAR(100),   -- multiple dishes in one cell
    dish_prices VARCHAR(100),
    waiter_name VARCHAR(50),
    waiter_phone VARCHAR(15)
);

INSERT INTO messy_orders VALUES
(1, 'Amit', 'Paneer Butter Masala, Naan', '200, 30', 'Ravi', '9876543210'),
(2, 'Sneha', 'Pizza, Coke', '300, 40', 'Ravi', '9876543210'),
(3, 'Rahul', 'Burger, Fries, Coke', '150, 80, 40', 'Meena', '9123456789');

SELECT * FROM messy_orders;
```

👉 Problems:

* Multiple dishes in one cell (violates **1NF**).
* Prices duplicated with dishes.
* Waiter details repeated again and again.

---

## Step 1: Apply **1NF (First Normal Form)**

**Rule:** Each cell should have only one value.

👉 Break dishes into separate rows:

```sql
CREATE TABLE orders_1nf (
    order_id INT,
    customer_name VARCHAR(50),
    dish_name VARCHAR(50),
    dish_price INT,
    waiter_name VARCHAR(50),
    waiter_phone VARCHAR(15)
);

INSERT INTO orders_1nf VALUES
(1, 'Amit', 'Paneer Butter Masala', 200, 'Ravi', '9876543210'),
(1, 'Amit', 'Naan', 30, 'Ravi', '9876543210'),
(2, 'Sneha', 'Pizza', 300, 'Ravi', '9876543210'),
(2, 'Sneha', 'Coke', 40, 'Ravi', '9876543210'),
(3, 'Rahul', 'Burger', 150, 'Meena', '9123456789'),
(3, 'Rahul', 'Fries', 80, 'Meena', '9123456789'),
(3, 'Rahul', 'Coke', 40, 'Meena', '9123456789');

SELECT * FROM orders_1nf;
```

✅ Now each cell has atomic (single) values.
❌ Still waiter details and dish prices repeat.

---

## Step 2: Apply **2NF (Second Normal Form)**

**Rule:** Remove partial dependency. Separate repeating groups.

👉 Split into **Orders**, **Order\_Details**, and **Dishes**:

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_name VARCHAR(50),
    waiter_name VARCHAR(50),
    waiter_phone VARCHAR(15)
);

CREATE TABLE dishes (
    dish_id INT PRIMARY KEY,
    dish_name VARCHAR(50),
    dish_price INT
);

CREATE TABLE order_details (
    order_id INT,
    dish_id INT,
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (dish_id) REFERENCES dishes(dish_id)
);

-- Insert data
INSERT INTO orders VALUES
(1, 'Amit', 'Ravi', '9876543210'),
(2, 'Sneha', 'Ravi', '9876543210'),
(3, 'Rahul', 'Meena', '9123456789');

INSERT INTO dishes VALUES
(101, 'Paneer Butter Masala', 200),
(102, 'Naan', 30),
(103, 'Pizza', 300),
(104, 'Coke', 40),
(105, 'Burger', 150),
(106, 'Fries', 80);

INSERT INTO order_details VALUES
(1, 101), (1, 102),
(2, 103), (2, 104),
(3, 105), (3, 106), (3, 104);

SELECT * FROM orders;
SELECT * FROM dishes;
SELECT * FROM order_details;
```

✅ Dish prices are now stored once in `dishes`.
❌ Still waiter’s phone number is repeated for every order he serves.

---

## Step 3: Apply **3NF (Third Normal Form)**

**Rule:** Remove transitive dependency (non-key depending on another non-key).

👉 Extract **Waiters** into a separate table:

```sql
CREATE TABLE waiters (
    waiter_id INT PRIMARY KEY,
    waiter_name VARCHAR(50),
    waiter_phone VARCHAR(15)
);

ALTER TABLE orders ADD waiter_id INT;
ALTER TABLE orders DROP COLUMN waiter_name, DROP COLUMN waiter_phone;

-- Insert waiters
INSERT INTO waiters VALUES
(1, 'Ravi', '9876543210'),
(2, 'Meena', '9123456789');

-- Update orders with waiter_id
UPDATE orders SET waiter_id = 1 WHERE order_id IN (1,2);
UPDATE orders SET waiter_id = 2 WHERE order_id = 3;

SELECT * FROM waiters;
SELECT * FROM orders;
```

✅ Now data is fully normalised:

* **orders** → customer info + waiter\_id
* **dishes** → dish name + price
* **order\_details** → which order has which dish
* **waiters** → waiter info stored once

---

# 🎯 Final Outcome for Freshers:

* **Unnormalised Data** = messy restaurant notebook with repeated entries.
* **1NF** = break combined values into single cells.
* **2NF** = move repeating groups into separate tables.
* **3NF** = remove indirect dependencies (waiter info separate).

---

---

# ✅ Advantages of Normalisation 

### 1. **Easy Updates (Avoids Repetition)**

👉 Suppose **waiter Ravi changes his phone number**.

* **Before Normalisation (messy/1NF table):**
  Ravi’s phone number is copied in **every order he served**.
  If he served 500 orders, you must update in **500 rows**.
  If you miss one, data is inconsistent.

* **After Normalisation (3NF, separate `waiters` table):**
  Ravi’s phone number is stored **only once** in the `waiters` table.
  Update in **one place → reflects everywhere**.

---

### 2. **No Redundant Data (Saves Space)**

👉 Suppose **Paneer Butter Masala price changes from ₹200 to ₹220**.

* **Before Normalisation:**
  Price ₹200 is repeated in every order. You’d have to edit in many rows.
  Lots of duplicate storage.

* **After Normalisation (separate `dishes` table):**
  Paneer Butter Masala price is stored **once** in the `dishes` table.
  Change in one place → every order automatically reflects the new price.

---

### 3. **Better Consistency (No Conflicts)**

👉 Suppose Coke is ₹40 in one row, ₹45 in another row (data entry mistake).
Which is correct? Nobody knows ❌

* **After Normalisation:**
  Coke has only **one price entry** in `dishes`. No confusion ✅

---

### 4. **Easy Deletion (No Accidental Data Loss)**

👉 Suppose you delete an order.

* In messy table, you might **accidentally delete waiter or dish info** also.
* In normalised tables, deleting from `orders` only affects that order; waiter and dishes stay safe.

---

### 5. **Better Search and Reporting**

👉 Want to find **all orders served by Meena**?

* Messy table → You have to filter through repeating names and phones.
* Normalised table → Just filter by `waiter_id = 2`, and join with `orders`. Easy and fast.

---

# 🎯 Simple Analogy 
* **Unnormalised:** Like writing *everything about every order in a diary* → repeated info, messy.
* **Normalised:** Like keeping **one Menu card, one Waiter list, and one Orders log** → update once, use everywhere.

👉 So whenever **a waiter changes number, a dish price changes, or new waiter joins**, you only update **one place** instead of hundreds of rows.

---
