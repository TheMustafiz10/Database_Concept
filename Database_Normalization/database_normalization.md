

# Database Normalization

## Introduction

**Database Normalization** is the process of organizing data in a database to reduce data redundancy (duplicate data) and improve data consistency and integrity.

It divides large tables into smaller related tables and connects them using keys.

## Why is Database Normalization Important?

- Reduces duplicate data.
- Prevents data insertion, update, and deletion anomalies.
- Improves data consistency.
- Makes databases easier to maintain.
- Organizes data efficiently.

---

# Types of Database Normalization

There are several normal forms:

## 1. First Normal Form (1NF)

A table is in 1NF if:

- Each column contains atomic (single) values.
- There are no multiple values in a single cell.
- Each row is unique.

### Example (Not in 1NF)

| Student_ID | Name | Subjects |
|------------|------|----------|
| 101 | Rahim | Math, English |
| 102 | Karim | Science, ICT |

### Converted into 1NF

| Student_ID | Name | Subject |
|------------|------|---------|
| 101 | Rahim | Math |
| 101 | Rahim | English |
| 102 | Karim | Science |
| 102 | Karim | ICT |

---

## 2. Second Normal Form (2NF)

A table is in 2NF if:

- It is already in 1NF.
- Every non-key attribute depends on the whole primary key, not just part of it.

This removes **Partial Dependency**.

### Example

| Student_ID | Course_ID | Student_Name | Course_Name |
|------------|-----------|--------------|-------------|
| 101 | C01 | Rahim | Database |
| 102 | C02 | Karim | Networking |

Here, the combined primary key is:

`Student_ID + Course_ID`

### Convert into 2NF

**Student Table**

| Student_ID (PK) | Student_Name |
|-----------------|--------------|
| 101 | Rahim |
| 102 | Karim |

**Course Table**

| Course_ID (PK) | Course_Name |
|----------------|-------------|
| C01 | Database |
| C02 | Networking |

**Enrollment Table**

| Student_ID (FK) | Course_ID (FK) |
|-----------------|----------------|
| 101 | C01 |
| 102 | C02 |

---

## 3. Third Normal Form (3NF)

A table is in 3NF if:

- It is already in 2NF.
- There is no transitive dependency.
- Non-key attributes depend only on the primary key.

This removes **Transitive Dependency**.

### Example (Not in 3NF)

| Student_ID | Student_Name | Dept_ID | Dept_Name |
|------------|--------------|---------|-----------|
| 101 | Rahim | D01 | CSE |
| 102 | Karim | D02 | EEE |

Here:

- Student_ID → Dept_ID
- Dept_ID → Dept_Name

### Convert into 3NF

**Student Table**

| Student_ID (PK) | Student_Name | Dept_ID (FK) |
|-----------------|--------------|--------------|
| 101 | Rahim | D01 |
| 102 | Karim | D02 |

**Department Table**

| Dept_ID (PK) | Dept_Name |
|--------------|-----------|
| D01 | CSE |
| D02 | EEE |

---

## 4. Boyce-Codd Normal Form (BCNF)

BCNF is a stronger version of 3NF.

A table is in BCNF if:

- It is already in 3NF.
- Every determinant must be a candidate key.

**In simple words:** Every attribute that determines another attribute must be a candidate key.

---

## 5. Fourth Normal Form (4NF)

A table is in 4NF if:

- It is already in BCNF.
- It has no non-trivial multivalued dependencies unless the determinant is a superkey.

---

## 6. Fifth Normal Form (5NF)

A table is in 5NF if:

- It is already in 4NF.
- It has no non-trivial join dependencies that cause redundancy.

---

# Summary of Normal Forms

| Normal Form | Main Condition |
|-------------|----------------|
| 1NF | Atomic values |
| 2NF | No partial dependency |
| 3NF | No transitive dependency |
| BCNF | Every determinant is a candidate key |
| 4NF | No problematic multivalued dependency |
| 5NF | No problematic join dependency |

---

# Common Database Anomalies

Normalization helps prevent three major problems:

### 1. Insertion Anomaly

Difficulty inserting data without other unrelated data.

### 2. Update Anomaly

The same information must be updated in multiple places.

### 3. Deletion Anomaly

Deleting one record accidentally removes other important information.

---

# Easy Way to Remember

| Normal Form | Key Concept |
|-------------|-------------|
| 1NF | Atomic Values |
| 2NF | No Partial Dependency |
| 3NF | No Transitive Dependency |
| BCNF | Every Determinant is a Candidate Key |
| 4NF | No Problematic Multivalued Dependency |
| 5NF | No Problematic Join Dependency |

---

# Exam Tips

Remember these three important concepts:

- **1NF = Atomic Values**
- **2NF = Full Functional Dependency**
- **3NF = No Transitive Dependency**

---

# Conclusion

Database normalization is an essential concept in database management systems (DBMS). It helps organize data efficiently, minimize redundancy, maintain data integrity, and prevent database anomalies.

Understanding 1NF, 2NF, 3NF, BCNF, 4NF, and 5NF is important for designing a well-structured relational database.

---

**Happy Learning!**

