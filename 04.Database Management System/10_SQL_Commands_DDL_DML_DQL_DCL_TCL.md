# Topic 10 – SQL Commands (DDL, DML, DQL, DCL, TCL)

## 1. Introduction

SQL commands wo instructions hain jinki help se hum database aur uske data ko manage karte hain.

SQL commands ko commonly 5 categories mein divide kiya jata hai:

1. DDL – Data Definition Language
2. DML – Data Manipulation Language
3. DQL – Data Query Language
4. DCL – Data Control Language
5. TCL – Transaction Control Language

```text
              SQL COMMANDS
                   |
     +-------------+-------------+
     |             |             |
    DDL           DML           DQL
     |             |             |
   DCL             +-------------+
     |
    TCL
```

---

## 2. DDL – Data Definition Language

DDL ka full form **Data Definition Language** hai.

DDL commands ka use database objects ka structure create, modify aur delete karne ke liye hota hai.

Main DDL commands:

- CREATE
- ALTER
- DROP
- TRUNCATE
- RENAME

### A. CREATE

Database ya table create karta hai.

```sql
CREATE DATABASE college_db;
```

Table create:

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);
```

### B. ALTER

Existing table ka structure change karta hai.

Column add:

```sql
ALTER TABLE students
ADD city VARCHAR(50);
```

Column modify (MySQL):

```sql
ALTER TABLE students
MODIFY name VARCHAR(100);
```

Column delete:

```sql
ALTER TABLE students
DROP COLUMN city;
```

**Note:** ALTER syntax database system ke according different ho sakta hai.

### C. DROP

Database ya table ko completely remove karta hai.

```sql
DROP TABLE students;
```

Database delete:

```sql
DROP DATABASE college_db;
```

**Warning:** DROP table ke structure aur uske stored records dono remove karta hai.

### D. TRUNCATE

Table ke saare records remove karta hai, lekin table ka structure bana rehta hai.

```sql
TRUNCATE TABLE students;
```

### E. RENAME

Table ka naam change karta hai.

MySQL example:

```sql
RENAME TABLE students TO learners;
```

---

## 3. DML – Data Manipulation Language

DML ka full form **Data Manipulation Language** hai.

DML commands ka use table ke records insert, update aur delete karne ke liye hota hai.

Main commands:

- INSERT
- UPDATE
- DELETE

### A. INSERT

New records insert karta hai.

```sql
INSERT INTO students (id, name, age)
VALUES (1, 'Rahul', 21);
```

Multiple records:

```sql
INSERT INTO students (id, name, age)
VALUES
(2, 'Aman', 22),
(3, 'Priya', 20);
```

### B. UPDATE

Existing records modify karta hai.

```sql
UPDATE students
SET age = 23
WHERE id = 2;
```

Multiple columns:

```sql
UPDATE students
SET age = 24, name = 'Aman Kumar'
WHERE id = 2;
```

**Important:** WHERE ke bina UPDATE karne par saare records update ho sakte hain.

### C. DELETE

Records delete karta hai.

```sql
DELETE FROM students
WHERE id = 3;
```

Saare records delete:

```sql
DELETE FROM students;
```

**Important:** WHERE ke bina DELETE karne par table ke saare records delete ho sakte hain.

---

## 4. DQL – Data Query Language

DQL ka full form **Data Query Language** hai.

DQL ka use database se data retrieve karne ke liye hota hai.

Main command:

- SELECT

### A. All Records

```sql
SELECT * FROM students;
```

### B. Specific Columns

```sql
SELECT name, age
FROM students;
```

### C. WHERE

```sql
SELECT *
FROM students
WHERE age > 20;
```

### D. ORDER BY

```sql
SELECT *
FROM students
ORDER BY age DESC;
```

### E. DISTINCT

```sql
SELECT DISTINCT age
FROM students;
```

### F. LIMIT (MySQL / PostgreSQL)

```sql
SELECT *
FROM students
LIMIT 5;
```

**Note:** Kuch educational sources SELECT ko broadly DML mein bhi classify karte hain. DQL ek commonly used educational category hai.

---

## 5. DCL – Data Control Language

DCL ka full form **Data Control Language** hai.

DCL ka use database users ki permissions aur access control karne ke liye hota hai.

Main commands:

- GRANT
- REVOKE

### A. GRANT

User ko permission dene ke liye.

```sql
GRANT SELECT
ON college_db.students
TO user1;
```

Is example mein user1 ko students table par SELECT permission di ja rahi hai.

### B. REVOKE

User se permission remove karne ke liye.

```sql
REVOKE SELECT
ON college_db.students
FROM user1;
```

**Note:** User creation aur permission syntax DBMS-specific hota hai. Exact syntax database system aur privileges par depend karega.

---

## 6. TCL – Transaction Control Language

TCL ka full form **Transaction Control Language** hai.

TCL commands ka use transactions ko manage karne ke liye hota hai.

Main commands:

- COMMIT
- ROLLBACK
- SAVEPOINT

### A. COMMIT

Transaction ke changes permanently save karta hai.

```sql
START TRANSACTION;

