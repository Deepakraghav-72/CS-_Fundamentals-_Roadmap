# Topic 17: Database Fundamentals

## 1. Database Kya Hota Hai?

Database ek organized collection of data hota hai, jahan hum information ko store, manage, update aur retrieve kar sakte hain.

**Simple Example:**

Maan lo tum ek college management application bana rahe ho.

Us application mein students ki information store hogi:

- Student Name
- Roll Number
- Email
- Course
- Marks

Agar ye saari information properly organized form mein store hai, to use Database mein manage kiya ja sakta hai.

### Simple Definition

A Database is an organized collection of data that can be easily stored, accessed, managed and updated.

### Real-Life Examples

| Application | Database Mein Kya Store Hota Hai? |
| ----------- | --------------------------------- |
| Instagram   | Users, Posts, Comments            |
| WhatsApp    | Users, Messages, Groups           |
| Amazon      | Products, Orders, Payments        |
| Banking App | Accounts, Transactions            |
| College App | Students, Courses, Marks          |

---

## 2. Database Ki Zaroorat Kyu Hoti Hai?

Maan lo tum ek website bana rahe ho jisme users signup aur login kar sakte hain.

Tumhe users ki information store karni hogi:

```text
Name: Rahul
Email: rahul@gmail.com
Password: Hashed Password
```

Agar database nahi hoga, to application ke restart hone ke baad in-memory data lose ho sakta hai.

Database ki help se hum data ko persistent storage mein save kar sakte hain.

### Database Ke Main Uses

1. Data Store Karna
2. Data Retrieve Karna
3. Data Update Karna
4. Data Delete Karna
5. Data Search Karna
6. Data Security Manage Karna
7. Multiple Users Ko Data Access Dena

---

## 3. DBMS Kya Hota Hai?

DBMS ka full form hai:

**Database Management System**

DBMS ek software hota hai jo database ko create, store, manage, retrieve aur update karne mein help karta hai.

Simple words mein:

Database data ka collection hai, jabki DBMS us data ko manage karne wala software hai.

### Examples of DBMS

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- MongoDB

### Database vs DBMS

| Database                     | DBMS                                                |
| ---------------------------- | --------------------------------------------------- |
| Data ka organized collection | Database manage karne wala software                 |
| Information store karta hai  | Information manage karne ke tools provide karta hai |
| Data contain karta hai       | Data operations execute karta hai                   |

### Example

Maan lo tumne MySQL install kiya.

- MySQL = DBMS
- MySQL ke andar created database = Database
- Students ki information = Data

---

## 4. DBMS Kaise Kaam Karta Hai?

Jab application ko data save ya retrieve karna hota hai, to wo DBMS ke through database ke saath communicate karti hai.

### Basic Flow

```text
       User
        |
        v
   Frontend (React)
        |
        v
   Backend (Node.js)
        |
        v
       DBMS
        |
        v
     Database
```

### Example: Signup

1. User React form mein details enter karta hai.
2. React data backend ko send karta hai.
3. Node.js backend data validate karta hai.
4. Backend DBMS ko data save karne ki request deta hai.
5. DBMS database mein data store karta hai.
6. Backend frontend ko response send karta hai.

**Important:** Frontend ko normally database ke saath directly connect nahi karna chahiye. Database credentials aur operations backend ke through securely manage karne chahiye.

---

## 5. Types of Databases

Databases ko different categories mein divide kiya ja sakta hai.

Important database types:

1. Relational Database
2. NoSQL Database
3. Hierarchical Database
4. Network Database
5. Object-Oriented Database
6. Time-Series Database
7. Graph Database

System Design aur modern web development mein Relational aur NoSQL databases bahut important hain.

### 5.1 Relational Database

Relational Database mein data tables ke form mein store hota hai.

Tables mein rows aur columns hote hain.

Example:

**Students Table**

