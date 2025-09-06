
---

# 📘 MySQL Advanced Concepts 

---

## 1️⃣ MySQL Subqueries

### 🧠 What is a Subquery?

* A **query inside another query**.
* Think of it as asking one question **inside** another.

👉 Example in real life:
“Who earns more than the **average salary**?”

* First find the **average salary** (inner query).
* Then compare each employee’s salary (outer query).

### 🔑 Syntax

```sql
SELECT column
FROM table
WHERE column OPERATOR (
    SELECT column FROM table WHERE condition
);
```

### 🏦 Demo Setup

```sql
CREATE DATABASE CompanyDB;
USE CompanyDB;

CREATE TABLE Employees (
    emp_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10, 2)
);

INSERT INTO Employees (name, department, salary) VALUES
('Alice', 'HR', 50000),
('Bob', 'IT', 70000),
('Charlie', 'Finance', 65000),
('David', 'IT', 55000),
('Eva', 'HR', 48000);
```

### ⚡ Examples

* Find employees earning more than average:

```sql
SELECT name, salary
FROM Employees
WHERE salary > (SELECT AVG(salary) FROM Employees);
```

* Find employees working in departments where someone earns above 60,000:

```sql
SELECT name, department
FROM Employees
WHERE department IN (
    SELECT department
    FROM Employees
    WHERE salary > 60000
);
```

---

## 2️⃣ MySQL Stored Procedures

### 🧠 What is a Stored Procedure?

* A **named block of SQL** that can be executed repeatedly.
* Like a **function in programming**.

👉 Example in real life:
Instead of writing the same recipe every time, you keep it in a **cookbook** → just call the recipe name when needed.

### 🔑 Syntax

```sql
DELIMITER //
CREATE PROCEDURE procedure_name()
BEGIN
   SQL statements;
END //
DELIMITER ;
```

### 🏦 Demo Setup

```sql
CREATE TABLE Departments (
    dept_id INT AUTO_INCREMENT PRIMARY KEY,
    dept_name VARCHAR(50)
);

INSERT INTO Departments (dept_name) VALUES
('HR'), ('IT'), ('Finance');
```

### ⚡ Examples

* Procedure to list all employees:

```sql
DELIMITER //
CREATE PROCEDURE GetAllEmployees()
BEGIN
    SELECT * FROM Employees;
END //
DELIMITER ;

CALL GetAllEmployees();
```

* Procedure with parameter:

```sql
DELIMITER //
CREATE PROCEDURE GetEmployeesByDept(IN dept VARCHAR(50))
BEGIN
    SELECT * FROM Employees WHERE department = dept;
END //
DELIMITER ;

CALL GetEmployeesByDept('IT');
```

---

## 3️⃣ MySQL Transactions

### 🧠 What is a Transaction?

* A group of SQL operations treated as **one single unit**.
* **All or nothing**:

  * If all succeed → `COMMIT`
  * If one fails → `ROLLBACK`

👉 Example: Bank transfer (deduct from A, add to B).

### 🔑 Syntax

```sql
START TRANSACTION;
-- SQL statements
COMMIT;   -- save changes
-- or
ROLLBACK; -- cancel changes
```

### 🏦 Demo Setup

```sql
CREATE TABLE BankAccounts (
    acc_id INT PRIMARY KEY,
    name VARCHAR(50),
    balance DECIMAL(10, 2)
);

INSERT INTO BankAccounts VALUES
(1, 'John', 1000),
(2, 'Mike', 500);
```

### ⚡ Example: Transfer ₹200 from John to Mike

```sql
START TRANSACTION;

UPDATE BankAccounts SET balance = balance - 200 WHERE acc_id = 1;
UPDATE BankAccounts SET balance = balance + 200 WHERE acc_id = 2;

COMMIT;
-- or ROLLBACK;
```

---

## 4️⃣ MySQL Views

### 🧠 What is a View?

* A **virtual table** created from a query.
* It does not store data, only the **SQL query**.
* Useful for **simplifying complex queries** and **restricting access**.

👉 Example: Instead of writing a long join every time, create a view and query it directly.

### 🔑 Syntax

```sql
CREATE VIEW view_name AS
SELECT columns FROM tables WHERE condition;
```

### 🏦 Demo Setup

```sql
-- Reuse Employees table
```

### ⚡ Examples

* Create a view for high-salary employees:

```sql
CREATE VIEW HighSalaryEmployees AS
SELECT name, department, salary
FROM Employees
WHERE salary > 60000;
```

* Query the view:

```sql
SELECT * FROM HighSalaryEmployees;
```

* Drop a view:

```sql
DROP VIEW HighSalaryEmployees;
```

---

# ✅ Summary

* **Subqueries** → query inside another query (like nested questions).
* **Stored Procedures** → reusable SQL blocks (like functions).
* **Transactions** → all-or-nothing deals (commit or rollback).
* **Views** → virtual tables for simplified access.

---

