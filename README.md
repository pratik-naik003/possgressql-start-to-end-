
# 📘 PostgreSQL – Notes (Part 1)

## 1. Course Introduction

PostgreSQL is one of the most advanced open-source relational databases.

Learning PostgreSQL in 2024–25 gives a strong foundation because of:

* Advanced features
* High performance
* Use in real-world applications

Course covers basic → advanced concepts with simple examples.

### Topics Covered in Course

* SQL basic terms
* PostgreSQL setup
* CRUD operations
* Primary key & foreign key
* Data types
* Aggregate functions & operators
* Relationships & joins

### Advanced Topics

* Stored procedures
* Functions
* Views
* Triggers
* CTE
* Window functions

---

## 2. What is a Database?

**Definition:**
Database is an organized collection of data with methods to access and manipulate it.

### Example:

Think of a library:

* If books are arranged subject-wise → easy to find
* If unorganized → very difficult

### Sample Table Format

| First Name | Last Name | City   | Contact |
| ---------- | --------- | ------ | ------- |
| Raju       | Kumar     | Ranchi | 98765   |

Data is stored in rows & columns and is easy to search and manage.

### Why Not Use Excel Instead?

Excel works for small data, but for millions of records:

* Slow
* Not efficient
* Hard to manage

➡ Databases solve this problem.

---

## 3. Database vs DBMS

* **Database** → only data storage
* **DBMS** → tool to manage that data

### Real Example:

Website → DBMS → Database

* App sends data
* DBMS processes
* Stores in database

### Examples of DBMS

* PostgreSQL
* MySQL
* Oracle
* MongoDB

---

## 4. RDBMS

RDBMS = Relational DBMS

* Data stored in tables (rows + columns)
* Uses SQL to manage data

If data is in tabular form → it is RDBMS

### Examples

* PostgreSQL
* MySQL
* Oracle

---

## 5. SQL vs PostgreSQL

* **SQL** → Language
* **PostgreSQL** → Tool/Database that uses SQL

### Example SQL command:

```sql
SELECT * FROM table_name;
```

---

## 6. Installation Overview (Windows)

* Download PostgreSQL from official site
* Install with default options
* Set password (example: root)

### Default Details

* Port: 5432
* Default user: postgres

---

## 7. Tools Provided

### 1. pgAdmin

* GUI tool
* Write queries easily
* View tables visually

### 2. psql (Command Line)

To list databases:

```
\l
```

Clear screen:

```
\! cls
```

Create database:

```sql
CREATE DATABASE test;
```

---

## 8. Connect to Database

Switch database:

```
\c test
```

---

## 9. Database → Schema → Table

Hierarchy:

* Server
* Database
* Schema
* Tables

### Example:

Instagram Database

* Schema: user_data
* Tables:

  * users
  * posts
  * reels

---

## 10. CRUD Operations

CRUD =

* Create
* Read
* Update
* Delete

---

## 11. Creating Table

### Example Table

| id | name | city |

### Query

```sql
CREATE TABLE person (
    id INT,
    name VARCHAR(100),
    city VARCHAR(100)
);
```

Verify:

```
\d person
```

---

## 12. Insert Data

### Single Insert

```sql
INSERT INTO person (id, name, city)
VALUES (101, 'Raju', 'Delhi');
```

### Multiple Insert

```sql
INSERT INTO person (id, name, city)
VALUES
(102, 'Shyam', 'Mumbai'),
(103, 'Paul', 'Chennai');
```

### Without Column Names

```sql
INSERT INTO person
VALUES (104, 'Alex', 'Pune');
```

---

## 13. Read Data

### Select All

```sql
SELECT * FROM person;
```

### Select Specific Column

```sql
SELECT name FROM person;
```

### Multiple Columns

```sql
SELECT name, city FROM person;
```

---

## 14. Update Data

### Example: Change Raju’s city to Bangalore

```sql
UPDATE person
SET city = 'Bangalore'
WHERE name = 'Raju';
```

Better to use id:

```sql
UPDATE person
SET city = 'Bangalore'
WHERE id = 101;
```

---

## 15. Delete Data

### Delete by ID

```sql
DELETE FROM person
WHERE id = 104;
```

---

## ✅ Summary

* Database = organized data
* DBMS = tool to manage data
* PostgreSQL = RDBMS using SQL

### Learned:

* Create DB
* Create Table
* Insert
* Select
* Update
* Delete

# 📘 PostgreSQL Notes – Part 2 (Simple English)

## 1. DELETE Operation (CRUD)

To delete a record from table:

DELETE FROM person
WHERE id = 104;

