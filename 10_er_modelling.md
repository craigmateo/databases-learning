# Module 10: ER Modelling

## Introduction

In this module, you will be introduced to the anomalies in a database and learn about good relational database design. You will learn about insertion, update, and deletion anomalies.

This module also discusses functional dependency. By the end of this module, you should be able to identify different anomalies that could occur in a database.

---

## Learning Outcomes

By the end of this module, you should be able to:

- Learn about Relational Design and Redundancy
- Determine the storage and use of metadata in a DBMS
- Understand functional dependency

---

## Key Terms and Concepts

| Key Term or Concept    | Definition                                                                                          |
|-----------------------|---------------------------------------------------------------------------------------------------|
| **Relational Design**  | The key for a good relational design for a database is a design with no data redundancy.          |
| **Redundancy**         | Data Redundancy is the repetition of the same data in a database.                                 |
| **Three different anomalies** | Insertion Anomaly, Update Anomaly, Deletion Anomaly                                         |
| **Insertion Anomaly**  | Occurs when a user inserts data that is not consistent with the rest of the data.                  |
| **Update Anomaly**     | Occurs when a user updates data incorrectly or incompletely.                                      |
| **Deletion Anomaly**   | Occurs when deleting a record also deletes important information that was not intended to be lost.|
| **Functional Dependency** | Normalizing the data can be achieved by the concept of Functional Dependencies which separates each table based on attributes. |

## Relational Design and Redundancy

The key for a good relational design for a database is a design with **no data redundancy**.  
Data redundancy means the repetition of the same data in a database.

---

### Example (Fig. 1)

Fig. 1 displays different details about students registered in a college. Although student details like name, age, and phone number are unique, the **student program** has redundant data. This redundancy affects the performance and integrity of the database.

---

### Common Anomalies Caused by Redundancy

There are three anomalies that can occur due to redundant data:

- **Insertion Anomaly**  
- **Update Anomaly**  
- **Deletion Anomaly**

---

### Insertion Anomaly

Insertion anomaly occurs when inserting data forces the entry of unnecessary or inconsistent data.

**Example:**  
In Fig. 1, if a new program called *Technical Writing* needs to be added but no students have registered for it yet, a student record must still be added to maintain consistency — even though no student actually exists for that program.

---

### Update Anomaly

Update anomaly happens when updating a piece of data requires changes in multiple records, and some records are not updated properly, leading to inconsistency.

**Example:**  
If the program name *Computer Programmer* changes to *Computer Systems* (Fig. 1), every record containing *Computer Programmer* must be updated. Failure to do so will cause data inconsistency.

---

### Deletion Anomaly

Deletion anomaly occurs when deleting a record also removes data that should not be deleted.

**Example:**  
If the student *Amanda* leaves the college and her record is deleted, it may also remove the program name if no other students are registered in that program, resulting in loss of valid program information.

## Avoiding Anomalies and Functional Dependency

### Avoiding Anomalies

Anomalies can be avoided by **separating the table** and **normalizing the data**.

---

#### Examples (Fig. 2 and Fig. 3)

- **Avoiding Insertion Anomaly:**  
  The Student table is divided into two tables —  
  - Fig. 2: Student Table  
  - Fig. 3: Program Table  

  This separation prevents insertion anomaly. For example, the *Technical Writing* program can now be inserted into the Program table **without adding any new student**.

- **Avoiding Update Anomaly:**  
  If the program name *Computer Programmer* changes to *Computer Systems*, only a single update is required in the Program table. The change will then reflect correctly without the need to update multiple student records.

- **Avoiding Deletion Anomaly:**  
  If Amanda is deleted from the Student table, her record is removed without affecting the existence of the program in the Program table.

---

### Functional Dependency

Normalizing the data can be achieved through the concept of **Functional Dependency**, which involves separating each table based on attributes that depend on one another.

In Fig. 1, the student details and the program they are registered in were all in one table. Since the **Program Name** represents a different entity than the student details, it can be separated into its own table to reduce redundancy and anomalies.

