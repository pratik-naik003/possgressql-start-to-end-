
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
