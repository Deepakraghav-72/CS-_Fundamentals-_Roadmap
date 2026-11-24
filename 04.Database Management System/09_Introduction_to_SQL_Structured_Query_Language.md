# Topic 09 – Introduction to SQL (Structured Query Language)

## 1. What is SQL?

**SQL ka full form Structured Query Language hai.**

SQL ek standard language hai jiska use relational databases ke saath communicate karne ke liye hota hai.

SQL ki help se hum database mein:

- Data store kar sakte hain.
- Data retrieve kar sakte hain.
- Existing data update kar sakte hain.
- Data delete kar sakte hain.
- Tables aur database structure create kar sakte hain.
- Users aur permissions manage kar sakte hain.
- Transactions control kar sakte hain.

### Simple Definition

SQL ek database language hai jiska use relational database mein data ko create, read, update aur delete karne ke liye kiya jata hai.

### Example

```sql
SELECT * FROM students;
```

Is query ka meaning hai:

`students` table ke saare columns aur records ko retrieve karo.

---

## 2. SQL ka History

SQL ka development IBM ke researchers ne relational database model par kaam karte hue kiya tha.

Important points:

1. 1970 mein Edgar F. Codd ne Relational Model introduce kiya.
2. IBM ke researchers ne relational database ke liye ek language develop ki.
3. Is language ka original naam SEQUEL tha.
4. Baad mein iska naam SQL ho gaya.
5. ANSI ne 1986 mein SQL standard adopt kiya.
6. ISO ne 1987 mein SQL standard adopt kiya.

**Important:** SQL ka standard exist karta hai, lekin different database systems mein SQL ke syntax aur features mein differences ho sakte hain.

---

## 3. SQL, Database, DBMS aur RDBMS mein Difference

In chaar terms ko confuse mat karna.

| Term     | Meaning                                         |
| -------- | ----------------------------------------------- |
| Database | Organized collection of data                    |
| DBMS     | Software jo database manage karta hai           |
| RDBMS    | Relational model par based DBMS                 |
| SQL      | Database ke saath communicate karne ki language |

### Example

- Database: Students ka stored data
- DBMS: Database manage karne wala software
- RDBMS: MySQL, PostgreSQL, Oracle
- SQL: In databases ko instructions dene ki language

**Yaad rakho:**

SQL ek language hai, database software nahi.

---

## 4. SQL ki Need Kyu Hoti Hai?

Imagine karo ek college ke paas 10,000 students ka data hai.

Humein kuch questions ke answers chahiye:

- Saare students ka data kya hai?
- Sirf BCA students kaun hain?
- Kis student ke marks sabse zyada hain?
- Kisi student ka phone number update kaise karein?
- Kisi particular student ka record delete kaise karein?

Aise operations SQL ki help se easily perform kiye ja sakte hain.

### SQL ke Main Uses

1. Database create karna.
2. Tables create karna.
3. Data insert karna.
4. Data retrieve karna.
5. Data update karna.
6. Data delete karna.
7. Data filter aur sort karna.
8. Database permissions manage karna.
9. Transactions manage karna.

---

## 5. SQL ki Important Characteristics

### 1. Declarative Language

SQL ek declarative language hai.

Iska matlab hai ki hum database ko batate hain ki **kya result chahiye**, generally ye nahi batate ki database us result ko internally kaise calculate kare.

Example:

```sql
SELECT * FROM students
WHERE marks > 80;
```

Humne database ko bataya ki 80 se zyada marks wale students chahiye.

Database khud decide karta hai ki query execute kaise karni hai.

### 2. Standardized Language

SQL ka ek international standard hai.

Lekin MySQL, PostgreSQL, Oracle aur SQL Server mein kuch syntax differences hote hain.

### 3. Set-Based Language

SQL generally ek saath multiple records par operations perform kar sakti hai.

Example:

```sql
UPDATE students
SET city = 'Delhi'
WHERE city = 'New Delhi';
```

Ye query condition match karne wale multiple records update kar sakti hai.

### 4. Easy to Understand

SQL commands generally English-like keywords use karti hain:

- SELECT
- INSERT
- UPDATE
- DELETE
- CREATE

### 5. Database Management

SQL ka use data ke saath-saath database structure, permissions aur transactions manage karne ke liye bhi hota hai.

