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

👉 *Layman*: Like calculating class-wise average marks.

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

👉 *Layman*: First group by class, then filter only the classes with more than 10 students.

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

👉 *Layman*: Just like filtering duplicate fruits in a list, keeping only unique ones.

---

✅ **Wrap-Up Summary**

* **GROUP BY** → Categorize data.
* **HAVING** → Filter grouped data.
* **DISTINCT** → Remove duplicates.

---