Select the query → Execute

After delete, check:

SELECT * FROM person;

Result: Alex record removed

Only 3 persons left

✅ Now all CRUD operations completed:

Create

Read

Update

Delete

---

## 2. Problems in Our Old Table Structure

### Problem 1 – Duplicate ID

Example:

INSERT INTO person VALUES (101, 'Alex', 'Pune');

Raju already has ID = 101

Still database accepted duplicate
❌ This should NOT happen.

### Problem 2 – NULL Values

INSERT INTO person (id, name)
VALUES (105, 'Vikta');

City not provided

Result:

id    name    city
105   Vikta   NULL

❌ City became NULL
We need rules to avoid this.

---

## 3. Data Types

Data type defines what kind of data a column will store.

### Common Data Types

Numeric

INT → whole numbers

DECIMAL → numbers with points

String

VARCHAR(100)

Date

For DOB, joining date

Boolean

TRUE / FALSE

### Numeric Types Example

INT → normal numbers

BIGINT → very large numbers

DECIMAL(5,2)

Example:

155.50 → valid for DECIMAL(5,2)
1501.22 → NOT valid (too big)

---

## 4. Constraints

Constraint = Rule on column

Used to:

Stop duplicates

Stop NULL

Set default values

### Types:

Primary Key

NOT NULL

UNIQUE

DEFAULT

SERIAL (Auto Increment)

### Primary Key

Unique for each row

No duplicate

No NULL

Only ONE per table

Example:

id INT PRIMARY KEY

NOT NULL
name VARCHAR(50) NOT NULL

### DEFAULT Value

account_type VARCHAR(50)
NOT NULL DEFAULT 'Savings';

If no value given → ‘Savings’ stored

### Auto Increment (SERIAL)

PostgreSQL uses SERIAL

id SERIAL PRIMARY KEY

Automatically:
1, 2, 3, 4…

---

## 5. TASK – Create Bank Database

### Create Database

CREATE DATABASE bank_db;

### Create Employee Table

CREATE TABLE employee (
emp_id SERIAL PRIMARY KEY,

```
f_name VARCHAR(100) NOT NULL,

l_name VARCHAR(100) NOT NULL,

email VARCHAR(100) NOT NULL UNIQUE,

department VARCHAR(50),

salary DECIMAL(10,2) DEFAULT 30000.00,

hire_date DATE NOT NULL DEFAULT CURRENT_DATE
```

);

### Verify Table

\d employee

You will see:

NOT NULL

DEFAULT values

PRIMARY KEY

Index created automatically

---

## 6. Insert Employee Data

### Normal Insert

INSERT INTO employee
(emp_id, f_name, l_name, email, department, salary, hire_date)
VALUES
(1, 'Raj', 'Sharma', '[raj@gmail.com](mailto:raj@gmail.com)', 'IT', 45000, '2024-03-10');

### Using Defaults

INSERT INTO employee
(f_name, l_name, email, department)
VALUES
('Priya', 'Singh', '[priya@gmail.com](mailto:priya@gmail.com)', 'HR');

✔ What happens automatically:

emp_id → 2 (SERIAL)

salary → 30000

hire_date → today’s date

---

## 7. SERIAL Problem Explained

If we insert first record manually with id = 1
Then next insert without id → system again tries 1 → error!

### Solution:

SELECT setval('employee_emp_id_seq', 1);

Now next value will be 2.

---

## 8. UNIQUE Constraint Test

Try duplicate email:

INSERT INTO employee
(f_name, l_name, email, department)
VALUES
('Sachin', 'Verma', '[priya@gmail.com](mailto:priya@gmail.com)', 'IT');

❌ Error:

duplicate value violates unique constraint

✔ UNIQUE working correctly

---

## 9. Insert Multiple Records

Teacher provided ready query with 10 employees
(Use that to fill table for next topics)

Check:

SELECT * FROM employee;

---

## 10. SQL Clauses (Start of Section 4)

Clause = condition used with SQL query

We will learn:

WHERE

DISTINCT

ORDER BY

LIMIT

LIKE

### WHERE Clause

Used to fetch specific data

Example:

SELECT * FROM employee
WHERE emp_id = 5;

Fetch only one employee

Based on primary key

---

## ✅ Summary of This Part

### Problems Solved

Duplicate ID

NULL values

Default values

Auto increment

### New Concepts Learned

Data Types

Constraints

PRIMARY KEY

NOT NULL

UNIQUE

DEFAULT

SERIAL

### Practical Work

Created bank_db

Created employee table

Tested constraints

Inserted data

Verified behavior

