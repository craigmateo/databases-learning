# Module 3: Modelling and Classification of DBMS

## Module 3:  
### Data Modelling and Classification of DBMS

### Introduction

In module 3, you will be introduced to the database schema and learn about data independence when implementing a database. You will learn about two different kinds of data independence: logical and physical data independence.

This module discusses the different classifications of DBMS. By the end of this module, you should be able to identify different kinds of data models. In addition, you will get familiar with different kinds of distributed systems.

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Build a scenario to demonstrate physical data independence and its use in database design.
- Use a logical view to achieve physical data independence.
- Identify different classifications of database management systems.
- Understand the database schema of the database management system.

### Key Terms and Concepts

| Key Term or Concept          | Definition                                                                                                                      |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Schema**                  | A logical representation of a database.                                                                                        |
| **Data Independence**       | When data is independent of the logical and physical constraints of the database.                                               |
| **Physical Data Independence** | Physical data independence is the method to make physical storage structures and/or indexing strategy of data independent of external application and the logical schema of the application. |
| **Logical Data Independence**  | Logical data independence is achieved when the view of the end users remains the same even after modifications (like adding columns, adding tables, removing tables, etc.) to the logical schema. |
| **Relational Data Models**  | The relational model represents data as relations or tables.                                                                    |
| **Centralized Systems**     | The DBMS and database are stored on a single system and other systems access the single system.                                 |
| **Distributed Database Systems** | The DBMS and database are distributed on various systems which are connected through a network.                               |
| **Homogeneous Database Systems** | The DBMS and database are distributed on various systems using the same software which is connected through a network.          |
| **Heterogeneous Database Systems** | The DBMS and database are distributed on various systems using different software, in addition to a common software, to support data exchange which is connected through a network. |

## Database Schema

A database schema is a logical representation of the database, often shown using an Entity Relationship Diagram (ERD).

### Logical and Physical Data Independence

**Data Independence** means that changes in data storage or structure do not affect how end users perceive the data. Only relevant data is exposed to users.

There are two types of data independence:

- **Physical Data Independence:**  
  Separates physical storage and indexing methods from the logical schema and external applications. Changes to storage do not affect the user view or logical schema.

- **Logical Data Independence:**  
  The end user’s view remains unchanged even if the logical schema is modified (e.g., adding or removing tables or columns). This allows structural changes without impacting the user experience.

*Example:* If an e-commerce site removes a manufacturer's product from their database, the consumer interface is unaffected.

## Different Classification of DBMS

Database Management Systems (DBMS) can be classified based on Data Model, User Numbers, and Database Distribution.

### Classification Based on Data Model
- **Relational Data Models:**  
  Represent data as tables or relations. Examples: SQL Server, DB2.
- **Object-oriented Models:**  
  Represent data as objects, combining OOP concepts with databases. Examples: Zodb, Caché.

### Classification Based on User Numbers
- **Single-User:**  
  Supports only one user at a time (e.g., most personal computers).
- **Multi-User:**  
  Supports multiple users simultaneously (common in industry DBMS).

### Classification Based on Database Distribution
- **Centralized Systems:**  
  DBMS and database stored on a single system; other systems access it remotely.
- **Distributed Database Systems:**  
  DBMS and database spread across multiple systems connected by a network.
- **Homogeneous Database Systems:**  
  Distributed systems running the same DBMS software connected via a network.
- **Heterogeneous Database Systems:**  
  (Implied but not detailed) Systems running different DBMS software connected together.

