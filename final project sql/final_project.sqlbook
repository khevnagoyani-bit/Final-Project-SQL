-- SQLBook: Code
DROP DATABASE IF EXISTS university_db;
CREATE DATABASE university_db;
USE university_db;
-- SQLBook: Markup
## Students Table
-- SQLBook: Code
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    BirthDate DATE,
    EnrollmentDate DATE
);

INSERT INTO Students VALUES
(1, 'Aarav', 'Patel', 'aarav@gmail.com', '2002-05-10', '2021-06-15'),
(2, 'Diya', 'Shah', 'diya@gmail.com', '2003-03-20', '2022-07-10'),
(3, 'Rohan', 'Mehta', 'rohan@gmail.com', '2002-08-12', '2023-06-20'),
(4, 'Kavya', 'Desai', 'kavya@gmail.com', '2003-11-05', '2024-07-15'),
(5, 'Arjun', 'Joshi', 'arjun@gmail.com', '2001-01-25', '2020-06-10'),
(6, 'Neha', 'Trivedi', 'neha@gmail.com', '2002-09-18', '2021-07-12'),
(7, 'Vivaan', 'Sharma', 'vivaan@gmail.com', '2003-02-14', '2025-06-18'),
(8, 'Ananya', 'Patel', 'ananya@gmail.com', '2004-04-22', '2025-07-20'),
(9, 'Dhruv', 'Gandhi', 'dhruv@gmail.com', '2002-12-30', '2023-08-01'),
(10, 'Pooja', 'Rana', 'pooja@gmail.com', '2003-06-16', '2024-06-25');
-- SQLBook: Markup
## Courses Table
-- SQLBook: Code
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(100),
    DepartmentID INT,
    Credits INT
);

INSERT INTO Courses VALUES
(101, 'Introduction to SQL', 1, 4),
(102, 'Data Structures', 2, 3),
(103, 'Python Programming', 1, 4),
(104, 'Calculus', 2, 3),
(105, 'Database Management', 1, 4),
(106, 'Statistics', 2, 3),
(107, 'Physics Basics', 3, 4),
(108, 'Web Development', 3, 3),
(109, 'Linear Algebra', 2, 4),
(110, 'Data Analytics', 1, 4);
-- SQLBook: Markup
## Instructors Table
-- SQLBook: Code
CREATE TABLE Instructors (
    InstructorID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    DepartmentID INT
);

INSERT INTO Instructors VALUES
(1, 'Amit', 'Sharma', 'amit@gmail.com', 1),
(2, 'Priya', 'Patel', 'priya@gmail.com', 2),
(3, 'Rahul', 'Mehta', 'rahul@gmail.com', 1),
(4, 'Sneha', 'Shah', 'sneha@gmail.com', 3),
(5, 'Vikram', 'Joshi', 'vikram@gmail.com', 2),
(6, 'Nisha', 'Desai', 'nisha@gmail.com', 3),
(7, 'Karan', 'Gandhi', 'karan@gmail.com', 1),
(8, 'Meera', 'Trivedi', 'meera@gmail.com', 2),
(9, 'Raj', 'Rana', 'raj@gmail.com', 1),
(10, 'Isha', 'Patel', 'isha@gmail.com', 3);
-- SQLBook: Markup
## Enrollments Table
-- SQLBook: Code
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE
);

INSERT INTO Enrollments VALUES
(1, 1, 101, '2021-06-15'),
(2, 2, 102, '2022-07-10'),
(3, 3, 101, '2023-06-20'),
(4, 4, 103, '2024-07-15'),
(5, 5, 104, '2020-06-10'),
(6, 6, 105, '2021-07-12'),
(7, 7, 101, '2025-06-18'),
(8, 8, 108, '2025-07-20'),
(9, 9, 102, '2023-08-01'),
(10, 10, 110, '2024-06-25');
-- SQLBook: Markup
## Departments Table
-- SQLBook: Code
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);

