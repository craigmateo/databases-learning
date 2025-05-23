# Module 5: Relationship, File Organization, SQL

## Module 5:  
### Relationships, File Organization, and Introduction to SQL

### Introduction

In module 5, you will be introduced to identifying and non-identifying relationships and learn about file organization techniques. You will learn about sequential, hashed, and index data structures.

This module also introduces you to SQL Boolean expressions. By the end of this module, you should be able to identify different kinds of data types and know which datatype to use when developing a database.

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Differentiate between identifying and non-identifying relationships.
- Describe the three types of file organization.
- Justify using an index structure.
- Compare sequential files, hashed, and index data structures.
- Explain database Boolean logic operators.
- Choose appropriate data types to create tables.
- Differentiate between cardinality and degree of relationships.

### Key Terms and Concepts

| Key Term or Concept           | Definition                                                                                                 |
|------------------------------|------------------------------------------------------------------------------------------------------------|
| **Identifying Relationship**   | A relationship between tables where the primary key contains the foreign key, usually shown as a solid line in an ERD. |
| **Non-Identifying Relationship** | A relationship where the primary key does not contain the foreign key, usually shown as a dotted line in an ERD.   |
| **Comparison Operators**       | `<`, `<=`, `>=`, `!=`                                                                                     |
| **Special Comparison Operators** | `IN`, `BETWEEN`, `IS`, `NOT`                                                                              |
| **Multiple and Grouped Conditionals** | `AND`, `OR`, `()`                                                                                        |
| **Datatypes in SQL**           | Categories include Text types, Number types, and Time and date types.                                     |
|

## Relationship & File Organization

### Relationship

- **Identifying Relationship:**  
  A relationship between tables where the **primary key contains the foreign key**.  
  It is usually represented by a **solid line** in an ERD.

  ![Identifying Relationship](m5_relationship1)  *(Replace with actual image or link)*

- **Non-Identifying Relationship:**  
  A relationship between tables where the **primary key does not contain the foreign key**.  
  It is usually represented by a **dotted line** in an ERD.

  ![Non-Identifying Relationship](m5_relationship2)  *(Replace with actual image or link)*

*Read Chapter 8 (Types of Relationship)*

*Watch video: Database Tables, Primary Keys, Foreign Keys, and Relationships*  
*Watch video: Microsoft Access Relationship Types*

---

### File Organization

Different techniques used in DBMS to organize data:

- **Sequential**  
- **Indexing**  
- **Hash Structure**

# Resolving Many-To-Many Relationship with Identifying Relationships

A many-to-many relationship is depicted in a model when both ends of the relationship show a cardinality of **‘many’**.  
A relational database **should not** be implemented with this type of relationship. To resolve, the many-to-many relationship is converted into two one-to-many relationships.

---

### Example: Students and Courses

STUDENTS ->O-------O<- COURSES


- A student may take many courses.
- A course may be attended by many students.

This is a many-to-many (M:N) relationship.

---

### Original Table Structure:

**STUDENTS**

| Column      | Key  |
|-------------|------|
| student_id  | PK   |
| first_name  |      |
| last_name   |      |
| address     |      |

**COURSES**

| Column      | Key  |
|-------------|------|
| course_id   | PK   |
| course_name |      |
| duration    |      |

---

### Resolving the Many-to-Many Relationship

To resolve the many-to-many relationship, a new entity is added between the two entities.  
This new entity is referred to as an **associative entity**, **junction entity**, or **bridge entity** (all synonymous).

- The new entity contains the primary keys of the two tables.
- These combined keys form the new entity’s **composite primary key**.

---

### Modified Model:

STUDENTS -||------O<- ENROLLMENTS ->O------||- COURSES


- A student may have many enrollments; an enrollment is tied to one student.
- A course may have many enrollments; an enrollment is tied to one course.

---

### New Table Structures:

**STUDENTS**

| Column      | Key  |
|-------------|------|
| student_id  | PK   |
| first_name  |      |
| last_name   |      |
| address     |      |

**ENROLLMENTS**

| Column      | Key     |
|-------------|---------|
| student_id  | PK, FK  |
| course_id   | PK, FK  |

**COURSES**

| Column      | Key  |
|-------------|------|
| course_id   | PK   |
| course_name |      |
| duration    |      |

---

### Important Notes

- The structure of **STUDENTS** and **COURSES** remains unchanged.
- The new entity **ENROLLMENTS** has a **composite primary key** made up of the primary keys of the other two tables.
- This creates **identifying relationships** between STUDENTS/ENROLLMENTS and COURSES/ENROLLMENTS, because ENROLLMENTS' primary key contains the parent tables’ keys.
- Foreign key relationships between ENROLLMENTS and STUDENTS/COURSES ensure **referential integrity**.
- This model can be applied to scenarios where a student enrolls in multiple courses.

# Boolean Expressions in SQL & Datatypes in SQL

**SQL** - Structured Query Language is a database language for handling data.

---

## Basic Expressions in SQL

### Standard Comparison Operators
The normal set which is very similar to C-like languages:

- `<`, `<=`, `>=`, `!=`  
- Equality check uses a single equal sign: `=`  
- Not equal can be written two ways:  
  - Used to be `<>`  
  - `!=` is now acceptable  

### Special Comparison Operators
- **IN** – check if a value is in a list.  
  Example: `id IN (1, 2, 4, 5, 6)`

- **BETWEEN** – inclusive check between two values.  
  Example: `id BETWEEN 1 AND 4`

- **IS** – allows checking for nulls or Booleans.  
  Examples: `IS NULL` or `IS TRUE`

- **NOT** – negates special operators.  
  Examples:  
  `id NOT IN (1, 2, 4, 5, 6)`  
  `id NOT BETWEEN 1 AND 4`  
  `IS NOT NULL`

### Multiple and Grouped Conditionals
- Use `AND` and/or `OR` to check against multiple conditions.  
- Use brackets to group conditions together.

Examples:  

```sql
id > 4 AND name LIKE 'Dan%'
(id = 4 AND name LIKE 'Dan%') OR id = 2
```

#### Datatypes in SQL

Watch Video: MySQL 24 - Important Data Types

#### Text Types
- **CHAR / CHARACTER** – fixed-length string, always occupies defined space  
- **VARCHAR / CHARACTER VARYING** – variable length string  
- **TEXT** – variable length  

#### Number Types
- **INT** – whole numbers  
- **DECIMAL / NUMERIC** – fixed precision numbers  
- **MONEY** – 8 bytes size, range from -922337203685477.5808 to +922337203685477.5807  

#### Time and Date Types
- **TIMESTAMP** – contains both date and time  
- **DATETIME** – contains both date and time  

