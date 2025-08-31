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