INSERT INTO Departments VALUES
(1, 'Computer Science'),
(2, 'Mathematics'),
(3, 'Information Technology'),
(4, 'Physics'),
(5, 'Chemistry'),
(6, 'Commerce'),
(7, 'English'),
(8, 'Statistics'),
(9, 'Business Administration'),
(10, 'Data Science');
-- SQLBook: Code
SELECT * FROM Students;

SELECT * FROM Courses;

SELECT * FROM Instructors;

SELECT * FROM Enrollments;

SELECT * FROM Departments;
-- SQLBook: Markup
### CRUD Operations on All Tables
-- SQLBook: Code

INSERT INTO Students
VALUES (11, 'Yash', 'Patel', 'yash@gmail.com', '2003-10-15', '2025-08-01');

SELECT * FROM Students;

UPDATE Students
SET Email = 'yashpatel@gmail.com'
WHERE StudentID = 11;

DELETE FROM Students
WHERE StudentID = 11;

INSERT INTO Courses
VALUES (111, 'Machine Learning', 1, 4);

SELECT * FROM Courses;

UPDATE Courses
SET Credits = 3
WHERE CourseID = 111;

DELETE FROM Courses
WHERE CourseID = 111;

INSERT INTO Instructors
VALUES (11, 'Harsh', 'Shah', 'harsh@gmail.com', 1, 70000);

SELECT * FROM Instructors;

UPDATE Instructors
SET Email = 'harshshah@gmail.com'
WHERE InstructorID = 11;

DELETE FROM Instructors
WHERE InstructorID = 11;

INSERT INTO Enrollments
VALUES (11, 1, 101, '2025-08-01');

SELECT * FROM Enrollments;

UPDATE Enrollments
SET CourseID = 103
WHERE EnrollmentID = 11;

DELETE FROM Enrollments
WHERE EnrollmentID = 11;

INSERT INTO Departments
VALUES (11, 'Artificial Intelligence');

SELECT * FROM Departments;

UPDATE Departments
SET DepartmentName = 'Artificial Intelligence and ML'

DELETE FROM Departments
WHERE DepartmentID = 11;
-- SQLBook: Markup
### Students enrolled after 2022
-- SQLBook: Code
SELECT *
FROM Students
WHERE EnrollmentDate > '2022-12-31';
-- SQLBook: Markup
### Mathematics courses with LIMIT 5
-- SQLBook: Code
SELECT c.CourseID,
       c.CourseName,
       c.Credits
FROM Courses c
JOIN Departments d
ON c.DepartmentID = d.DepartmentID
WHERE d.DepartmentName = 'Mathematics'
LIMIT 5;
-- SQLBook: Markup
### Number of students in each course, more than 5
-- SQLBook: Code
USE university_db;
SELECT c.CourseName,
       COUNT(e.StudentID) AS TotalStudents
FROM Courses c
JOIN Enrollments e
ON c.CourseID = e.CourseID
GROUP BY c.CourseID, c.CourseName
HAVING COUNT(e.StudentID) > 5;
-- SQLBook: Markup
### Students enrolled in BOTH SQL and Data Structures
-- SQLBook: Code
USE university_db;
SELECT s.StudentID,
       s.FirstName,
       s.LastName
FROM Students s
JOIN Enrollments e
ON s.StudentID = e.StudentID
JOIN Courses c
ON e.CourseID = c.CourseID
WHERE c.CourseName IN ('Introduction to SQL', 'Data Structures')
GROUP BY s.StudentID, s.FirstName, s.LastName
HAVING COUNT(DISTINCT c.CourseName) = 2;
-- SQLBook: Markup
### Students enrolled in SQL OR Data Structures
-- SQLBook: Code
SELECT DISTINCT
       s.StudentID,
       s.FirstName,
       s.LastName
