# Module 12: Indexes, Views, and Triggers

## Introduction

In this module, you will be introduced to the concepts of **Indexes**, **Views**, and **Triggers**. You will learn how to create indexes and understand how they speed up the information retrieval process.

This module also covers views, including how to create them and their uses. By the end of this module, you should be able to create triggers and use them effectively within a database.

---

## Learning Outcomes

By the end of this module, you should be able to:

- Create indexes, views, and triggers.
- Differentiate between **materialized views** and **logical views**, understanding their uses, advantages, and disadvantages.
- Draw a simple schematic diagram to explain an index structure.
- Determine the appropriate index structure for a given relation.

---

## Key Terms and Concepts

| Key Term or Concept | Definition                                                                                 |
|---------------------|--------------------------------------------------------------------------------------------|
| **Index**           | Indexes are database structures used to find data quickly without scanning the whole table.|
| **View**            | A view is a virtual table based on the result of a query. You can run most commands on views just like on tables. |
| **Trigger**         | A trigger is a procedural code that automatically executes when an **INSERT**, **UPDATE**, or **DELETE** operation occurs on a table. |

## Index

Indexes can be used to find data fast and quickly. Just like how the index page in a book helps you find a particular topic without flipping through the whole book, database indexes help locate data efficiently without scanning every row in a table.

*For more details, you can refer to Module 5 on File Organization.*

---

## Creating an INDEX in a Database

Consider a **COLLEGE** database with a table called `students` that contains many student records.

### Without an Index

When searching for a student by their last name without an index, the database performs a **full table scan** — it checks every row in the `students` table until it finds matching entries. This is slow when the table contains a large number of records.

**Fig 1:** Searching `LastName` without an index  
*(Imagine a database engine scanning every row sequentially.)*

---

### With an Index

If an index is created on the `LastName` column, the database uses this index to quickly jump to the matching rows, making the search much faster.

**Fig 2:** Searching `LastName` with an index  
*(Imagine flipping directly to the indexed pages like in a book.)*

---

### How to Create an Index

You can create an index on the `LastName` column of the `students` table using this SQL command:

    CREATE INDEX idx_lastname ON students(LastName);

Alternatively, the index can be created when the table is initially created, for example:

    CREATE TABLE students (
        student_id INT PRIMARY KEY,
        FirstName VARCHAR(50),
        LastName VARCHAR(50),
        Age INT,
        -- other columns
        INDEX idx_lastname (LastName)
    );

---

### Example: Searching Students by Last Name

Suppose you want to find all students with the last name "Smith":

    SELECT * FROM students WHERE LastName = 'Smith';

- **Without an index**: The database scans all student records one by one.
- **With an index**: The database uses the index to directly access only the relevant rows, greatly improving search speed — especially noticeable when the table has thousands or millions of records.

---

## Views

Let us go back to Joins (Module 8) and see how views could have been used to simplify JOIN statements.

In an **Inner Join**, we combined details from the `student` and `college` tables. But what if we needed to run the same query frequently? Instead of writing the JOIN query repeatedly, we could create a **VIEW** based on that query.

---

### Creating a View

For example, suppose you want to create a view for the INNER JOIN of `student` and `college` tables:

    CREATE VIEW student_college_view AS
    SELECT s.student_id, s.student_name, c.college_name, c.college_location
    FROM student s
    INNER JOIN college c ON s.college_id = c.college_id;

---

### Using the View

Once created, you can query the view just like a table:

    SELECT * FROM student_college_view WHERE college_location = 'New York';

This will return all students who attend colleges located in New York, without needing to write the JOIN again.

---

### Benefits of Views

- **Simplify complex queries:** Encapsulate joins and filters into reusable queries.
- **Improve code readability:** Other users can query the view without needing to understand the underlying joins.
- **Security:** You can restrict access to underlying tables by giving permissions on views instead.

---

### Example Outputs (Fig 5 and Fig 6)

- **Fig 5:** Shows data retrieved by querying the view.
- **Fig 6:** Shows using the view in further SQL operations such as filtering or joining with other tables.

---

## Triggers

A trigger is executed whenever an **INSERT**, **UPDATE**, or **DELETE** operation is performed on a table.

---

### Example Scenario

Consider a **COLLEGE** database with two tables: `students` and `professor`. We want to keep an audit trail of important changes made to the `students` table. For this, we create a new table called `student_program_audit` to store snapshots of student information whenever an update occurs on the `students` table.

We will store three fields in the audit table:  
- `StudentNo`  
- `StudentName`  
- `StudentProgram`

---

### Step 1: Create the audit table

    CREATE TABLE student_program_audit (
        StudentNo INT,
        StudentName VARCHAR(100),
        StudentProgram VARCHAR(100),
        AuditTimestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    );

---

### Step 2: Create the Trigger

The trigger will fire **before an UPDATE** on the `students` table, inserting the old student data into the audit table before it changes.

    CREATE TRIGGER trg_student_update
    BEFORE UPDATE ON students
    FOR EACH ROW
    BEGIN
        INSERT INTO student_program_audit (StudentNo, StudentName, StudentProgram)
        VALUES (OLD.StudentNo, OLD.StudentName, OLD.StudentProgram);
    END;

---

### Step 3: Update the `StudentProgram` column in the `students` table

Before Update (example data):

| StudentNo | StudentName | StudentProgram       |
|-----------|-------------|---------------------|
| 101       | Alice Smith | Computer Science    |

---

Update Statement:

    UPDATE students
    SET StudentProgram = 'Data Science'
    WHERE StudentNo = 101;

---

### Step 4: After the update, the audit table is populated with the previous student data:

| StudentNo | StudentName | StudentProgram     | AuditTimestamp          |
|-----------|-------------|-------------------|-------------------------|
| 101       | Alice Smith | Computer Science  | 2025-05-23 14:30:00     |

---

### Summary:

- The trigger automatically stores the old data before changes occur.
- This keeps a history of changes for auditing or rollback purposes.
- Triggers can be defined for INSERT, UPDATE, or DELETE events.

---

