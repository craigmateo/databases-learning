# Module 13: Advanced SQL Concepts

### Introduction

In this module, you will be introduced to the concepts of **Transactions**, **Concurrency**, and **Stored Procedures**. You will learn to initiate transactions and create stored procedures to ease data handling techniques.

This module also discusses **Replication** and **Sharding**. By the end of this module, you should be able to understand the basic concepts of handling big data in the real world.

---

### Learning Outcomes

By the end of this module, you should be able to:

- Explain how transactions and replication are used to provide a robust database environment for high availability and performance
- Explain the concepts of concurrency
- Explain the concept and creation of stored procedures
- Improve database performance using vertical and horizontal partitioning

---

### Key Terms and Concepts

| Key Term or Concept | Definition |
|---------------------|------------|
| **Transactions**    | Transactions are used to commit or rollback changes made in a database. |
| **Concurrency**     | Concurrency is the process where multiple users can access the same record without affecting transactions. Concurrency allows multiple users to access the database simultaneously. |
| **Stored Procedures** | A stored procedure is a collection of multiple SQL statements. It is usually created to avoid writing the same SQL statement multiple times. |
| **Sharding**        | Multiple nodes with the data split up amongst them, distributing the load and improving performance and scalability. |

---

## Advanced SQL Concepts

---

### Transactions

🎥 **Watch**: *Database Transactions, part 1: Introduction*

Transactions allow changes in a database to be either **committed** or **rolled back**.

#### Key Clauses:
- `START TRANSACTION`
- `ROLLBACK`
- `COMMIT`

You start a transaction, run SQL commands, and then use either `COMMIT` or `ROLLBACK`.

#### Example:
Imagine you mistakenly delete a student's record:

    START TRANSACTION;

    DELETE FROM students WHERE FirstName = 'Alex';

    -- Realize it's a mistake:
    ROLLBACK;

    -- If the deletion is correct:
    -- COMMIT;

📘 **Read**: Transactions documentation

---

### Concurrency

**Concurrency** allows multiple users to access the same data without conflict, ensuring integrity and consistent performance.

📘 **Read**: [Concurrency Control](#)  
📘 **Read**: [Deadlock](#)

---

### Stored Procedures

🎥 **Watch**: *MySQL Stored Procedure 7 - Intro to Stored Procedures*

A **stored procedure** is a collection of SQL statements saved to be reused multiple times.

#### Example:
You frequently need to fetch `StudentNo` and `StudentProgram` from the `students` table.

    DELIMITER //

    CREATE PROCEDURE GetStudentInfo()
    BEGIN
        SELECT StudentNo, StudentProgram FROM students;
    END //

    DELIMITER ;

To call the procedure:

    CALL GetStudentInfo();

You can find it under the *Stored Procedures* folder in your DB GUI.

📘 **Read**: Stored Procedure documentation

---

### Replication and Sharding

🎥 **Watch**: *What is Data Replication?*

#### Replication
Replication is the process of copying data across databases to ensure availability and redundancy.

##### Types:
- **Master → Slave**: Most common, easy to implement, widely supported
- **Multi-Master**: More complex, better supported in Oracle and MS SQL Server

#### Sharding
Sharding splits data across multiple nodes (shards) for scalability.

- Requires 1 controller + N shards
- Ideal for isolated datasets
- Poor fit for cross-shard queries

#### Real-world Example: Banking
- Each bank branch uses a shard
- Central DB replicates the data across branches for access