---

## 6. SQL vs MySQL

Ye interview ka important question hai.

**SQL:** Ek language hai.

**MySQL:** Ek relational database management system (RDBMS) hai jo SQL ka use karta hai.

| SQL                                  | MySQL                         |
| ------------------------------------ | ----------------------------- |
| Database language                    | RDBMS software                |
| Instructions likhne ke kaam aati hai | Database manage karta hai     |
| Standardized language                | Specific database product     |
| Database se communicate karti hai    | SQL queries execute karta hai |

### Other SQL-Based Database Systems

1. MySQL
2. PostgreSQL
3. Oracle Database
4. Microsoft SQL Server
5. SQLite

In sab mein SQL use hoti hai, lekin har system ka SQL dialect aur supported features thode different ho sakte hain.

---

## 7. SQL Database ke Basic Terms

SQL samajhne se pehle kuch basic terms samajh lo.

### 1. Database

Related data ka organized collection.

Example: `college_db`

### 2. Table

Database ke andar data rows aur columns ke form mein store hota hai.

Example: `students`

### 3. Row / Record / Tuple

Table mein ek complete record ko row kehte hain.

Example:

| id  | name  | age |
| --- | ----- | --- |
| 1   | Rahul | 21  |

Ye ek row hai.

### 4. Column / Field / Attribute

Table mein kisi particular type ki information ko column kehte hain.

Example:

- id
- name
- age

### 5. Schema

Database ya table ka logical structure schema kehlata hai.

Example:

```text
students
---------
id
name
age
city
```

### 6. NULL

NULL ka matlab hai value missing, unknown ya unavailable hai.

NULL ka matlab zero ya empty string nahi hota.

---

## 8. Example: Students Table

Hum ek simple students table imagine karte hain.

| id  | name  | age | city   | marks |
| --- | ----- | --: | ------ | ----: |
| 1   | Rahul |  21 | Delhi  |    85 |
| 2   | Aman  |  22 | Meerut |    90 |
| 3   | Priya |  20 | Noida  |    95 |
| 4   | Neha  |  21 | Delhi  |    75 |

Is table mein:

- Table Name = students
- Total Columns = 5
- Total Rows = 4
- Column names = id, name, age, city, marks

---

## 9. SQL Query ka Basic Structure

SQL mein likhi gayi instruction ko SQL statement ya query kehte hain.

Example:

```sql
SELECT name, marks
FROM students
WHERE marks > 80
ORDER BY marks DESC;
```

Is query ko samjho:

| Keyword  | Meaning                          |
| -------- | -------------------------------- |
| SELECT   | Kaunse columns chahiye           |
| FROM     | Kis table se data chahiye        |
| WHERE    | Kaunsi condition apply karni hai |
| ORDER BY | Result ko kaise sort karna hai   |
| DESC     | Descending order                 |

### SQL Statement Terminator

SQL statements ke end mein generally semicolon `;` use kiya jata hai.

```sql
SELECT * FROM students;
```

Kuch tools single statement ke end mein semicolon ke bina bhi query accept kar lete hain, lekin semicolon use karna good practice hai.

---

## 10. SQL Keywords aur Case Sensitivity

SQL keywords generally case-insensitive hote hain.

Matlab ye queries equivalent hain:

```sql
SELECT * FROM students;
```

```sql
select * from students;
```

```sql
Select * From students;
```

Lekin database identifiers (table/column names) ki case sensitivity DBMS aur configuration par depend kar sakti hai.

**Best Practice:**

- SQL keywords uppercase mein likho.
- Table aur column names consistent style mein rakho.
- Queries ko readable format mein likho.

Example:

```sql
SELECT name, age
FROM students
WHERE age > 20;
```

---

## 11. Basic SQL Data Types

Data type batata hai ki kisi column mein kis type ki value store hogi.

| Data Type         | Use                        | Example     |
| ----------------- | -------------------------- | ----------- |
| INT / INTEGER     | Whole numbers              | 10, 25      |
| DECIMAL / NUMERIC | Exact decimal values       | 99.50       |
| FLOAT / REAL      | Approximate decimal values | 12.45       |
| CHAR(n)           | Fixed-length text          | 'ABC'       |
| VARCHAR(n)        | Variable-length text       | 'Rahul'     |
| TEXT              | Long text                  | Description |
| DATE              | Date                       | 2026-11-06  |
| TIME              | Time                       | 10:30:00    |
| BOOLEAN           | True/False                 | TRUE        |
| BLOB / BINARY     | Binary data                | File bytes  |