| ID  | Name  | Email           |
| --- | ----- | --------------- |
| 1   | Rahul | rahul@gmail.com |
| 2   | Aman  | aman@gmail.com  |
| 3   | Rohit | rohit@gmail.com |

Examples:

- MySQL
- PostgreSQL
- Oracle
- SQL Server

### 5.2 NoSQL Database

NoSQL databases data ko relational tables ke traditional format ke alawa different structures mein store kar sakte hain.

Example: MongoDB mein data documents ke form mein store hota hai.

```json
{
  "_id": "101",
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "course": "MERN Stack"
}
```

Examples:

- MongoDB
- Redis
- Cassandra
- Couchbase

**Note:** NoSQL ka matlab "No SQL" nahi, commonly "Not Only SQL" ke sense mein use hota hai.

---

## 6. Table, Row aur Column Kya Hote Hain?

Ye concepts relational databases mein use hote hain.

### Table

Table related data ka collection hota hai.

Example: Students Table.

### Row

Row ek complete record ko represent karti hai.

Example:

```text
1 | Rahul | rahul@gmail.com
```

Ye ek student ka complete record hai.

### Column

Column kisi specific attribute ko represent karta hai.

Example:

- ID
- Name
- Email

### Diagram

```text
             Students Table

       ID      Name       Email
       ----------------------------
       1       Rahul      rahul@gmail.com
       2       Aman       aman@gmail.com
       3       Rohit      rohit@gmail.com
```

| Term   | Meaning                        |
| ------ | ------------------------------ |
| Table  | Related records ka collection  |
| Row    | One complete record            |
| Column | One attribute / field          |
| Cell   | Row aur column ka intersection |

---

## 7. Schema Kya Hota Hai?

Database Schema database ka logical structure ya blueprint hota hai.

Schema define karta hai ki database mein:

- Kaunsi tables hongi
- Kaunse columns honge
- Data types kya honge
- Tables ke relationships kya honge
- Constraints kya honge

Example:

```sql
CREATE TABLE Students (
    id INT,
    name VARCHAR(100),
    email VARCHAR(150)
);
```

Is example mein hum Students table ka structure define kar rahe hain.

**Important:** Schema ka exact meaning database technology ke according vary kar sakta hai. Relational databases mein ye tables, columns, relationships aur constraints ke structure ko describe karta hai.

---

## 8. Data Types Kya Hote Hain?

Data Type define karta hai ki kisi column mein kis type ka data store ho sakta hai.

Common SQL Data Types:

| Data Type    | Use                   |
| ------------ | --------------------- |
| INT          | Integer numbers       |
| BIGINT       | Large integer numbers |
| VARCHAR(n)   | Variable-length text  |
| CHAR(n)      | Fixed-length text     |
| TEXT         | Long text             |
| DATE         | Date                  |
| TIME         | Time                  |
| BOOLEAN      | True / False          |
| DECIMAL(p,s) | Exact decimal values  |

Example:

```sql
CREATE TABLE Products (
    id INT,
    name VARCHAR(100),
    price DECIMAL(10,2),
    created_at DATE
);
```

**Note:** Exact data types aur unka behavior DBMS ke according change ho sakta hai.

---

## 9. Primary Key Kya Hoti Hai?

Primary Key ek column ya columns ka combination hota hai jo table ke har record ko uniquely identify karta hai.

Example:

| Student_ID | Name  |
| ---------- | ----- |
| 101        | Rahul |
| 102        | Aman  |
| 103        | Rohit |

Yahan Student_ID Primary Key ho sakti hai.

### Primary Key Ki Properties

1. Unique honi chahiye.
2. NULL nahi ho sakti.
3. Ek table mein ek primary key constraint hota hai.
4. Primary key ek ya multiple columns se milkar ban sakti hai.

Example:

```sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);
```

---

## 10. Foreign Key Kya Hoti Hai?

Foreign Key ek column ya columns ka combination hota hai jo doosri table ke Primary Key ya kisi eligible unique key ko reference karta hai.

