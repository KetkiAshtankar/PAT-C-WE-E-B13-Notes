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