**Note:** Available data types aur unka exact behavior database system ke according change ho sakta hai.

---

## 12. SQL Database par Kaam Kaise Karti Hai?

Generally SQL ke saath kaam karne ka basic workflow:

1. Database server se connect karna.
2. Database select karna ya create karna.
3. Table create karna.
4. Table mein records insert karna.
5. Required records retrieve karna.
6. Zarurat padne par update ya delete karna.

### Step 1: Database Create Karna

```sql
CREATE DATABASE college_db;
```

Isse `college_db` naam ka database create hoga, agar database system aur permissions allow karte hain.

### Step 2: Database Select Karna

MySQL:

```sql
USE college_db;
```

SQL Server mein bhi `USE` supported hai.

PostgreSQL ke `psql` command-line client mein:

```text
\c college_db
```

**Note:** `\c` PostgreSQL client ka meta-command hai, normal SQL statement nahi.

### Step 3: Table Create Karna

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    city VARCHAR(50),
    marks DECIMAL(5,2)
);
```

Is query se `students` table create hogi.

### Step 4: Data Insert Karna

```sql
INSERT INTO students
(id, name, age, city, marks)
VALUES
(1, 'Rahul', 21, 'Delhi', 85.00);
```

### Step 5: Data Read Karna

```sql
SELECT * FROM students;
```

Ye table ke saare columns retrieve karega.

---

## 13. SELECT Statement

SELECT ka use database se data retrieve karne ke liye hota hai.

### A. Saare Columns Retrieve Karna

```sql
SELECT * FROM students;
```

`*` ka meaning hai all columns.

### B. Specific Columns Retrieve Karna

```sql
SELECT name, marks
FROM students;
```

Sirf name aur marks columns show honge.

### C. DISTINCT Keyword

Duplicate values ko result se remove karne ke liye DISTINCT use hota hai.

```sql
SELECT DISTINCT city
FROM students;
```

Agar Delhi multiple students ka city hai, result mein Delhi ek baar aayega.

### D. Column Alias

Column ko temporary display name dene ke liye alias use karte hain.

```sql
SELECT name AS student_name
FROM students;
```

Result mein column heading `student_name` show hogi.

**Important:** Alias generally query ke result ko label karta hai; original column ka naam permanently change nahi hota.

---

## 14. WHERE Clause

WHERE ka use records ko condition ke according filter karne ke liye hota hai.

### Example 1: Equal To

```sql
SELECT *
FROM students
WHERE city = 'Delhi';
```

Delhi wale students show honge.

### Example 2: Greater Than

```sql
SELECT *
FROM students
WHERE marks > 80;
```

80 se zyada marks wale students show honge.

### Example 3: Less Than

```sql
SELECT *
FROM students
WHERE age < 22;
```

### Example 4: AND

Dono conditions true honi chahiye.

```sql
SELECT *
FROM students
WHERE city = 'Delhi' AND marks > 80;
```

### Example 5: OR

Koi ek condition true ho to record select ho sakta hai.

```sql
SELECT *
FROM students
WHERE city = 'Delhi' OR city = 'Noida';
```

### Example 6: NOT

Condition ko reverse karta hai.

```sql
SELECT *
FROM students
WHERE NOT city = 'Delhi';
```

### Example 7: IN

Multiple possible values check karne ke liye.

```sql
SELECT *
FROM students
WHERE city IN ('Delhi', 'Noida');
```

### Example 8: BETWEEN

Range ke andar values check karne ke liye.

```sql
SELECT *
FROM students
WHERE marks BETWEEN 70 AND 90;
```

BETWEEN generally inclusive hota hai: 70 aur 90 dono included hain.

### Example 9: LIKE

Pattern matching ke liye.

```sql
SELECT *
FROM students
WHERE name LIKE 'R%';
```

`R%` ka meaning hai naam R se start ho.

Common wildcards:

| Wildcard | Meaning                 |
| -------- | ----------------------- |
| %        | Zero ya more characters |
| _        | Exactly one character   |

Example:

```sql
SELECT *
FROM students
WHERE name LIKE '_a%';
```

Ye pattern aise names match kar sakta hai jinka second character `a` ho.

LIKE ki case sensitivity database aur collation par depend kar sakti hai.

### Example 10: IS NULL

NULL values check karne ke liye:

```sql
SELECT *
FROM students
WHERE city IS NULL;
```

NULL check karne ke liye `= NULL` use nahi karna chahiye.

Correct:

```sql
WHERE city IS NULL;
```

Incorrect:

```sql
WHERE city = NULL;
```

---

## 15. ORDER BY Clause

ORDER BY ka use result ko sort karne ke liye hota hai.

### A. Ascending Order

```sql
SELECT *
FROM students
ORDER BY marks ASC;
```

Lowest marks se highest marks.

### B. Descending Order

```sql
SELECT *
FROM students
ORDER BY marks DESC;
```

Highest marks se lowest marks.

### C. Multiple Columns

```sql
SELECT *
FROM students
ORDER BY city ASC, marks DESC;
```

Pehle city ke according sorting hogi. Same city ke records marks ke according descending order mein sort honge.

**Note:** ORDER BY specify nahi karne par result ka order guaranteed nahi hota.

---

## 16. LIMIT Clause

LIMIT ka use result mein records ki maximum number control karne ke liye hota hai.

Example:

```sql
SELECT *
FROM students
LIMIT 3;
```

Maximum 3 rows return hongi.

### Highest Marks Wale 2 Students

```sql
SELECT *
FROM students
ORDER BY marks DESC
LIMIT 2;
```

**Important Dialect Differences:**

| Database                         | Common Syntax           |
| -------------------------------- | ----------------------- |
| MySQL                            | LIMIT 5                 |
| PostgreSQL                       | LIMIT 5                 |
| SQLite                           | LIMIT 5                 |
| SQL Server                       | TOP 5                   |
| Standard SQL / supported systems | FETCH FIRST 5 ROWS ONLY |

SQL Server example:

```sql
SELECT TOP 5 *
FROM students;
```

Standard-style example:

```sql
SELECT *
FROM students
FETCH FIRST 5 ROWS ONLY;
```

Exact support aur syntax DBMS version ke according vary kar sakte hain.

---

## 17. SQL mein Comments

Comments ka use code ko explain karne ke liye hota hai. Database generally comments ko execute nahi karta.

### Single-Line Comment

```sql
-- This query retrieves all students

