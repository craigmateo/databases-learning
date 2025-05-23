# Module 8: Advanced DML Joins

## Introduction

In module 8, you will be introduced to joins and learn about different techniques when selecting data using joins. You will learn about Inner, Left, Right, Full, and Cross Joins.

This module discusses different Venn Diagrams for joins to illustrate how joins work. By the end of this module, you should be able to create SQL join statements to retrieve data and learn the basics of subqueries.

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Define a join operation
- Use basic SQL SELECT statements to perform inner joins, outer joins, and subqueries
- Identify a correlated and non-correlated subquery
- Differentiate between a JOIN operation, Cross Join (CARTESIAN PRODUCT), and a UNION

### Key Terms and Concepts

| Key Term or Concept | Definition                                                                 |
|---------------------|----------------------------------------------------------------------------|
| **Joins**           | Joins are used to retrieve data from multiple tables in a single command.  |
| **Inner Joins**     | An Inner Join is used to connect two tables. It retrieves common records from both tables. |
| **Left Join**       | Used to retrieve all records from the left table, and matching records from the right table. |
| **Right Join**      | Used to retrieve all records from the right table, and matching records from the left table. |
| **Full Join**       | Retrieves records from both the left and right tables, including non-matching rows from both. |
| **Cross Join**      | Returns the Cartesian product of two tables (all possible combinations of rows). |
| **Subqueries**      | Queries embedded within another query, used to perform operations on subsets of data. |

## Joins

Data Manipulation Language has an important concept of **Joins**.

Joins are used to retrieve data from multiple tables in a single command.

There are mainly 4 types of Joins:
- Inner Join
- Left Outer Join
- Right Outer Join
- Full Outer Join

---

### Inner Joins

An Inner Join is used to connect two tables. It retrieves common records from both tables. Uncommon records are rejected.

In the Venn Diagram below, the two tables A and B intersect. The shaded region is the common record. The diagram represents the Inner Join.

**Inner Join Commands:**  
The `INNER JOIN` clause is used to join two tables.

**Example:**

Assume two tables `professor` and `student` in a `college` database.

To find which professors teach which students (matching on `ProgramName`):

```sql
SELECT professor.ProfessorName, student.StudentName, professor.ProgramName
FROM professor
INNER JOIN student
ON professor.ProgramName = student.ProgramName;
```

This query returns only professors and students with matching ``ProgramName``.

### Left Join
Used to retrieve all records from the left table (``professor``), plus matched records from the right table (``student``).

In the Venn Diagram below, the shaded region includes all of table A and the intersection with table B.

Left Join Commands:
The ``LEFT JOIN`` clause is used to join two tables.

**Example:**
To get all professors and any students they teach (including professors without students):

```sql
SELECT professor.ProfessorName, student.StudentName, professor.ProgramName
FROM professor
LEFT JOIN student
ON professor.ProgramName = student.ProgramName;
```

All professors appear; students will be ``NULL`` if no match exists.

### Right Join
Used to retrieve all records from the right table (``student``), plus matched records from the left table (``professor``).

In the Venn Diagram below, the shaded region includes all of table B and the intersection with table A.

Right Join Commands:
The ``RIGHT JOIN`` clause is used to join two tables.

**Example:**
To get all students and the professors teaching them (including students without professors):

```sql
SELECT professor.ProfessorName, student.StudentName, student.ProgramName
FROM professor
RIGHT JOIN student
ON professor.ProgramName = student.ProgramName;
```

### Full Join
Used to retrieve records from both the Left and Right tables — all professors and all students regardless of matches.

Note: MySQL does not support ``FULL JOIN`` directly. Use a ``UNION`` of ``LEFT JOIN`` and ``RIGHT JOIN`` instead.

**Example:**
```sql
SELECT professor.ProfessorName, student.StudentName, professor.ProgramName
FROM professor
LEFT JOIN student
ON professor.ProgramName = student.ProgramName

UNION

SELECT professor.ProfessorName, student.StudentName, student.ProgramName
FROM professor
RIGHT JOIN student
ON professor.ProgramName = student.ProgramName;
```

This query returns all professors and all students, with NULLs where no match exists.

### Cross Join
Returns the Cartesian product of the two tables — every row from the first table combined with every row from the second.

**Example:**
If ``student`` has 10 rows and ``professor`` has 6 rows:

```sql
SELECT professor.ProfessorName, student.StudentName
FROM professor
CROSS JOIN student;
```

This returns 60 rows (10 * 6).


