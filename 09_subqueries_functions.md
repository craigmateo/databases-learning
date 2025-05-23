## Module 9: Subqueries and Library Functions

## Introduction

In this module, you will be introduced to the Library Functions in MySQL and learn about subqueries. You will learn about aggregate functions, conversion functions, date functions, and mathematical functions.

This module discusses different uses of these functions. By the end of this module, you should be able to create SQL statements that utilize different functions.

---

### Learning Outcomes

By the end of this module, you should be able to:

- Differentiate between scalar and vector aggregate functions  
- Use different aggregate functions  
- Use conversion functions, date functions, and mathematical functions  

---

### Key Terms and Concepts

| Key Term or Concept   | Definition                                                                                      |
|----------------------|------------------------------------------------------------------------------------------------|
| **Aggregate Functions** | Perform calculations on a set of values and return a single or summary value.                 |
| **AVG**              | Calculates the average of all values in a column.                                              |
| **COUNT**            | Returns the number of occurrences (rows) in a column or dataset.                               |
| **MAX**              | Finds the maximum value in a column.                                                           |
| **MIN**              | Finds the minimum value in a column.                                                           |
| **SUM**              | Adds all values in a column.                                                                    |
| **Conversion Function** | Converts the data type of a column or expression.                                            |
| **Date Function**    | Functions that help work with date values more easily.                                         |
| **Mathematical Function** | Functions that perform mathematical operations on data.                                    |

## Aggregate Functions

The database not only allows you to store and retrieve data but also perform different functions.

One of the useful functions in databases is **Aggregate Functions**.

Aggregate functions perform calculations on a set of values which return a single or summary value.

Some Aggregate Functions are:

- AVG  
- COUNT  
- MAX  
- MIN  
- SUM  

### Scalar and Vector Functions

Read this [opens in new window](#) to learn about scalar and vector functions.

---

### AVG

Watch video: *Using the COUNT, AVG, and SUM function in a MySQL query #10*

The `AVG` function calculates the average value of a set.

In Fig. 1 below, a SELECT query displays all columns, and the average of the ages for all students is 31.9 (calculated).

**Example:**

```sql
SELECT *, AVG(age) OVER () AS average_age FROM students;
```

Now, in Fig. 2, the `AVG` function is used to display just the average age which matches the results of Fig. 1.

**Example:**

```sql
SELECT AVG(age) AS average_age FROM students;
```

---

### COUNT

The `COUNT` function returns the number of occurrences.

In Fig. 3, there are 10 entries of Student Program; if unique values are required, use the `DISTINCT` clause.

**Example: Count all rows**

```sql
SELECT COUNT(*) AS total_students FROM students;
```

**Example: Count distinct programs**

```sql
SELECT COUNT(DISTINCT program) AS unique_programs FROM students;
```

---

### MAX

The `MAX` function is used to find the maximum value in a column.

The maximum student age in the database is ‘45’ (see Fig. 4).

**Example:**

```sql
SELECT MAX(age) AS oldest_student FROM students;
```

---

### MIN

The `MIN` function is used to find the minimum value in a column.

The minimum student age in the database is ‘20’ (see Fig. 5).

**Example:**

```sql
SELECT MIN(age) AS youngest_student FROM students;
```

Read: Min and Max [opens in new window](#)

---

### SUM

Watch video: *SQL Aggregation queries using Group By, Sum, Count and Having*

The `SUM` function adds all values of a column.

In Fig. 6, sum of all the ages of students in a database is shown.

**Example:**

```sql
SELECT SUM(age) AS total_age FROM students;
```

Read: Count, Avg and Sum [opens in new window](#)

---

### GROUP BY

The `GROUP BY` clause is used with the `SELECT` statement and is typically used with aggregate functions to return the aggregate value grouped by a column.

**Example: Average student age by program**

```sql
SELECT program, AVG(age) AS average_age
FROM students
GROUP BY program;
```

**Example: Minimum, maximum, and average student age by program**

```sql
SELECT program,
       MIN(age) AS youngest,
       MAX(age) AS oldest,
       AVG(age) AS average_age
FROM students
GROUP BY program;
```

---

### DISTINCT

Watch video: *SQL Server Distinct Keyword*

`DISTINCT` is used to select unique values from a column.

**Example: List distinct programs**

```sql
SELECT DISTINCT program FROM students;
```

## Conversion Function, Date Function, and Mathematical Function

---

### Conversion Function

This function converts the data type of a column.

In Fig. 7, the phone number of students, which is stored as an `INT`, is converted to `CHAR(3)` as displayed in the last column.

**Example:**

```sql
SELECT 
    student_id, 
    phone_number, 
    CAST(phone_number AS CHAR(3)) AS phone_char
FROM students;
```

---

### Date Function

The Date functions help to work with dates more easily.

One of the many Date functions is `CURDATE()` (see Fig. 8), which returns the current date.

**Example:**

```sql
SELECT 
    student_id,
    enrollment_date,
    CURDATE() AS today_date
FROM students;
```

---

### Mathematical Function

Mathematical functions help to perform calculations on the data.

Below are a few examples (Fig. 9) of common mathematical functions in SQL.

**Examples:**

```sql
SELECT 
    student_id,
    ABS(balance_due) AS absolute_balance,   -- absolute value
    CEIL(gpa) AS ceiling_gpa,               -- round up
    FLOOR(gpa) AS floor_gpa,                -- round down
    ROUND(gpa, 2) AS rounded_gpa            -- round to 2 decimals
FROM students;
```