Iska use tables ke beech relationship establish karne ke liye hota hai.

Example:

**Students Table**

| Student_ID | Name  |
| ---------- | ----- |
| 101        | Rahul |
| 102        | Aman  |

**Orders Table**

| Order_ID | Student_ID |
| -------- | ---------- |
| 1        | 101        |
| 2        | 102        |
| 3        | 101        |

Yahan Orders table ka Student_ID, Students table ke Student_ID ko reference kar sakta hai.

### SQL Example

```sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    student_id INT,
    FOREIGN KEY (student_id)
    REFERENCES Students(student_id)
);
```

### Primary Key vs Foreign Key

| Primary Key                             | Foreign Key                                |
| --------------------------------------- | ------------------------------------------ |
| Record ko uniquely identify karti hai   | Do tables ke beech relationship banati hai |
| Unique hoti hai                         | Duplicate values allowed ho sakti hain     |
| NULL allowed nahi                       | NULL allowed ho sakta hai, unless NOT NULL |
| Ek table mein ek primary key constraint | Multiple foreign key constraints possible  |

---

## 11. Constraints Kya Hote Hain?

Constraints database columns par apply hone wale rules hote hain.

Ye ensure karte hain ki invalid data database mein store na ho.

### Important SQL Constraints

**1. NOT NULL**

Column mein NULL value allow nahi karta.

```sql
name VARCHAR(100) NOT NULL
```

**2. UNIQUE**

Column ki values unique honi chahiye.

```sql
email VARCHAR(150) UNIQUE
```

**3. PRIMARY KEY**

Record ko uniquely identify karti hai.

```sql
id INT PRIMARY KEY
```

**4. FOREIGN KEY**

Tables ke beech referential relationship maintain karti hai.

```sql
FOREIGN KEY (user_id) REFERENCES Users(id)
```

**5. CHECK**

Condition define karta hai.

```sql
age INT CHECK (age >= 18)
```

**6. DEFAULT**

Value provide nahi karne par default value set karta hai.

```sql
status VARCHAR(20) DEFAULT 'active'
```

---

## 12. CRUD Operations Kya Hote Hain?

CRUD ka full form hai:

- C – Create
- R – Read
- U – Update
- D – Delete

Ye database ke four basic operations hain.

### 12.1 Create

Naya record insert karna.

```sql
INSERT INTO Students (id, name)
VALUES (1, 'Rahul');
```

### 12.2 Read

Database se data retrieve karna.

```sql
SELECT * FROM Students;
```

### 12.3 Update

Existing record modify karna.

```sql
UPDATE Students
SET name = 'Aman'
WHERE id = 1;
```

### 12.4 Delete

Record delete karna.

```sql
DELETE FROM Students
WHERE id = 1;
```

**Important:** UPDATE aur DELETE queries mein WHERE condition bhoolne se multiple ya saare records affect ho sakte hain.

---

## 13. SQL Kya Hota Hai?

SQL ka full form hai:

Structured Query Language.

SQL ek language hai jiska use relational databases ke saath communicate karne ke liye kiya jata hai.

SQL ki help se hum:

- Database create kar sakte hain.
- Tables create kar sakte hain.
- Data insert kar sakte hain.
- Data retrieve kar sakte hain.
- Data update kar sakte hain.
- Data delete kar sakte hain.

Example:

```sql
SELECT name, email
FROM Students
WHERE student_id = 101;
```

Ye query Student ID 101 wale student ka name aur email retrieve karegi.

---

## 14. Query Kya Hoti Hai?

Query database ko diya gaya instruction ya request hoti hai.

Example:

```sql
SELECT * FROM Students;
```

Ye database se Students table ke saare columns aur records retrieve karne ki request hai.

### Common SQL Queries

