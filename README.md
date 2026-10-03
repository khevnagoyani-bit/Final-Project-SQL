# Final-Project-SQL

  <strong>📚 SQL Final Project</strong><br>
  A complete database system for managing students, courses, instructors, enrollments, and departments.

---

## 🌟 Project Overview

The **University Course Management System** is a SQL-based database project designed to manage university academic information efficiently.

This project demonstrates practical implementation of important **MySQL and SQL concepts**, including:

* 🗃️ Database & Table Creation
* ➕ INSERT Operations
* 🔍 SELECT Queries
* ✏️ UPDATE Operations
* 🗑️ DELETE Operations
* 🔗 INNER JOIN
* 🔗 LEFT JOIN
* 🧩 Subqueries
* 📊 Aggregate Functions
* 🏷️ GROUP BY & HAVING
* 📅 Date Functions
* 🔤 String Functions
* 🪟 Window Functions
* 🔀 CASE Expression
* 🎯 Filtering & Sorting

---

## 🎯 Project Objective

The main objective of this project is to create a functional **University Course Management Database** and apply different SQL operations to retrieve, manipulate, and analyze academic data.

The system manages relationships between:

```text
👨‍🎓 Students
      │
      ▼
📝 Enrollments
      │
      ▼
📚 Courses
      │
      ▼
🏢 Departments

👨‍🏫 Instructors
      │
      ▼
🏢 Departments
```

---

## 🗂️ Database Structure

**Database Name:**

```text
university_db
```

### 📌 Tables

| #   | Table         | Purpose                                  |
| --- | ------------- | ---------------------------------------- |
| 1️⃣ | `Students`    | Stores student information               |
| 2️⃣ | `Courses`     | Stores available courses                 |
| 3️⃣ | `Instructors` | Stores instructor information            |
| 4️⃣ | `Enrollments` | Stores student-course enrollment records |
| 5️⃣ | `Departments` | Stores university departments            |

---

## 👨‍🎓 1. Students Table

Stores information about university students.

| Column           | Data Type | Description                |
| ---------------- | --------- | -------------------------- |
| `StudentID`      | INT       | Primary Key                |
| `FirstName`      | VARCHAR   | Student first name         |
| `LastName`       | VARCHAR   | Student last name          |
| `Email`          | VARCHAR   | Student email              |
| `BirthDate`      | DATE      | Date of birth              |
| `EnrollmentDate` | DATE      | University enrollment date |

---

## 📚 2. Courses Table

Stores information about university courses.

| Column         | Data Type | Description          |
| -------------- | --------- | -------------------- |
| `CourseID`     | INT       | Primary Key          |
| `CourseName`   | VARCHAR   | Name of course       |
| `DepartmentID` | INT       | Department reference |
| `Credits`      | INT       | Course credits       |

---

## 👨‍🏫 3. Instructors Table

Stores information about instructors.

| Column         | Data Type | Description           |
| -------------- | --------- | --------------------- |
| `InstructorID` | INT       | Primary Key           |
| `FirstName`    | VARCHAR   | Instructor first name |
| `LastName`     | VARCHAR   | Instructor last name  |
| `Email`        | VARCHAR   | Instructor email      |
| `DepartmentID` | INT       | Department reference  |
| `Salary`       | DECIMAL   | Instructor salary     |

---

## 📝 4. Enrollments Table

Connects students with courses.

| Column           | Data Type | Description       |
| ---------------- | --------- | ----------------- |
| `EnrollmentID`   | INT       | Primary Key       |
| `StudentID`      | INT       | Student reference |
| `CourseID`       | INT       | Course reference  |
| `EnrollmentDate` | DATE      | Enrollment date   |

---

## 🏢 5. Departments Table

Stores university department information.

| Column           | Data Type | Description     |
| ---------------- | --------- | --------------- |
| `DepartmentID`   | INT       | Primary Key     |
| `DepartmentName` | VARCHAR   | Department name |

---

# 🔗 Relationships

The database uses **Primary Keys and Foreign Keys** to maintain relationships.

```text
Departments
     │
     ├──────────────► Courses
     │
     └──────────────► Instructors

Students
     │
     ▼
Enrollments
     │
     ▼
Courses
```

### 🔑 Primary Keys

```text
Students      → StudentID
Courses       → CourseID
Instructors   → InstructorID
Enrollments   → EnrollmentID
Departments   → DepartmentID
```

### 🔗 Foreign Keys

```text
Courses.DepartmentID
        ↓
Departments.DepartmentID

Instructors.DepartmentID
        ↓
Departments.DepartmentID

Enrollments.StudentID
        ↓
Students.StudentID

Enrollments.CourseID
        ↓
Courses.CourseID
```

---

# 🛠️ SQL Concepts Used

## 1️⃣ CRUD Operations

CRUD stands for:

| Operation | SQL      |
| --------- | -------- |
| 🟢 Create | `INSERT` |
| 🔵 Read   | `SELECT` |
| 🟡 Update | `UPDATE` |
| 🔴 Delete | `DELETE` |

---

## 2️⃣ Filtering

The project uses `WHERE` to filter records.

```sql
SELECT *
FROM Students
WHERE EnrollmentDate > '2022-12-31';
```

---

## 3️⃣ LIMIT

Used to restrict the number of returned records.

```sql
SELECT *
FROM Courses
LIMIT 5;
```

---

## 4️⃣ Aggregate Functions

The project uses:

```text
COUNT()
AVG()
MAX()
SUM()
```

Example:

```sql
SELECT AVG(Credits) AS AverageCredits
FROM Courses;
```

---

## 5️⃣ GROUP BY

Used to group similar records.

```sql
SELECT CourseID,
       COUNT(StudentID) AS TotalStudents
FROM Enrollments
GROUP BY CourseID;
```

---

## 6️⃣ HAVING

Used to filter grouped results.

```sql
SELECT CourseID,
       COUNT(StudentID) AS TotalStudents
FROM Enrollments
GROUP BY CourseID
HAVING COUNT(StudentID) > 5;
```

---

## 7️⃣ INNER JOIN

Retrieves matching records from related tables.

```sql
SELECT s.FirstName,
       s.LastName,
       c.CourseName
FROM Students s
INNER JOIN Enrollments e
ON s.StudentID = e.StudentID
INNER JOIN Courses c
ON e.CourseID = c.CourseID;
```

---

## 8️⃣ LEFT JOIN

Retrieves all students and their courses if available.

```sql
SELECT s.StudentID,
       s.FirstName,
       c.CourseName
FROM Students s
LEFT JOIN Enrollments e
ON s.StudentID = e.StudentID
LEFT JOIN Courses c
ON e.CourseID = c.CourseID;
```

---

## 9️⃣ Subquery

Used to find students enrolled in courses having more than 10 students.

```sql
SELECT DISTINCT s.StudentID,
       s.FirstName,
       s.LastName
FROM Students s
JOIN Enrollments e
ON s.StudentID = e.StudentID
WHERE e.CourseID IN
(
    SELECT CourseID
    FROM Enrollments
    GROUP BY CourseID
    HAVING COUNT(StudentID) > 10
);
```

---

## 🔤 String Function

Instructor names are combined using `CONCAT()`.

```sql
SELECT CONCAT(FirstName, ' ', LastName)
AS InstructorName
FROM Instructors;
```

---

## 📅 Date Function

Extract the enrollment year:

```sql
SELECT StudentID,
       YEAR(EnrollmentDate) AS EnrollmentYear
FROM Students;
```

---

## 🪟 Window Function

The project uses a running total:

```sql
SELECT CourseID,
       COUNT(StudentID) AS StudentCount,
       SUM(COUNT(StudentID)) OVER (
           ORDER BY CourseID
       ) AS RunningTotal
FROM Enrollments
GROUP BY CourseID;
```

---

## 🔀 CASE Expression

Students are classified as **Senior** or **Junior**.

```sql
SELECT StudentID,
       FirstName,
       EnrollmentDate,
       CASE
           WHEN TIMESTAMPDIFF(
               YEAR,
               EnrollmentDate,
               CURDATE()
           ) > 4
           THEN 'Senior'
           ELSE 'Junior'
       END AS StudentLevel
FROM Students;
```

---

# 📋 Project Queries

The project includes queries for:

```text
01. CRUD Operations
02. Students enrolled after 2022
03. Mathematics courses with LIMIT 5
04. Course enrollment count
05. Students in both SQL and Data Structures
06. Students in SQL OR Data Structures
07. Average course credits
08. Maximum Computer Science instructor salary
09. Students per department
10. INNER JOIN
11. LEFT JOIN
12. Subquery
13. Extract enrollment year
14. Concatenate instructor name
15. Running total
16. Senior / Junior classification
```

---

# 💻 Technologies Used

| Technology                  | Purpose             |
| --------------------------- | ------------------- |
| 🐬 **MySQL**                | Database Management |
| 🧾 **SQL**                  | Query Language      |
| 🖥️ **MySQL Workbench**     | SQL Development     |
| 🗄️ **Relational Database** | Data Management     |

---

# 🚀 How to Run

### Step 1️⃣

Open **MySQL Workbench**.

### Step 2️⃣

Create or select the database:

```sql
CREATE DATABASE university_db;
USE university_db;
```

### Step 3️⃣

Create the five tables.

### Step 4️⃣

Insert the sample data.

### Step 5️⃣

Run the required SQL queries.

### Step 6️⃣

Check the results using:

```sql
SHOW TABLES;
```

and:

```sql
SELECT * FROM Students;
SELECT * FROM Courses;
SELECT * FROM Instructors;
SELECT * FROM Enrollments;
SELECT * FROM Departments;
```

---

# 📊 Sample Departments

```text
1  → Computer Science
2  → Mathematics
3  → Information Technology
4  → Physics
5  → Chemistry
6  → Commerce
7  → English
8  → Statistics
9  → Business Administration
10 → Data Science
```

---

# 🎓 Learning Outcomes

After completing this project, the learner can:

* Understand relational database design
* Create and manage multiple tables
* Work with Primary and Foreign Keys
* Perform CRUD operations
* Use different types of JOINs
* Write aggregate queries
* Use `GROUP BY` and `HAVING`
* Work with subqueries
* Manipulate strings and dates
* Use SQL `CASE`
* Apply window functions
* Analyze relational data using SQL

---

# 🏁 Conclusion

The **University Course Management System** provides practical experience in designing and querying a relational database.

It combines basic and advanced SQL concepts into one complete project, making it useful for **SQL practical exams, viva preparation, database learning, and final project demonstrations**.

---


### 💙 Built with SQL & MySQL

**University Course Management System**

📚 Learn • 🗃️ Manage • 🔍 Query • 📊 Analyze