SELECT * FROM students;
```

### Multi-Line Comment

```sql
/*
This query retrieves
student names and marks
*/

SELECT name, marks
FROM students;
```

---

## 18. CRUD Operations in SQL

CRUD ka full form:

- C = Create
- R = Read
- U = Update
- D = Delete

| CRUD   | Meaning                      | SQL Example |
| ------ | ---------------------------- | ----------- |
| Create | New record insert karna      | INSERT      |
| Read   | Record retrieve karna        | SELECT      |
| Update | Existing record change karna | UPDATE      |
| Delete | Record remove karna          | DELETE      |

### A. CREATE – Insert New Record

```sql
INSERT INTO students
(id, name, age, city, marks)
VALUES
(2, 'Aman', 22, 'Meerut', 90);
```

### B. READ – Retrieve Record

```sql
SELECT *
FROM students;
```

### C. UPDATE – Existing Record Change

```sql
UPDATE students
SET marks = 95
WHERE id = 2;
```

Aman ke marks 95 ho jayenge.

**Warning:** UPDATE mein WHERE clause nahi lagaya to table ke saare records update ho sakte hain.

### D. DELETE – Record Remove

```sql
DELETE FROM students
WHERE id = 2;
```

ID 2 wala record delete ho jayega.

**Warning:** DELETE mein WHERE clause nahi lagaya to table ke saare records delete ho sakte hain.

### Important Difference

`CREATE TABLE` aur CRUD ka `Create` same operation nahi hain.

- `CREATE TABLE` = Table structure create karta hai.
- `INSERT` = Table mein new record create karta hai.

---

## 19. SQL Command Categories – Introduction

SQL commands ko commonly categories mein divide kiya jata hai.

| Category | Full Form                    | Purpose                    |
| -------- | ---------------------------- | -------------------------- |
| DDL      | Data Definition Language     | Structure define karna     |
| DML      | Data Manipulation Language   | Data modify karna          |
| DQL      | Data Query Language          | Data retrieve karna        |
| DCL      | Data Control Language        | Permissions control karna  |
| TCL      | Transaction Control Language | Transactions control karna |

Examples:

- DDL: CREATE, ALTER, DROP
- DML: INSERT, UPDATE, DELETE
- DQL: SELECT
- DCL: GRANT, REVOKE
- TCL: COMMIT, ROLLBACK, SAVEPOINT

**Important:** SELECT ko kai educational classifications mein DQL kaha jata hai, jabki kuch references ise broadly DML mein include karte hain. Is classification ka detailed explanation next topic mein hoga.

---

## 20. SQL Injection – Basic Introduction

SQL Injection ek security vulnerability hai jisme attacker malicious input ke through SQL query ka behavior change karne ki koshish karta hai.

### Unsafe Example

```javascript
const query = "SELECT * FROM users WHERE email = '" + email + "'";
```

Agar untrusted input directly query string mein concatenate kiya jaye, to SQL injection ka risk ho sakta hai.

### Safe Approach: Parameterized Query

Example using a Node.js database driver with placeholder syntax:

```javascript
const result = await db.query("SELECT * FROM users WHERE email = ?", [email]);
```

Placeholder syntax database driver ke according change ho sakti hai.

**Golden Rule:**

User input ko directly SQL query string mein concatenate mat karo. Parameterized queries ya prepared statements use karo.

---

## 21. SQL ka MERN Stack mein Use

MERN Stack ka full form:

- M = MongoDB
- E = Express.js
- R = React.js
- N = Node.js

MERN mein default database MongoDB hota hai, jo document-oriented NoSQL database hai.

Lekin real-world development mein SQL databases bhi use kiye ja sakte hain.

### Typical Application Flow

```text
       USER
        |
        v
   REACT FRONTEND
        |
        v
   EXPRESS / NODE API
        |
        v
   DATABASE DRIVER / ORM
        |
        v
   SQL DATABASE
   (MySQL / PostgreSQL)
