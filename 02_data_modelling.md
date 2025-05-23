# Module 2: Data Modelling

## Introduction

Here in module 2, you will be introduced to the concept of data modeling. You will learn about the three main types of data models, the importance of each model, and how the models can help when designing a database.

You will learn about the process of data modeling and why data modeling is important when enforcing business rules.

This module explains how data abstraction can be used to hide irrelevant details and information from the end user. The concepts of metadata and data dictionary will also be covered.

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Describe database models.
- Compare a client-server architecture to a terminal-based system.
- Describe the purpose of the data dictionary.
- Draw a three-tier architecture and place the database components in the appropriate tier.

### Key Terms and Concepts

| Key Term or Concept    | Definition                                                                                          |
|-----------------------|---------------------------------------------------------------------------------------------------|
| **Data Model**         | It represents logical relationships and constraints that determine how data will flow, get stored, and get accessed. |
| **Relation**           | Another term for the table.                                                                        |
| **Constraint**         | A restriction that determines what can be entered or edited in a table.                            |
| **Entity**             | An entity represents a real-world object, such as an employee or a project.                        |
| **Attribute**          | It represents properties, such as an employee's name, address, and birthdate.                      |
| **Structural Part**    | It is a set of rules that define how a database will be constructed.                               |
| **Manipulative Part**  | It is the operational part, which defines the types of operation that will take place on data in a database. For example, updating the structure of a database. |
| **Integrity Rules**    | These are the rules that ensure data in the database is accurate and without redundancy.           |
| **Conceptual Data Model** | Conceptual data models are summary level data models.                                            |
| **Logical Data Model** | This data model represents data with information about entities, attributes, and the relationships between entities. |
| **Physical Data Model**| This data model reflects how the data model should be implemented in the database.                 |
| **Data Modelling**     | Data Modeling is the process of creating a data model for the data to be stored in a database.     |
| **Data Abstraction**   | Data abstraction is the process of hiding irrelevant details and information from the user to ease user interaction with the database. |
| **View Level**         | It is the highest level which represents the end user's view of data.                             |
| **Logical Level**      | This level is both independent of software and hardware. Changes in either hardware or DBMS software have no effect on the database design at the conceptual level. |
| **Physical Level**     | It is simply the way the data is stored on disk. Each database vendor has its own way of storing the data. |
| **Metadata**           | Metadata defines and describes the data and relationships between tables in the database.          |
| **Data Dictionary**    | A data dictionary is a structure which holds metadata and information about it, such as tables, columns, data types, constraints, etc. |

## What is a Data Model?

A data model represents the logical relationships and constraints that determine how data flows, is stored, and accessed in a database.

### Main Components of a Data Model:
- **Structural Part:**  
  Defines rules for how a database will be constructed.

- **Manipulative Part:**  
  Defines the types of operations performed on the data, such as updating the database structure.

- **Integrity Rules:**  
  Ensure data accuracy and prevent redundancy.

### Types of Data Models

There are three main types of data models:

#### Conceptual Data Model
- High-level summary model, easy to understand.
- Used by businesses for confirmation and corrections.
- Shows entities (real-world objects like customers, orders) and their relationships in an abstract way.
- Entities have attributes (e.g., customer name, address).
- Relationships show associations, e.g., a customer has many orders.

#### Logical Data Model
- More detailed than conceptual models.
- Represents entities, attributes, relationships, and keys (primary and foreign).
- Focuses on data organization without physical implementation details.
- Includes normalization.
- Common types:  
  - Relational model (data as tables)  
  - Network model (data as record types)  
  - Hierarchical model (data as a tree structure)

#### Physical Data Model
- Reflects how data is physically implemented in the database.
- Entities and attributes correspond to tables and columns.
- Defines table names, column names, and data types according to database standards.

## Data Modelling & Metadata and Data Dictionary in DBMS

### Data Modelling
Data Modelling is the process of creating a data model for storing data in a database. Its goals include:

- Ensuring the database contains relevant data (e.g., entities like customers, addresses, orders).
- Defining relationships between tables/entities (e.g., customers place orders, orders are delivered to addresses).
- Enforcing constraints on data (e.g., order numbers have 6 digits and 2 letters; postal codes have 6 characters).

Data modeling provides a visual representation of data that enforces business rules.

### Data Abstraction
Data abstraction hides irrelevant details to simplify user interaction with the database.

There are three levels of data abstraction:

- **View Level:** Highest level representing the end user's view of data.
- **Logical Level:** Independent of hardware and software; changes here do not affect database design.
- **Physical Level:** How data is actually stored on disk, varying by database vendor.

### Metadata and Data Dictionary in DBMS
- **Metadata** describes data and relationships between tables, providing context (e.g., title, author, last modified).
- A **data dictionary** holds metadata and information about tables, columns, data types, and constraints.
- It helps users understand what data items mean in the real world and serves as a reference for database information.

