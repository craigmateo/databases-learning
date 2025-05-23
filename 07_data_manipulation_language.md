# Module 7: Data Manipulation Language (DML)

## Introduction

In Module 7, you will be introduced to the data manipulation language and learn about different techniques when selecting, inserting, or deleting data in a table. You will learn about grouping and ordering data when querying.

This module discusses wildcards that are used to look for special characters. By the end of this module, you should be able to create SQL statements to retrieve data using a wildcard and select clause.

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Select and insert data in the database  
- Update and delete data  
- Group and order data  

### Key Terms and Concepts

List the key terms and concepts and provide the definitions.

| Key Term or Concept       | Definition                                                                                      |
|--------------------------|------------------------------------------------------------------------------------------------|
| **DML**                  | Data Manipulation Language                                                                     |
| **Data Manipulation Language** | DML is a part of Structured Query Language (SQL) which is used to SELECT, INSERT, UPDATE, and DELETE. |
| **SELECT**               | The SELECT statement is used to retrieve data from the database. Many different criteria could be set to retrieve data. |
| **ORDER BY**             | ORDER BY command can be used along with the SELECT statement to retrieve rows in order.        |
| **GROUP BY**             | A GROUP BY statement is used with the SELECT statement to group the same kind of data.         |
| **WHERE**                | To add the criteria to SELECT statements, add a WHERE clause to it.                            |
| **INSERT**               | To insert data in the table, the INSERT clause is used.                                        |
| **UPDATE**               | UPDATE statement, as the name suggests, updates the data in the table.                         |
| **DELETE**               | The DELETE statement is used to permanently remove rows in Database.                           |
| **Wildcard**             | The wildcard is used to search for data that contain some specific letters. It is used with the LIKE clause. |

## Data Manipulation Language (DML)

Data Manipulation Language (DML) is a part of Structured Query Language (SQL) which is used to **SELECT**, **INSERT**, **UPDATE**, and **DELETE** data.

---

### SELECT statement

The `SELECT` statement is used to retrieve data from the database. Many different criteria can be set to retrieve data.

**Example 1:** Retrieve all columns from the table `student` in the database `db`.

```sql
SELECT * FROM db.student;
```

**Example 2:** Retrieve only the StudentNo column from the student table.

```sql
SELECT StudentNo FROM db.student;
```

**Example 3:** Retrieve the StudentNo and ProgramName columns from the student table.

```sql
SELECT StudentNo, ProgramName FROM db.student;
```

### ORDER BY statement
``ORDER BY`` can be used along with ``SELECT`` to retrieve rows in a specified order.

Before ``ORDER BY``, the ProgramName column might be in random order:

```sql
SELECT StudentNo, ProgramName FROM db.student;
```

After ordering by ProgramName ascending (alphabetical order):

```sql
SELECT StudentNo, ProgramName FROM db.student ORDER BY ProgramName ASC;
```

You can order the list in descending order by using ``DESC``:

```sql
SELECT StudentNo, ProgramName FROM db.student ORDER BY ProgramName DESC;
```

By default, ``ORDER BY`` uses ascending order (``ASC``).

### WHERE clause in SELECT statement

To add conditions to a ``SELECT`` statement, use the ``WHERE`` clause.

**Example:** Retrieve all students with age above 25:

```sql
SELECT * FROM db.student WHERE age > 25;
```

### INSERT statement
To insert data into a table, use the ``INSERT`` clause.

Before Insert:

Assume the table ``student`` has no records.

Insert a new student:

```sql
INSERT INTO db.student (StudentNo, FirstName, LastName, Age, ProgramName) 
VALUES (18712345, 'John', 'Doe', 22, 'Computer Science');
```

After Insert:

The student table now has one record for John Doe.

### UPDATE statement
The ``UPDATE`` statement updates existing data in a table.

Before UPDATE:

| StudentNo | FirstName | LastName | Age | ProgramName      |
| --------- | --------- | -------- | --- | ---------------- |
| 18712345  | John      | Doe      | 22  | Computer Science |


Update the ProgramName for StudentNo 18712345 to 'DB':

```sql
UPDATE db.student
SET ProgramName = 'DB'
WHERE StudentNo = 18712345;
```

| StudentNo | FirstName | LastName | Age | ProgramName |
| --------- | --------- | -------- | --- | ----------- |
| 18712345  | John      | Doe      | 22  | DB          |

``UPDATE`` is useful to fix erroneous records or update information.

### DELETE statement
The ``DELETE`` statement is used to permanently remove rows from a database table.

Example: Delete a student record where StudentNo is 18712345:

```sql
DELETE FROM db.student WHERE StudentNo = 18712345;
```

## Wildcard

A wildcard is used to search for data that contains some specific letters. It is used with the `LIKE` clause in SQL.

---

### Percent sign `%`

The percent sign `%` represents zero or more characters.

**Example:**  
Display all program names starting with the letter 'C':

```sql
SELECT ProgramName FROM db.programs
WHERE ProgramName LIKE 'C%';
```

This will match ``Computer Science``, ``Chemistry``, ``Creative Writing``, etc.

### Underscore _
The underscore _ represents any single character.

**Example:**
Display all program names where the second letter is 'a' (e.g., Data, Math):

```sql
SELECT ProgramName FROM db.programs
WHERE ProgramName LIKE '_a%';
```

This matches program names where the second character is 'a', followed by any number of characters. You can combine these wildcards to match various patterns in your search criteria.