```

### Example

1. User React form mein registration details fill karta hai.
2. React API request bhejta hai.
3. Express backend request receive karta hai.
4. Backend input validate karta hai.
5. Database driver parameterized query execute karta hai.
6. Database result return karta hai.
7. Backend response React ko bhejta hai.

**Important Security Point:**

Database credentials aur direct database connection browser/frontend mein expose nahi karne chahiye. Database access trusted backend se control karo.

---

## 22. SQL vs NoSQL – Basic Introduction

| SQL                                  | NoSQL                                                |
| ------------------------------------ | ---------------------------------------------------- |
| Relational databases ke liye         | Multiple non-relational data models                  |
| Tables, rows, columns                | Documents, key-value, graphs, etc.                   |
| Relationships commonly use hoti hain | Data modeling approach database par depend karti hai |
| SQL language use hoti hai            | Query methods database-specific ho sakte hain        |
| MySQL, PostgreSQL                    | MongoDB, Redis, Neo4j                                |

SQL vs NoSQL ka detailed comparison Topic 21 mein cover hoga.

---

## 23. Complete Practical Example

Ab ek complete example dekhte hain.

### Step 1: Database Create

```sql
CREATE DATABASE college_db;
```

### Step 2: Database Select (MySQL)

```sql
USE college_db;
```

### Step 3: Table Create

```sql
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT,
    city VARCHAR(50),
    marks DECIMAL(5,2)
);
```

### Step 4: Multiple Records Insert

```sql
INSERT INTO students
(id, name, age, city, marks)
VALUES
(1, 'Rahul', 21, 'Delhi', 85.00),
(2, 'Aman', 22, 'Meerut', 90.00),
(3, 'Priya', 20, 'Noida', 95.00),
(4, 'Neha', 21, 'Delhi', 75.00),
(5, 'Rohit', 23, 'Meerut', 88.00);
```

### Step 5: All Records Show

```sql
SELECT *
FROM students;
```

### Step 6: Specific Columns Show

```sql
SELECT name, marks
FROM students;
```

### Step 7: Marks Greater Than 80

```sql
SELECT *
FROM students
WHERE marks > 80;
```

### Step 8: Delhi Students

```sql
SELECT *
FROM students
WHERE city = 'Delhi';
```

### Step 9: Highest Marks First

```sql
SELECT *
FROM students
ORDER BY marks DESC;
```

### Step 10: Top 3 Students (MySQL)

```sql
SELECT *
FROM students
ORDER BY marks DESC
LIMIT 3;
```

### Step 11: Update Marks

```sql
UPDATE students
SET marks = 92
WHERE id = 2;
```

### Step 12: Delete a Record

```sql
DELETE FROM students
WHERE id = 5;
```

---

## 24. Common Mistakes

| Mistake                                   | Correct Approach                                    |
| ----------------------------------------- | --------------------------------------------------- |
| SQL ko database samajhna                  | SQL ek language hai                                 |
| MySQL ko SQL samajhna                     | MySQL ek RDBMS product hai                          |
| `= NULL` use karna                        | `IS NULL` use karo                                  |
| UPDATE mein WHERE bhool jana              | Intended rows ko condition se target karo           |
| DELETE mein WHERE bhool jana              | Delete se pehle condition verify karo               |
| `SELECT *` har jagah use karna            | Required columns select karo                        |
| ORDER BY ke bina fixed order assume karna | Explicit sorting use karo                           |
| Har DBMS mein same syntax assume karna    | Dialect differences check karo                      |
| Frontend mein DB password rakhna          | Backend environment/configuration mein secure rakho |
| User input concatenate karna              | Parameterized query use karo                        |

---

## 25. Important SQL Interview Questions

### Q1. What is SQL?

SQL stands for Structured Query Language. It is used to communicate with relational databases and manage data.

### Q2. Is SQL a programming language?

SQL is generally classified as a declarative database query language. It is not a general-purpose programming language like C++ or Java.

### Q3. What is the difference between SQL and MySQL?

SQL is a language, whereas MySQL is a relational database management system that uses SQL.

### Q4. What is a SQL query?

A SQL query is an instruction written in SQL to perform an operation on a database.

### Q5. What is the use of SELECT?

SELECT retrieves data from one or more database tables.

### Q6. What is the use of WHERE?

WHERE filters records based on a specified condition.

### Q7. What is the difference between WHERE and ORDER BY?

WHERE filters records, while ORDER BY sorts the result.

### Q8. What is DISTINCT?

DISTINCT removes duplicate rows from the selected result columns.

### Q9. What is NULL in SQL?

NULL represents missing, unknown, or unavailable information. It is not the same as zero or an empty string.

### Q10. What is CRUD?

CRUD stands for Create, Read, Update, and Delete.

### Q11. What is SQL Injection?

SQL Injection is a security vulnerability in which malicious input changes the intended behavior of a database query.

### Q12. What is the difference between SQL and NoSQL?

SQL databases are relational, while NoSQL databases support different data models such as document, key-value, and graph.

### Q13. What is a SQL dialect?

A SQL dialect is a particular database system's implementation of SQL, including its supported syntax and features.

### Q14. What is an alias in SQL?

An alias gives a temporary alternative name to a column or table in a query.

### Q15. Why should we avoid SELECT *?

Selecting only required columns can improve readability, reduce unnecessary data transfer, and make applications less dependent on table structure.

---

## 26. Practical Coding Tasks

Khud se ye queries likhne ki practice karo.

Assume table:

`students(id, name, age, city, marks)`

1. Saare students ka data retrieve karo.
2. Sirf name aur age show karo.
3. 80 se zyada marks wale students show karo.
4. Delhi ke students show karo.
5. Marks ascending order mein show karo.
6. Marks descending order mein show karo.
7. Sirf unique cities show karo.
8. Meerut aur Delhi ke students show karo.
9. Age 20 se 22 ke beech wale students show karo.
10. Highest marks wale top 3 students show karo.
11. Name R se start hone wale students show karo.
12. City NULL wale students show karo.

### Practice Solutions

```sql
-- 1. All students
SELECT * FROM students;

