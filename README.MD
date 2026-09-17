# Student Attendance Management System

## Project Overview

The **Student Attendance Management System** is a Java-based desktop
application developed to provide a simple computerized solution for
managing student attendance.

The application uses **Java Swing** for the graphical user interface and
**MySQL** for persistent data storage. It provides separate modules for
student management, attendance recording, and attendance reporting.

## Project Details

  Particular            Details
  --------------------- --------------------------------------
  Project Title         Student Attendance Management System
  Name                  Vanshaj Saxena
  Registration Number   25BAI11239
  Course                Programming in Java
  Faculty               S. Muthusundari
  University            VIT Bhopal University

## Features

### 1. Student Management

-   Add student information.
-   Store student name, registration number, and email.
-   Validate required fields.
-   Display a confirmation message after successful insertion.

### 2. Mark Attendance

-   Enter Student ID and Subject ID.
-   Enter the attendance date.
-   Mark the student as Present or Absent.
-   Store attendance records in MySQL.
-   Display a success or failure message.

### 3. Attendance Report

-   Enter Student ID and Subject ID.
-   Retrieve attendance records from the database.
-   Calculate total classes.
-   Calculate classes attended.
-   Calculate attendance percentage.
-   Display an attendance warning when the percentage is below 75%.

## Technologies Used

-   **Java**
-   **Java Swing** -- Graphical User Interface
-   **JDBC** -- Java-MySQL connectivity
-   **MySQL** -- Database
-   **SQL** -- Database operations
-   **IntelliJ IDEA** -- Development environment
-   **MySQL Connector/J** -- JDBC driver

## Project Structure

``` text
StudentAttendanceSystem/
└── src/
    ├── Main.java
    ├── model/
    │   ├── Student.java
    │   ├── Subject.java
    │   └── Attendance.java
    ├── database/
    │   ├── DatabaseConnection.java
    │   ├── StudentDAO.java
    │   ├── SubjectDAO.java
    │   └── AttendanceDAO.java
    ├── service/
    │   └── ReportService.java
    └── gui/
        ├── AttendanceFrame.java
        ├── StudentManagementFrame.java
        ├── MarkAttendanceFrame.java
        └── AttendanceReportFrame.java
```

## Architecture

The project follows a layered structure:

``` text
User
  |
  v
Java Swing GUI
  |
  v
Report Service
  |
  v
DAO Layer
  |
  v
JDBC / MySQL
  |
  v
MySQL Database
```

### Main Layers

-   **Model Layer:** Represents Student, Subject, and Attendance
    objects.
-   **GUI Layer:** Provides the graphical interface and handles user
    interaction.
-   **Service Layer:** Generates attendance reports and performs
    attendance calculations.
-   **DAO Layer:** Handles database operations for students, subjects,
    and attendance.
-   **Database Connection Layer:** Establishes the JDBC connection with
    MySQL.
-   **Database Layer:** Stores student, subject, and attendance records.

## Database

The project uses a MySQL database named:

``` text
student_attendance
```

It contains three tables:

### students

``` text
id
name
registration_no
email
```

### subjects

``` text
id
name
```

### attendance

``` text
id
student_id
subject_id
date
present
```

The attendance table uses foreign keys to connect attendance records
with students and subjects.

## Attendance Calculation

The attendance percentage is calculated using:

``` text
Attendance Percentage =
(Classes Attended / Total Classes) × 100
```

If the calculated attendance is below **75%**, the application displays
a warning.

## Input Validation and Error Handling

The application performs basic validation, including:

-   Checking required fields.
-   Checking that Student ID and Subject ID are numeric.
-   Checking that Present or Absent is selected.
-   Handling database operation errors.
-   Using foreign-key constraints to maintain valid student and subject
    relationships.

## How to Run

### Prerequisites

Install the following:

1.  Java JDK
2.  MySQL Server
3.  IntelliJ IDEA or another Java IDE
4.  MySQL Connector/J JDBC driver

### Database Setup

Create the database:

``` sql
CREATE DATABASE student_attendance;
USE student_attendance;
```

Create the required tables:

``` sql
CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    registration_no VARCHAR(30) NOT NULL UNIQUE,
    email VARCHAR(100)
);
```

``` sql
CREATE TABLE subjects (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL
);
```

``` sql
CREATE TABLE attendance (
    id INT PRIMARY KEY AUTO_INCREMENT,
    student_id INT NOT NULL,
    subject_id INT NOT NULL,
    date DATE NOT NULL,
    present BOOLEAN NOT NULL,
    FOREIGN KEY (student_id) REFERENCES students(id),
    FOREIGN KEY (subject_id) REFERENCES subjects(id)
);
```

### Configure Database Connection

Open:

``` text
src/database/DatabaseConnection.java
```

Set the MySQL username and password according to your local MySQL
installation.

The default database connection uses:

``` text
Database: student_attendance
Host: localhost
Port: 3306
User: root
```

### Run the Application

Run:

``` text
src/Main.java
```

The main dashboard opens with:

-   Student Management
-   Mark Attendance
-   Attendance Report
-   Exit

## Example Workflow

1.  Launch the application.
2.  Open **Student Management**.
3.  Enter student details and add the student.
4.  Add a subject to the database if required.
5.  Open **Mark Attendance**.
6.  Enter the valid Student ID and Subject ID.
7.  Enter the date and select Present or Absent.
8.  Save the attendance record.
9.  Open **Attendance Report**.
10. Enter Student ID and Subject ID.
11. Generate the report to view total classes, attended classes,
    attendance percentage, and attendance status.

## OOP Concepts Demonstrated

The project demonstrates practical Java concepts including:

-   Classes and objects
-   Encapsulation
-   Constructors
-   Methods
-   Packages
-   Exception handling
-   Event handling
-   Modular programming
-   JDBC database connectivity

The model classes use private attributes and getter methods to
demonstrate encapsulation.

## Future Enhancements

The system can be extended with:

-   Update and delete student records.
-   Display all students using `JTable`.
-   Dedicated subject-management interface.
-   Subject-wise attendance summaries.
-   Calculation of classes required to reach 75% attendance.
-   Export attendance reports to PDF or Excel.
-   User authentication and role-based access.
-   Graphical attendance charts.
-   Improved visual design of the Swing interface.

## Author

**Vanshaj Saxena**\
Registration Number: **25BAI11239**\
VIT Bhopal University

## References

1.  Oracle Java Documentation
2.  Oracle Java Swing Documentation
3.  MySQL Documentation
4.  MySQL Connector/J Documentation
5.  IntelliJ IDEA Documentation
6.  VIT Bhopal University Programming in Java course/project guidelines
7.  VITyarthi Build Your Own Project guidelines
