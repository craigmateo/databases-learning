# Module 11: Normalization

### Introduction

In this module, you will be introduced to the concepts of Normalization. You will learn about the first, second, and third normal forms. You will also learn about the special case of the third normal form called **BCNF** (Boyce-Codd Normal Form).

This module discusses removing redundancy in data. By the end of this module, you should be able to design a database without redundancy and learn about denormalization.

---

### Learning Outcomes

By the end of this module, you should be able to complete the following:

- Learn different normalization techniques.
- Justify controlled de-normalization.
- Transform un-normalized data to Boyce-Codd Normal Form using principles of partial functional dependency, transitive dependency, and functional dependency.

---

### Key Terms and Concepts

| Key Term or Concept | Definition |
| ------------------- | ---------- |
| **Normalization**   | The process to identify and reduce redundancy in a table. |
| **Normal Forms**    | - First Normal Form (1NF) <br> - Second Normal Form (2NF) <br> - Third Normal Form (3NF) <br> - Boyce-Codd Normal Form (BCNF) |
| **1NF**             | First Normal Form is achieved by ensuring each cell in a table has a single value (avoiding repeating groups). |
| **2NF**             | Second Normal Form is achieved if the relation is in 1NF and there is no partial dependency. |
| **3NF**             | Third Normal Form is achieved if the relation is in 2NF and all transitive dependencies are removed. |
| **BCNF**            | Boyce-Codd Normal Form is a special case of 3NF where every determinant is a candidate key. |

# Normalization

*Watch video: [Basic Concept of Database Normalization - Simple Explanation for Beginners]*

Normalization is the process to identify the amount of redundancy in a table. As discussed in the previous module, normalization can be achieved by functional dependency. Higher normal forms reduce data redundancy.

---

## Normal Forms

The first four normal forms are:

- First Normal Form (1NF)  
- Second Normal Form (2NF)  
- Third Normal Form (3NF)  
- Boyce-Codd Normal Form (BCNF)  

*Read more about [Normalization](#)*

---

## Rules for Normal Forms

- **1NF:** Tables should have no repeating fields, must have a primary key, and be organized in rows.  
- **2NF:** All data in tables with composite primary keys must depend on the whole key (no partial dependency).  
- **3NF:** All data must rely on the primary key, with no transitive dependency.

*More video links covering 1NF, 2NF, 3NF, and BCNF are available [here](#).*

---

## 1NF (First Normal Form)

1NF is achieved by making sure each cell in a table has a single value (avoiding repeating groups).

### Example: Company Details Table (Before 1NF)

| company_id | company_name | employees                           | department  | manager       | projects              |
|------------|--------------|-----------------------------------|-------------|---------------|-----------------------|
| 001        | ABC Corp     | John, Lisa, Mark                  | Sales       | Alice Brown   | Website Revamp, CRM    |

*Problem:* Employees is a repeating group (multiple values in one cell).

### Process to achieve 1NF:

- Create a new table `employees` with `employee_id`, `employee_name`, `employee_marital_status`.
- Identify employees by their `employee_id` (Primary Key).
- Now, the employees table has no repetition and is in 1NF.

### Example: Employees Table (After 1NF)

| employee_id | employee_name | employee_marital_status |
|-------------|---------------|------------------------|
| E101        | John          | Single                 |
| E102        | Lisa          | Married                |
| E103        | Mark          | Single                 |

---

## 2NF (Second Normal Form)

2NF is achieved if the table is already in 1NF and there is no **partial dependency** (i.e., no attribute depends on only part of a composite primary key).

### Example: Employees Table in 1NF

| employee_id | company_id | company_name | project    | manager       |
|-------------|------------|--------------|------------|---------------|
| E101        | 001        | ABC Corp     | Website    | Alice Brown   |

*Problem:* `company_name` depends only on `company_id` (part of composite key), so partial dependency exists.

### Process to achieve 2NF:

- Split the table into two: one for employees and one for company details.
- `company_details` table contains company info and manager.
- `employees` table contains employee info linked by company_id.

### Example: Company Details Table (After 2NF)

| company_id | company_name | manager     |
|------------|--------------|-------------|
| 001        | ABC Corp     | Alice Brown |

### Example: Employees Table (After 2NF)

| employee_id | company_id | project     |
|-------------|------------|-------------|
| E101        | 001        | Website     |

*Problem with 2NF:* If a new project is added, the manager must also be added to the `company_details` table. Deleting a manager may also delete project info (anomaly).

---

## 3NF (Third Normal Form)

3NF is achieved if the table is in 2NF and **all transitive dependencies** are removed.

### Process to achieve 3NF:

- Remove attributes that depend on non-key attributes.
- Create new tables accordingly.

### Example:

- Separate the project and manager info into their own tables.
- Now, no inappropriate dependencies exist.

---

## BCNF (Boyce-Codd Normal Form) and De-normalization

BCNF is a special case of 3NF. A table can have anomalies when it has more than one candidate key.

- A table is in BCNF if **every determinant is a candidate key**.
- De-normalization may be applied intentionally to improve performance in some cases.

*Read more in Chapter 8 (Types of Keys), Chapter 12 (Normalization), and about [De-normalization](#).*

---

*Watch video: [Normalization - 1NF, 2NF, 3NF and 4NF](#)*