FROM Students s
JOIN Enrollments e
ON s.StudentID = e.StudentID
JOIN Courses c
ON e.CourseID = c.CourseID
WHERE c.CourseName IN ('Introduction to SQL', 'Data Structures');
-- SQLBook: Markup
### Average credits of all courses
-- SQLBook: Code
SELECT AVG(Credits) AS AverageCredits
FROM Courses;
-- SQLBook: Markup
### Maximum salary in Computer Science
-- SQLBook: Code
ALTER TABLE Instructors
ADD Salary DECIMAL(10,2);

UPDATE Instructors SET Salary = 70000 WHERE InstructorID = 1;
UPDATE Instructors SET Salary = 65000 WHERE InstructorID = 2;
UPDATE Instructors SET Salary = 75000 WHERE InstructorID = 3;
UPDATE Instructors SET Salary = 60000 WHERE InstructorID = 4;
UPDATE Instructors SET Salary = 68000 WHERE InstructorID = 5;
UPDATE Instructors SET Salary = 72000 WHERE InstructorID = 6;
UPDATE Instructors SET Salary = 80000 WHERE InstructorID = 7;
UPDATE Instructors SET Salary = 71000 WHERE InstructorID = 8;
UPDATE Instructors SET Salary = 85000 WHERE InstructorID = 9;
UPDATE Instructors SET Salary = 62000 WHERE InstructorID = 10;
SELECT MAX(i.Salary) AS MaximumSalary
FROM Instructors i
JOIN Departments d
ON i.DepartmentID = d.DepartmentID
WHERE d.DepartmentName = 'Computer Science';

-- SQLBook: Markup
### Number of students in each department
-- SQLBook: Code
SELECT d.DepartmentName,
       COUNT(DISTINCT e.StudentID) AS TotalStudents
FROM Departments d
JOIN Courses c
ON d.DepartmentID = c.DepartmentID
JOIN Enrollments e
ON c.CourseID = e.CourseID
GROUP BY d.DepartmentID, d.DepartmentName;
-- SQLBook: Markup
### INNER JOIN — Students and Courses
-- SQLBook: Code
SELECT s.StudentID,
       CONCAT(s.FirstName, ' ', s.LastName) AS StudentName,
       c.CourseName
FROM Students s
INNER JOIN Enrollments e
ON s.StudentID = e.StudentID
INNER JOIN Courses c
ON e.CourseID = c.CourseID;
-- SQLBook: Markup
### LEFT JOIN — All students and courses

-- SQLBook: Code
SELECT s.StudentID,
       CONCAT(s.FirstName, ' ', s.LastName) AS StudentName,
       c.CourseName
FROM Students s
LEFT JOIN Enrollments e
ON s.StudentID = e.StudentID
LEFT JOIN Courses c
ON e.CourseID = c.CourseID;
-- SQLBook: Markup
### Subquery — Courses having more than 10 students
-- SQLBook: Code
SELECT DISTINCT
       s.StudentID,
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
-- SQLBook: Markup
### Extract year from EnrollmentDate
-- SQLBook: Code
SELECT StudentID,
       FirstName,
       LastName,
       EnrollmentDate,
       YEAR(EnrollmentDate) AS EnrollmentYear
FROM Students;
-- SQLBook: Markup
### Concatenate instructor first and last name
-- SQLBook: Code
SELECT InstructorID,
       CONCAT(FirstName, ' ', LastName) AS InstructorName
FROM Instructors;
-- SQLBook: Markup
### Running total of students enrolled in courses
-- SQLBook: Code
SELECT CourseID,
       COUNT(StudentID) AS StudentCount,
       SUM(COUNT(StudentID)) OVER (
           ORDER BY CourseID
       ) AS RunningTotal
FROM Enrollments
GROUP BY CourseID;
-- SQLBook: Markup
### Senior / Junior using CASE
-- SQLBook: Code
SELECT StudentID,
       FirstName,
       LastName,
       EnrollmentDate,
       CASE
           WHEN TIMESTAMPDIFF(YEAR, EnrollmentDate, CURDATE()) > 4
           THEN 'Senior'
           ELSE 'Junior'
       END AS StudentLevel
FROM Students;