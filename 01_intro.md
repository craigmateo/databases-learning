# Module 1: Need for Databases

## File-Based System vs Database Approach

### File-Based System (Decades Ago)
- Data stored separately by each department.
- Example: In a university:
  - Registrar’s Office stores fee payment files per student.
  - Professors store grade files per student.
  - Co-op department stores placement files per student.

#### Disadvantages of File-Based System
- **Data Redundancy:** Same information stored in multiple places.
- **Data Isolation:** Data scattered in various files, making retrieval difficult.
- **Integrity Problems:** No assurance that data is correct and consistent.
- **Security Problems:** Hard to define roles and access privileges.
- **Concurrency Access:** Multiple users cannot access the same data simultaneously.

### Database Approach
- A database is a shared collection of related data supporting organizational activities.
- Data is defined once and accessed by multiple users.
- Data organized into tables with rows and columns:
  - **Row:** A record containing multiple columns.
  - **Column:** Holds a specific data piece, with a name and datatype.

## Database Management System (DBMS)

A **Database Management System (DBMS)** is a collection of programs that allows users to create, maintain, and control access to databases. Its primary goal is to provide a convenient and efficient environment for storing and retrieving information.

### Examples of DBMS

- **Commercial:**
  - Oracle
  - DB2
  - SQL Server / Sybase
  - dBase / Access
- **Open Source:**
  - MySQL
  - PostgreSQL
  - Others (Firebird, SQLite, etc.)

With a DBMS, a single system can be accessed by different departments within an organization—such as various departments in a university—facilitating shared data management.

## Benefits of Databases

Using a database offers many advantages over a traditional file-based system:

- **Sharing of Data:**  
  Users can access and share data instantly based on their organizational roles.

- **Reducing Data Inconsistency:**  
  Data is stored in a single location, preventing multiple copies. Changes by one user are immediately reflected for all.

- **Data Integrity:**  
  Databases maintain data consistency by preventing duplication.

- **Privacy:**  
  Role-based access ensures users only see data relevant to their role. For example, a professor can access students in their course but not others.

- **Data Security:**  
  Security levels can be defined as needed, with user authentication through usernames and passwords.

- **Backup and Recovery:**  
  DBMS can create backups automatically or manually, enabling data restoration after crashes.

