# Module 6: DDL, Integrity Rules, and Constraints

## Introduction

In module 6, you will be introduced to the data definition language and learn about different techniques when creating, altering, or deleting the database. You will learn about creating databases and tables, as well as altering and dropping tables.

This module discusses different integrity rules and constraints. By the end of this module, you should be able to create, alter, and drop tables. You will also gain some basic knowledge of SQL commands.

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Create, alter and drop tables  
- Differentiate between alter and update SQL command  
- Describe integrity rules and constraints  

### Key Terms and Concepts

List the key terms and concepts and provide the definitions.

| Key Term or Concept | Definition |
|---------------------|------------|
| **DDL** | Data Definition Language |
| **Creating Database** | `CREATE Database <Database Name>` |
| **Creating Table** | `CREATE Table <TableName> ( ColumnName, DataType, Constraint );` |
| **Altering Table** | `ALTER Table <TableName> (Add different commands to add or remove)` |
| **Dropping Table** | `DROP Table <TableName>` |
| **Column Constraints** | These are optional and are used to restrict the type of data that will be stored in the column. Some examples are `NULL`, `NOT NULL`, `UNIQUE`, `PRIMARY KEY`, and `DEFAULT`. |
| **NULL constraint** | Column with a null value is allowed. |
| **UNIQUE Constraint** | Column can only have unique values. |
| **PRIMARY KEY Constraint** | Identifies a column as a primary key. |
| **AUTO_INCREMENT** | This constraint can be used in a column to provide incremental and unique value. |
| **FOREIGN KEY** | This constraint is used to define the foreign key to represent the relation with another table, which has a `PRIMARY KEY`, which has the same datatype as the `FOREIGN KEY`. |
| **CHECK** | It is the constraint which restricts the values that are accepted in a table. |

## Data Definition Language

Data Definition Language (DDL) is a part of Structured Query Language (SQL) which is used to create, alter or delete the database or the tables.

### Create Database

To create a database using SQL in MySQL, the command:

```sql
CREATE DATABASE DB;
```

is used where DB is the name of the database.

### Create Table
To create a table using SQL in MySQL, the command is:

```sql
CREATE TABLE <TableName> (ColumnName DataType Constraint);
```

where the constraint is optional.

For example:

```sql
CREATE TABLE T1 (
  cId INT PRIMARY KEY
);
```

In this example, DB is the database where table T1 is created with column cId of datatype int and constraint as the primary key.

### Alter Table
In the database, there may be many cases where you need to alter the table because of a change in business requirements or data. Instead of creating a table from scratch, the keyword ALTER can be used.

``ALTER TABLE`` can be used to remove columns or add columns (with or without constraints).

For example, to add a column:

```sql
ALTER TABLE student ADD FeesPaid DECIMAL;
```

In the above example, the ``student`` table is altered to add a ``FeesPaid`` column, which is of type decimal.

Another keyword ``ADD`` was used to add the column. You will learn more about data manipulation techniques in the next module.

### Drop Table
With changing business requirements, some data could become redundant or useless. To keep the database consistent, the ``DROP TABLE`` command can be used to remove unnecessary tables.

For example: In a COLLEGE database, if storing a student’s address is no longer required, the data can be removed to avoid keeping useless data.