-- 2. Specific columns
SELECT name, age FROM students;

-- 3. Marks above 80
SELECT * FROM students
WHERE marks > 80;

-- 4. Delhi students
SELECT * FROM students
WHERE city = 'Delhi';

-- 5. Ascending marks
SELECT * FROM students
ORDER BY marks ASC;

-- 6. Descending marks
SELECT * FROM students
ORDER BY marks DESC;

-- 7. Unique cities
SELECT DISTINCT city FROM students;

-- 8. Meerut and Delhi students
SELECT * FROM students
WHERE city IN ('Meerut', 'Delhi');

-- 9. Age between 20 and 22
SELECT * FROM students
WHERE age BETWEEN 20 AND 22;

-- 10. Top 3 students (MySQL / PostgreSQL)
SELECT * FROM students
ORDER BY marks DESC
LIMIT 3;

-- 11. Names starting with R
SELECT * FROM students
WHERE name LIKE 'R%';

-- 12. City is NULL
SELECT * FROM students
WHERE city IS NULL;
```

---

## 27. Quick Revision Notes

- SQL = Structured Query Language.
- SQL relational databases ke saath communicate karne ke kaam aati hai.
- SQL ek language hai, database software nahi.
- MySQL aur PostgreSQL RDBMS hain.
- Table rows aur columns se milkar banti hai.
- Row = Record / Tuple.
- Column = Attribute / Field.
- Schema = Database structure.
- SELECT = Data retrieve.
- WHERE = Data filter.
- ORDER BY = Data sort.
- DISTINCT = Duplicate result rows remove.
- LIMIT = Result rows ki maximum number limit (supported dialects).
- INSERT = New records add.
- UPDATE = Existing records modify.
- DELETE = Records remove.
- NULL check = IS NULL.
- SQL generally declarative aur set-based hai.
- SQL dialects mein syntax differences ho sakte hain.
- SQL Injection se bachne ke liye parameterized queries use karo.
- MERN mein MongoDB default hai, lekin SQL databases bhi Node.js ke saath use kiye ja sakte hain.

---

## 28. 10 MCQ – Self Test

**Q1. SQL ka full form kya hai?**

A. Simple Query Language  
B. Structured Query Language  
C. Standard Question Language  
D. System Query Logic

**Q2. SQL ka use mainly kis type ke databases ke saath hota hai?**

A. Relational databases  
B. Only graph databases  
C. Only file systems  
D. Operating systems

**Q3. MySQL kya hai?**

A. Programming language  
B. Operating system  
C. RDBMS  
D. Web browser

**Q4. Data retrieve karne ke liye kaunsa statement use hota hai?**

A. UPDATE  
B. SELECT  
C. DELETE  
D. DROP

**Q5. Records filter karne ke liye kya use hota hai?**

A. ORDER BY  
B. DISTINCT  
C. WHERE  
D. CREATE

**Q6. NULL value check karne ka correct syntax kya hai?**

A. `= NULL`  
B. `IS NULL`  
C. `== NULL`  
D. `LIKE NULL`

**Q7. Result ko descending order mein sort karne ke liye kya use hota hai?**

A. ASC  
B. DESC  
C. SORT  
D. REVERSE

**Q8. CRUD mein U ka meaning kya hai?**

A. Upload  
B. Undo  
C. Update  
D. Use

**Q9. SQL Injection se bachne ke liye best practice kya hai?**

A. User input concatenate karna  
B. Parameterized queries use karna  
C. Password frontend mein rakhna  
D. WHERE clause remove karna

**Q10. SQL aur MySQL mein correct difference kya hai?**

A. Dono programming languages hain  
B. SQL database hai aur MySQL language hai  
C. SQL language hai aur MySQL RDBMS hai  
D. Dono operating systems hain

### Answer Key

| Question | Correct Answer |
| -------- | -------------- |
| Q1       | B              |
| Q2       | A              |
| Q3       | C              |
| Q4       | B              |
| Q5       | C              |
| Q6       | B              |
| Q7       | B              |
| Q8       | C              |
| Q9       | B              |
| Q10      | C              |

---

# Topic 09 Completed

Ab tumhe SQL ka basic introduction, database se communication, basic queries, filtering, sorting, CRUD aur MERN stack mein SQL ka use samajh aa jana chahiye.

**Next Topic 10:** SQL Commands – DDL, DML, DQL, DCL and TCL

Ismein har command category ko examples aur practical queries ke saath detail mein samjhenge.