UPDATE students
SET age = 22
WHERE id = 1;

COMMIT;
```

### B. ROLLBACK

Uncommitted transaction ke changes cancel karta hai.

```sql
START TRANSACTION;

UPDATE students
SET age = 25
WHERE id = 1;

ROLLBACK;
```

Rollback ke baad transaction ke uncommitted changes cancel ho jayenge.

### C. SAVEPOINT

Transaction ke andar ek checkpoint create karta hai.

```sql
START TRANSACTION;

UPDATE students
SET age = 22
WHERE id = 1;

SAVEPOINT sp1;

UPDATE students
SET age = 25
WHERE id = 2;

ROLLBACK TO SAVEPOINT sp1;

COMMIT;
```

Is example mein:

- First update retain hogi.
- Second update rollback hogi.
- COMMIT first update save karega.

**Note:** Transaction syntax aur behavior DBMS ke according vary kar sakta hai.

---

## 7. DDL vs DML vs DQL vs DCL vs TCL

| Category | Full Form                    | Purpose             | Commands                      |
| -------- | ---------------------------- | ------------------- | ----------------------------- |
| DDL      | Data Definition Language     | Structure manage    | CREATE, ALTER, DROP, TRUNCATE |
| DML      | Data Manipulation Language   | Records modify      | INSERT, UPDATE, DELETE        |
| DQL      | Data Query Language          | Records retrieve    | SELECT                        |
| DCL      | Data Control Language        | Permissions manage  | GRANT, REVOKE                 |
| TCL      | Transaction Control Language | Transactions manage | COMMIT, ROLLBACK, SAVEPOINT   |

### Easy Trick

- DDL = Structure
- DML = Data change
- DQL = Data read
- DCL = Permission
- TCL = Transaction

---

## 8. DROP vs TRUNCATE vs DELETE

Ye bahut important interview question hai.

| Feature            | DELETE         | TRUNCATE           | DROP                 |
| ------------------ | -------------- | ------------------ | -------------------- |
| Purpose            | Records delete | All records remove | Table remove         |
| WHERE              | Supported      | Not supported      | Not supported        |
| Structure          | Remains        | Remains            | Removed              |
| Selective deletion | Yes            | No                 | No                   |
| Command type       | DML (commonly) | DDL (commonly)     | DDL                  |
| All rows           | Possible       | Yes                | Table itself removed |

### Examples

```sql
DELETE FROM students
WHERE id = 1;
```

```sql
TRUNCATE TABLE students;
```

```sql
DROP TABLE students;
```

**Important:** TRUNCATE aur DROP ke rollback behavior ko universally same mat samajhna. Ye DBMS aur transaction settings par depend karta hai.

---

## 9. DELETE vs UPDATE

| DELETE                                          | UPDATE                                          |
| ----------------------------------------------- | ----------------------------------------------- |
| Records remove karta hai                        | Existing records modify karta hai               |
| DELETE FROM use hota hai                        | UPDATE use hota hai                             |
| WHERE optional hai                              | WHERE optional hai                              |
| WHERE na ho to all records delete ho sakte hain | WHERE na ho to all records update ho sakte hain |

---

## 10. Practical Example – All SQL Categories

Assume database mein `students` table hai.

### DDL – Table Create

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    marks INT
);
```

### DML – Insert Record

```sql
INSERT INTO students
VALUES (1, 'Rahul', 85);
```

### DQL – Read Record

```sql
SELECT * FROM students;
```

### DML – Update Record

```sql
UPDATE students
SET marks = 95
WHERE id = 1;
```

### DCL – Permission

```sql
GRANT SELECT
ON college_db.students
TO user1;
```

### TCL – Save Transaction

```sql
START TRANSACTION;

UPDATE students
SET marks = 90
WHERE id = 1;

COMMIT;
```

---

## 11. Common Mistakes

1. DELETE aur DROP ko same samajhna.
2. TRUNCATE ko table structure delete karne wali command samajhna.
3. UPDATE mein WHERE bhool jana.
4. DELETE mein WHERE bhool jana.
5. SELECT ko har source mein exclusively DML ya DQL samajhna.
6. Har DBMS mein same ALTER syntax assume karna.
7. ROLLBACK ko already committed changes undo karne ka universal method samajhna.
8. GRANT aur REVOKE ka purpose confuse karna.