```sql
-- All records
SELECT * FROM Students;

-- Specific columns
SELECT name, email FROM Students;

-- Filter records
SELECT * FROM Students
WHERE age > 18;

-- Sort records
SELECT * FROM Students
ORDER BY name ASC;

-- Count records
SELECT COUNT(*) FROM Students;
```

---

## 15. Index Kya Hota Hai?

Index database ka ek data structure hota hai jo data ko efficiently search karne mein help karta hai.

Real-life example:

Maan lo tumhare paas 1000 pages ki book hai.

Agar kisi topic ko find karna hai aur index nahi hai, to tumhe page by page search karna pad sakta hai.

Lekin book ke end mein index diya ho, to topic ka page number jaldi mil sakta hai.

Database Index bhi isi tarah searching ko faster bana sakta hai.

### Without Index

```text
Search Request
      |
      v
Check records one by one
      |
      v
Find matching record
```

### With Index

```text
Search Request
      |
      v
   Database Index
      |
      v
Find matching record faster
```

### SQL Example

```sql
CREATE INDEX idx_email
ON Students(email);
```

Ab email column par suitable queries ko index ka benefit mil sakta hai.

### Index Ke Advantages

- Searching faster ho sakti hai.
- Filtering improve ho sakti hai.
- Sorting aur joins mein help mil sakti hai.

### Index Ke Disadvantages

- Extra storage use hota hai.
- INSERT, UPDATE aur DELETE operations slower ho sakte hain.
- Indexes ko maintain karna padta hai.

**Important:** Har column par index banana best practice nahi hai. Index query patterns aur data distribution ko dekhkar banaya jata hai.

---

## 16. Database Normalization Kya Hai?

Normalization relational database design ki ek technique hai.

Iska purpose unnecessary data duplication ko reduce karna aur data consistency improve karna hai.

Example:

Maan lo ek table mein student ki information aur course information baar-baar repeat ho rahi hai.

| Student_ID | Student_Name | Course |
| ---------- | ------------ | ------ |
| 1          | Rahul        | MERN   |
| 2          | Aman         | MERN   |
| 3          | Rohit        | MERN   |

Agar course ki details bahut baar repeat ho rahi hain, to separate tables banakar data organize kiya ja sakta hai.

### Normalization Ke Benefits

1. Duplicate data reduce hota hai.
2. Data consistency improve hoti hai.
3. Update anomalies reduce hoti hain.
4. Database structure organized hota hai.

### Important Normal Forms

**1NF – First Normal Form**

- Har cell mein atomic/single value honi chahiye.
- Repeating groups nahi hone chahiye.

**2NF – Second Normal Form**

- Table 1NF mein honi chahiye.
- Har non-key attribute poori candidate key par depend kare; partial dependency nahi honi chahiye.

**3NF – Third Normal Form**

- Table 2NF mein honi chahiye.
- Non-key attributes mein transitive dependency nahi honi chahiye (candidate keys ke through dependencies ko chhodkar).

Normalization ko hum Database Management System ke detailed topics mein aur depth se samajh sakte hain.

---

## 17. Database Relationships

Relational databases mein tables ke beech different types ke relationships ho sakte hain.

### 17.1 One-to-One Relationship

Ek record ka relationship doosri table ke ek hi record ke saath hota hai.

Example:

Ek user ka ek profile record.

```text
User 1 -------- 1 Profile
```

### 17.2 One-to-Many Relationship

Ek record ka relationship doosri table ke multiple records ke saath ho sakta hai.

Example:

Ek user ke multiple orders.

```text
User 1 -------- Many Orders
```

### 17.3 Many-to-Many Relationship

Ek table ke multiple records doosri table ke multiple records se related ho sakte hain.

Example:

Students aur Courses.

- Ek student multiple courses join kar sakta hai.
- Ek course mein multiple students ho sakte hain.

```text
Students ----- Student_Courses ----- Courses
```

Relational databases mein many-to-many relationship usually junction table ke through represent hota hai.

---

## 18. Database Transactions

