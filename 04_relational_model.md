# Module 4: Relational and Entity Relational Data Model

## Module 4:  
### The Relational and Entity Relational Data Model

### Introduction

In module 4, you will be introduced to the concepts of the relational and entity relational data model. You will learn about tables, columns, degree, and records. This module covers different types of tables and the basic fields within the table.

This module discusses entities and different types of them. By the end of this module, you should be able to identify different kinds of attributes and keys. In addition, you will get familiar with different kinds of table relationships.

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Explore basic Entity Relation Diagram (ERD) components — entities, attributes, relationships.
- Define key, candidate key, prime key, enterprise key, and determinant.
- Explain relational database terminology.

### Key Terms and Concepts

| Key Term or Concept   | Definition                                                                                  |
|----------------------|---------------------------------------------------------------------------------------------|
| **Relational Data Model** | A logical representation of a database.                                                  |
| **Table**            | A table is a collection of columns which contains data. A collection of tables constitutes a database. |
| **Column**           | A column is a part of the table that stores data in an organized way.                       |
| **Domain**           | In a column, an invalid entry should not be allowed; only valid data should be saved in a column. |
| **Records or Tuple** | A record or a tuple is a collection of data which relates to one another.                   |
| **Degree**           | It is the number of columns in a table.                                                    |
| **Entity**           | An entity is a real-world thing or an object.                                              |
| **Weak Entity**      | When an entity has a dependency on another entity, it is called a weak entity.             |
| **Strong Entity**    | When a table has no foreign key and can exist without dependency on another entity, it is called a strong entity. |
| **Entity Type**      | A collection of similar entities is called an entity type.                                |
| **Entity Set**       | A collection of entities of the same entity type.                                         |
| **Primary Key**      | A unique value in a table used to identify a record.                                      |
| **Foreign Key**      | A foreign key refers to the primary key of another table of the same data type.           |

## Relational Data Model

A relational data model consists of a collection of related tables and uses Structured Query Language (SQL).

### Table
A table is a collection of columns containing data. Multiple tables make up a database.

### Column
A column stores data in an organized way within a table. Each column has a name and a data type (e.g., "First Name" with datatype VARCHAR).

### Domain
A domain restricts the type of valid data stored in a column. For example, the "First Name" column domain would allow only variable characters (VARCHAR).

### Records or Tuple
A record (or tuple) is a collection of related data in a table row.  
Example: An employee table’s row containing employee name, employee ID, address, etc., is a record.

## Tables & Entities

### Types of Tables

- **Regular Tables**  
  Contain standard data and usually have several fields.

- **Reference Tables**  
  Hold static data, typically with 2 to 4 fields.

### Common Features of All Tables

- **Primary Key**  
  Uniquely identifies each row of data.

- **Description Field**  
  Provides a quick visual identifier for the row.

- **Timestamp Fields**  
  Usually two fields representing when the row was created and last modified.

---

### Entities

An **entity** is a real-world object or thing, such as a lecturer, student, or employee.

#### Weak Entity  
An entity dependent on another entity.  
Example: A "Parents Name" table dependent on the primary key of the "Student" table.

#### Strong Entity  
An entity that exists independently without foreign key dependencies.

#### Entity Type  
A collection of similar entities.

#### Entity Set  
A collection of entities of the same entity type.

Entities are usually represented in diagrams by a box with the entity name inside, for example:  
`Student`

---

### Types of Entities

1. **Independent Entities**  
2. **Dependent Entities**  
3. **Characteristic Entities**