---

## 12. Interview Questions

**Q1. SQL commands ki five categories kaun si hain?**

DDL, DML, DQL, DCL aur TCL.

**Q2. DDL ka purpose kya hai?**

Database objects ka structure create aur modify karna.

**Q3. DML ka purpose kya hai?**

Table ke records insert, update aur delete karna.

**Q4. DQL mein kaunsi command use hoti hai?**

SELECT.

**Q5. DCL ka purpose kya hai?**

Database permissions control karna.

**Q6. TCL ka purpose kya hai?**

Transactions manage karna.

**Q7. DROP aur TRUNCATE mein difference?**

DROP table structure aur records remove karta hai; TRUNCATE records remove karta hai aur structure retain karta hai.

**Q8. DELETE aur TRUNCATE mein difference?**

DELETE selected records remove kar sakta hai using WHERE; TRUNCATE generally table ke saare records remove karta hai.

**Q9. COMMIT kya karta hai?**

Transaction ke changes save karta hai.

**Q10. ROLLBACK kya karta hai?**

Current transaction ke uncommitted changes cancel karta hai.

**Q11. SAVEPOINT kya hai?**

Transaction ke andar ek checkpoint jahan tak rollback kiya ja sakta hai.

**Q12. GRANT aur REVOKE mein difference?**

GRANT permission deta hai, REVOKE permission remove karta hai.

---

## 13. Practical Tasks

`students` table par ye operations khud perform karo:

1. `college_db` database create karo.
2. `students` table create karo.
3. 5 records insert karo.
4. Saare records retrieve karo.
5. Ek student ke marks update karo.
6. Ek student ka record delete karo.
7. Table mein `city` column add karo.
8. Table ka naam `learners` rakho.
9. Transaction start karke update karo aur rollback karo.
10. Ek user ko SELECT permission grant karne ki query likho.

---

## 14. Quick Revision

- DDL = Structure management.
- DML = Data modification.
- DQL = Data retrieval.
- DCL = Access permissions.
- TCL = Transaction management.
- CREATE = New database object.
- ALTER = Existing structure modify.
- DROP = Object remove.
- TRUNCATE = All rows remove.
- INSERT = New record.
- UPDATE = Existing record modify.
- DELETE = Record remove.
- SELECT = Data retrieve.
- GRANT = Permission provide.
- REVOKE = Permission remove.
- COMMIT = Changes save.
- ROLLBACK = Uncommitted changes cancel.
- SAVEPOINT = Transaction checkpoint.

---

## 15. MCQ Test

**Q1. CREATE command kis category mein aati hai?**

A. DML  
B. DDL  
C. DQL  
D. TCL

**Q2. Data retrieve karne ke liye kaunsi command use hoti hai?**

A. SELECT  
B. DELETE  
C. DROP  
D. UPDATE

**Q3. User ko permission dene ke liye kya use hota hai?**

A. REVOKE  
B. ROLLBACK  
C. GRANT  
D. ALTER

**Q4. Transaction save karne ke liye kya use hota hai?**

A. DROP  
B. COMMIT  
C. DELETE  
D. TRUNCATE

**Q5. Table ke saare records remove karne ke liye kaunsi command use hoti hai?**

A. SELECT  
B. GRANT  
C. TRUNCATE  
D. ALTER

**Q6. Existing table mein column add karne ke liye kya use hota hai?**

A. ALTER  
B. DROP  
C. COMMIT  
D. SELECT

**Q7. Uncommitted transaction changes cancel karne ke liye kya use hota hai?**

A. GRANT  
B. ROLLBACK  
C. CREATE  
D. INSERT

**Q8. Permission remove karne ke liye kya use hota hai?**

A. GRANT  
B. COMMIT  
C. REVOKE  
D. SAVEPOINT

**Q9. Selected records delete karne ke liye kya use hota hai?**

A. DELETE with WHERE  
B. DROP  
C. TRUNCATE  
D. CREATE

**Q10. Transaction ke andar checkpoint create karne ke liye kya use hota hai?**

A. ALTER  
B. SAVEPOINT  
C. GRANT  
D. SELECT

### Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | A      |
| Q3       | C      |
| Q4       | B      |
| Q5       | C      |
| Q6       | A      |
| Q7       | B      |
| Q8       | C      |
| Q9       | A      |
| Q10      | B      |

---

# Topic 10 Completed

**Next Topic 11:** SQL Operators and Functions

Ismein Arithmetic, Comparison, Logical, Special Operators aur SQL Aggregate/String/Numeric/Date Functions cover honge.