Transaction database operations ka ek logical unit hota hai.

Example:

Bank Account A se ₹1000 deduct karke Account B mein ₹1000 add karna.

Dono operations successfully complete hone chahiye.

Agar ek operation fail ho jaye, to transaction ko rollback karna pad sakta hai.

### Example

```text
Account A = ₹5000
Account B = ₹2000

Transfer ₹1000

Account A = ₹4000
Account B = ₹3000
```

Transaction ensure karta hai ki operation database ke defined rules ke according safely complete ho.

Transactions ke important properties ko ACID kehte hain:

- Atomicity
- Consistency
- Isolation
- Durability

Inhe hum Topic 19: ACID Properties & Transactions mein detail mein padhenge.

---

## 19. Database Backup and Recovery

Database Backup ka matlab database ki copy create karna hai, taaki data loss hone par use recover kiya ja sake.

### Backup Ki Zaroorat Kyu Hai?

- Hardware failure
- Accidental deletion
- Software bugs
- Cyber attacks
- Data corruption

### Common Backup Types

**1. Full Backup**

Poore database ka backup.

**2. Incremental Backup**

Last backup ke baad hue changes ka backup.

**3. Differential Backup**

Last full backup ke baad hue changes ka backup.

### Recovery

Recovery ka matlab backup ya recovery logs ki help se database ko restore karna hai.

Production applications mein backup ke saath restore testing bhi important hoti hai.

---

## 20. Database Security

Database mein sensitive information ho sakti hai. Isliye database security important hai.

### Important Practices

1. Strong Authentication
2. Role-Based Access Control
3. Least Privilege
4. Encryption at Rest
5. Encryption in Transit
6. Regular Backups
7. Secure Credentials
8. SQL Injection Protection

### SQL Injection

SQL Injection ek security vulnerability hai jisme attacker unsafe user input ke through database query ko manipulate karne ki koshish karta hai.

**Unsafe Example:**

```javascript
const query = "SELECT * FROM users WHERE email = '" + userInput + "'";
```

User input ko directly SQL query mein concatenate karna dangerous ho sakta hai.

**Safe Approach:**

Parameterized queries ya prepared statements use karo.

```javascript
const query = "SELECT * FROM users WHERE email = ?";

db.execute(query, [userInput]);
```

Actual syntax database driver ke according change hota hai.

MongoDB mein bhi unsafe query construction aur improper input handling se injection risks ho sakte hain.

---

## 21. Database Performance

Database performance ka matlab database queries aur operations kitni efficiently execute ho rahe hain.

### Performance Improve Karne Ke Methods

1. Proper Indexing
2. Query Optimization
3. Connection Pooling
4. Avoid Unnecessary Queries
5. Pagination
6. Caching
7. Proper Schema Design

Example:

Agar database mein 10 lakh records hain aur frontend ko sirf 20 records dikhane hain, to pagination use karna better ho sakta hai.

```sql
SELECT * FROM Students
LIMIT 20 OFFSET 0;
```

---

## 22. Database in MERN Stack

MERN Stack mein MongoDB database use hota hai.

MERN ka full form:

- M – MongoDB
- E – Express.js
- R – React.js
- N – Node.js

### MERN Architecture

```text
       React.js
          |
          v
      Express.js
          |
          v
       Node.js
          |
          v
       MongoDB
```

### Example: User Signup

1. User React form fill karta hai.
2. React signup request Express backend ko bhejta hai.
3. Node.js request process karta hai.
4. Backend user data validate karta hai.
5. Password ko hash kiya jata hai.
6. MongoDB mein user document save hota hai.
7. Backend response return karta hai.

### MongoDB Document Example

```json
{
  "_id": "101",
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "password": "hashed_password",
  "role": "user"
}
```

**Important:** Real applications mein password ko plain text mein kabhi store nahi karna chahiye.

---

## 23. SQL vs NoSQL – Basic Comparison

| SQL Database                      | NoSQL Database                           |
| --------------------------------- | ---------------------------------------- |
| Relational model                  | Different data models                    |
| Tables, rows, columns             | Documents, key-value, graph, etc.        |
| Usually predefined schema         | Often flexible schema                    |
| SQL query language                | Database-specific query methods          |
| Relationships often through joins | Relationships may be modeled differently |
| MySQL, PostgreSQL                 | MongoDB, Redis, Cassandra                |

Dono types powerful hain. Kaunsa database choose karna hai, ye application requirements par depend karta hai.

Iska detailed comparison next topic mein padhenge.

---

## 24. Important Interview Questions

### Q1. What is a Database?

Database organized collection of data hota hai jisme information store, manage aur retrieve ki ja sakti hai.

### Q2. What is DBMS?

DBMS ek software hai jo database ko create, manage aur access karne mein help karta hai.

### Q3. What is a Primary Key?

Primary Key table ke har record ko uniquely identify karti hai.

### Q4. What is a Foreign Key?

Foreign Key ek table ke column ko doosri table ki eligible key se connect karti hai.

### Q5. What is Database Indexing?

Indexing ek technique hai jo data searching ko faster banane mein help karti hai.

### Q6. What is Normalization?

Normalization database design technique hai jo unnecessary duplication reduce aur consistency improve karti hai.

### Q7. What is a Database Transaction?

Transaction database operations ka logical unit hota hai jo ek complete operation ke roop mein execute hota hai.

### Q8. What is a Database Schema?

Schema database ke structure aur organization ko define karta hai.

### Q9. What are CRUD operations?

Create, Read, Update aur Delete database ke basic operations hain.

### Q10. What is SQL Injection?

SQL Injection ek vulnerability hai jisme malicious input ke through SQL queries manipulate ki ja sakti hain.

---

## 25. Practical Tasks

1. Database aur DBMS ka difference apne words mein likho.
2. Students naam ki SQL table design karo.
3. Primary Key aur Foreign Key ka example banao.
4. CRUD operations ki SQL queries likho.
5. Index create karne ki SQL query likho.
6. One-to-One, One-to-Many aur Many-to-Many relationships ke examples banao.
7. MERN application ka basic database flow draw karo.

---

## 26. Quick Revision

| Term          | Meaning                                     |
| ------------- | ------------------------------------------- |
| Database      | Organized collection of data                |
| DBMS          | Database manage karne wala software         |
| SQL           | Relational database query language          |
| Table         | Related data ka collection                  |
| Row           | Complete record                             |
| Column        | Attribute                                   |
| Schema        | Database structure                          |
| Primary Key   | Unique record identifier                    |
| Foreign Key   | Table relationship establish karti hai      |
| Constraint    | Data par applied rule                       |
| CRUD          | Create, Read, Update, Delete                |
| Index         | Searching improve karne wala data structure |
| Normalization | Data duplication reduce karne ki technique  |
| Transaction   | Logical unit of database operations         |
| Backup        | Data ki safety copy                         |
| Recovery      | Data restore karna                          |

---

## 27. Final Checklist

- [ ] Database kya hai samajh sakte ho.
- [ ] DBMS explain kar sakte ho.
- [ ] Relational aur NoSQL databases identify kar sakte ho.
- [ ] Table, Row aur Column explain kar sakte ho.
- [ ] Schema aur Data Types samajh sakte ho.
- [ ] Primary Key aur Foreign Key differentiate kar sakte ho.
- [ ] SQL CRUD queries likh sakte ho.
- [ ] Indexing explain kar sakte ho.
- [ ] Normalization ka purpose samajh sakte ho.
- [ ] Database relationships identify kar sakte ho.
- [ ] Transactions aur Backup ka purpose samajh sakte ho.
- [ ] MERN mein database ka flow explain kar sakte ho.

**Topic 17 Complete – Database Fundamentals**
