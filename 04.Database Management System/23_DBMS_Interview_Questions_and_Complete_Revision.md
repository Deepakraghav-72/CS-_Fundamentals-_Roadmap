# 23. DBMS Complete Interview Questions and Revision

## 1. DBMS Fundamentals

### Q1. DBMS kya hai?

DBMS (Database Management System) ek software hai jo data ko store, manage, retrieve, update aur delete karne mein help karta hai.

Examples: MySQL, PostgreSQL, Oracle, MongoDB.

### Q2. Database vs DBMS vs RDBMS?

| Database                  | DBMS                             | RDBMS                                  |
| ------------------------- | -------------------------------- | -------------------------------------- |
| Organized data collection | Data manage karne wala software  | Relational DBMS                        |
| Data store karta hai      | Data operations handle karta hai | Tables aur relationships use karta hai |

### Q3. DBMS ke advantages?

- Data redundancy reduce karta hai.
- Data security provide karta hai.
- Data consistency improve karta hai.
- Backup and recovery support karta hai.
- Multiple users ko access de sakta hai.

### Q4. Schema vs Instance?

- Schema: Database ka structure/design.
- Instance: Kisi particular time par actual stored data.

### Q5. Three-Schema Architecture kya hai?

1. External Level – User views.
2. Conceptual Level – Complete logical database structure.
3. Internal Level – Physical storage details.

### Q6. Data Independence kya hai?

Ek level par changes karne se doosre level par minimum impact hona.

- Physical Data Independence.
- Logical Data Independence.

## 2. ER Model, Keys and Relationships

### Q7. ER Model kya hai?

Entity-Relationship Model database ko entities, attributes aur relationships ke through represent karta hai.

### Q8. Entity vs Attribute?

- Entity: Real-world object, jaise Student.
- Attribute: Entity ki property, jaise Name, Age, Email.

### Q9. Primary Key kya hai?

Aisi key jo table ke har record ko uniquely identify karti hai. Isme duplicate aur NULL values allowed nahi hoti.

### Q10. Foreign Key kya hai?

Ek table ka column jo doosre table ki primary ya eligible unique key ko reference karta hai.

### Q11. Candidate Key kya hai?

Minimal set of attributes jo record ko uniquely identify kar sake.

### Q12. Super Key vs Candidate Key?

- Super Key: Unique identification ke liye sufficient attributes.
- Candidate Key: Minimal Super Key.

### Q13. Composite Key kya hai?

Do ya zyada columns milkar record ko uniquely identify karte hain.

### Q14. Relationships ke types?

- One-to-One (1:1)
- One-to-Many (1:M)
- Many-to-Many (M:N)

## 3. Relational Model and Constraints

### Q15. Relational Model kya hai?

Data ko rows aur columns wali relations (tables) mein represent karne ka model.

### Q16. Tuple, Attribute, Degree and Cardinality?

| Term        | Meaning           |
| ----------- | ----------------- |
| Tuple       | Row               |
| Attribute   | Column            |
| Degree      | Number of columns |
| Cardinality | Number of rows    |

### Q17. Constraints kya hain?

Rules jo database mein valid data ensure karte hain.

- NOT NULL
- UNIQUE
- PRIMARY KEY
- FOREIGN KEY
- CHECK
- DEFAULT

### Q18. NULL kya hota hai?

NULL ka matlab value missing, unknown ya not applicable ho sakti hai. Ye zero ya empty string ke equal nahi hai.

## 4. SQL Important Questions

### Q19. SQL kya hai?

SQL (Structured Query Language) relational databases ke saath communicate karne ke liye use hoti hai.

### Q20. SQL Commands ke types?

| Category | Commands                      |
| -------- | ----------------------------- |
| DDL      | CREATE, ALTER, DROP, TRUNCATE |
| DML      | INSERT, UPDATE, DELETE        |
| DQL      | SELECT                        |
| DCL      | GRANT, REVOKE                 |
| TCL      | COMMIT, ROLLBACK, SAVEPOINT   |

Note: SELECT ko DQL ya broad DML classification mein rakhne ka convention vary kar sakta hai.

### Q21. DELETE vs TRUNCATE vs DROP?

| DELETE                   | TRUNCATE                       | DROP                          |
| ------------------------ | ------------------------------ | ----------------------------- |
| Rows delete karta hai    | Table ke rows remove karta hai | Table object remove karta hai |
| WHERE use kar sakte hain | Generally WHERE nahi           | Table structure bhi remove    |
| DML                      | Usually DDL classification     | DDL                           |

Transaction aur rollback behavior DBMS-specific hota hai.

### Q22. WHERE vs HAVING?

- WHERE: Grouping se pehle individual rows filter karta hai.
- HAVING: GROUP BY ke baad groups filter karta hai.

### Q23. GROUP BY kya hai?

Same values wale records ko groups mein combine karta hai.

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

### Q24. Aggregate Functions?

- COUNT()
- SUM()
- AVG()
- MIN()
- MAX()

### Q25. COUNT(*) vs COUNT(column)?

- COUNT(*) = Total rows count.
- COUNT(column) = Non-NULL values count.

### Q26. SQL Operators?

- Arithmetic: `+ - * /`
- Comparison: `= != > < >= <=`
- Logical: `AND OR NOT`
- Special: `IN`, `BETWEEN`, `LIKE`, `IS NULL`, `EXISTS`

### Q27. UNION vs UNION ALL?

- UNION duplicate rows remove karta hai.
- UNION ALL duplicates retain karta hai.

### Q28. SQL JOIN kya hai?

Multiple tables ke related records ko combine karna.

| JOIN  | Result                    |
| ----- | ------------------------- |
| INNER | Matching records          |
| LEFT  | All left + matching right |
| RIGHT | All right + matching left |
| FULL  | Both sides ke all records |
| CROSS | Cartesian product         |
| SELF  | Same table ke saath join  |

### Q29. JOIN vs UNION?

JOIN columns combine karta hai; UNION compatible result sets ke rows combine karta hai.

### Q30. Subquery kya hai?

Ek query ke andar doosri query.

```sql
SELECT name
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

### Q31. Correlated Subquery?

Aisi subquery jo outer query ke columns ko reference karti hai.

### Q32. EXISTS vs IN?

- IN: Values ki list/set mein membership check karta hai.
- EXISTS: Subquery se rows exist karti hain ya nahi check karta hai.

### Q33. NULL ko kaise check karte hain?

```sql
SELECT *
FROM employees
WHERE manager_id IS NULL;
```

`= NULL` use nahi karna chahiye.

## 5. Normalization

### Q34. Normalization kya hai?

Database ko properly organize karna, redundancy aur anomalies reduce karna.

### Q35. Normal Forms?

| Normal Form | Main Rule                                                            |
| ----------- | -------------------------------------------------------------------- |
| 1NF         | Atomic values, repeating groups nahi                                 |
| 2NF         | 1NF + partial dependency nahi                                        |
| 3NF         | 2NF + transitive dependency ko remove karna (common simplified rule) |
| BCNF        | Har non-trivial FD ka determinant superkey                           |
| 4NF         | Non-trivial multivalued dependency ka proper decomposition           |
| 5NF         | Join dependencies aur lossless decomposition                         |

### Q36. Data Anomalies?

- Insertion Anomaly
- Update Anomaly
- Deletion Anomaly

### Q37. Denormalization kya hai?

Performance/read efficiency improve karne ke liye controlled redundancy introduce karna.

## 6. Transactions and ACID

### Q38. Transaction kya hai?

Database operations ka logical unit jo ek complete task perform karta hai.

Example: Bank transfer.

### Q39. ACID Properties?

| Property    | Meaning                                        |
| ----------- | ---------------------------------------------- |
| Atomicity   | All or nothing                                 |
| Consistency | Valid database state                           |
| Isolation   | Concurrent transactions ka controlled behavior |
| Durability  | Commit ke baad changes persist                 |

### Q40. COMMIT vs ROLLBACK?

- COMMIT: Transaction ke changes save karta hai.
- ROLLBACK: Uncommitted changes cancel karta hai.

### Q41. SAVEPOINT kya hai?

Transaction ke andar ek point jahan tak partial rollback kar sakte hain.

### Q42. Dirty Read kya hai?

Ek transaction doosre transaction ke uncommitted changes read kar leta hai.

### Q43. Isolation Levels?

1. Read Uncommitted
2. Read Committed
3. Repeatable Read
4. Serializable

Exact anomaly behavior DBMS implementation ke according vary kar sakta hai.

### Q44. Deadlock kya hai?

Jab transactions ek-doosre ke held resources ka wait karte hue indefinitely block ho jaate hain.

## 7. Concurrency Control and Indexing

### Q45. Concurrency Control kya hai?

Multiple transactions ko safely execute karwana, taaki data inconsistency na ho.

### Q46. Shared vs Exclusive Lock?

- Shared Lock (S): Read ke liye; compatible shared locks possible.
- Exclusive Lock (X): Write ke liye; conflicting locks ko block karta hai.

### Q47. 2PL kya hai?

Two-Phase Locking:

- Growing Phase: Locks acquire karna.
- Shrinking Phase: Locks release karna.

### Q48. MVCC kya hai?

Multi-Version Concurrency Control. Data ki multiple versions maintain karke readers aur writers ke beech conflicts reduce karta hai.

### Q49. Database Index kya hai?

Index ek data structure hai jo records ko efficiently search karne mein help karta hai.

### Q50. Index ke disadvantages?

- Extra storage.
- INSERT/UPDATE/DELETE par maintenance cost.
- Too many indexes performance hurt kar sakte hain.

### Q51. Clustered vs Non-Clustered Index?

Conceptually:

- Clustered: Rows ki storage organization index se associated hoti hai.
- Non-Clustered: Separate index structure rows ko locate karne mein help karta hai.

Implementation DBMS-specific hoti hai.

### Q52. B-Tree vs B+ Tree?

- B-Tree: Internal aur leaf nodes mein keys/data entries ho sakti hain.
- B+ Tree: Actual record entries generally leaf nodes par hoti hain; leaves linked ho sakti hain.

### Q53. Composite Index kya hai?

Multiple columns par bana index.

Example:

```sql
CREATE INDEX idx_dept_salary
ON employees(department, salary);
```

Composite index mein leftmost-prefix principle important hota hai.

## 8. Views, Procedures and Query Optimization

### Q54. View kya hai?

View ek virtual table hai jo SQL query ke result par based hota hai.

```sql
CREATE VIEW high_salary AS
SELECT name, salary
FROM employees
WHERE salary > 50000;
```

### Q55. Materialized View kya hai?

Query result physically store karta hai aur refresh karna pad sakta hai.

### Q56. Stored Procedure kya hai?

Database mein stored SQL statements ka reusable program/unit.

### Q57. Stored Procedure vs Function?

Dono mein differences DBMS ke according vary karte hain. Commonly procedure actions perform karta hai, function value return karne ke liye use hota hai.

### Q58. Query Optimization kya hai?

Query ko efficiently execute karne ke liye execution plan improve karna.

### Q59. EXPLAIN kya hai?

SQL query ka execution plan dekhne ke liye use hota hai.

### Q60. Full Table Scan kya hai?

Database table ke records ko scan karke required data search karta hai.

### Q61. Index har query ko fast kyun nahi karta?

Index maintenance aur lookup cost hoti hai. Small table ya large percentage of rows read karne mein full scan faster ho sakta hai.

## 9. NoSQL and MongoDB

### Q62. NoSQL kya hai?

Non-relational database systems ke liye use hone wala broad term.

Types:

1. Key-Value
2. Document
3. Column-Family
4. Graph

### Q63. MongoDB kya hai?

MongoDB ek document-oriented NoSQL database hai jo BSON format mein documents store karta hai.

### Q64. SQL vs NoSQL?

| SQL                       | NoSQL                                  |
| ------------------------- | -------------------------------------- |
| Relational model          | Different data models                  |
| Tables                    | Documents, key-value, graphs etc.      |
| SQL query language        | Database-specific APIs/query languages |
| Structured schemas common | Flexible schemas common                |

### Q65. MongoDB Document kya hai?

JSON-like BSON structure mein stored record.

```javascript
{
  name: "Rahul",
  age: 22,
  skills: ["HTML", "CSS", "JavaScript"]
}
```

### Q66. Collection vs Document?

- Collection = Related documents ka group.
- Document = Individual record.

### Q67. Embedding vs Referencing?

- Embedding: Related data same document mein store.
- Referencing: Related data ka ID/reference store.

### Q68. MongoDB Aggregation kya hai?

Data processing pipeline ke through filtering, grouping, sorting aur calculations karna.

```javascript
db.orders.aggregate([
  { $match: { status: "completed" } },
  {
    $group: {
      _id: "$customerId",
      total: { $sum: "$amount" },
    },
  },
]);
```

### Q69. MongoDB `$lookup` kya hai?

Aggregation pipeline mein doosri collection se related documents join-like operation se retrieve karta hai.

### Q70. MongoDB Index kya hai?

MongoDB index query performance improve karta hai. MongoDB collection mein `_id` par default unique index hota hai.

### Q71. MongoDB Transaction?

Multiple operations ko ACID transaction ke andar execute kiya ja sakta hai. Multi-document transactions ke liye replica set ya sharded cluster required hota hai.

## 10. Database Security and Backup

### Q72. SQL Injection kya hai?

Malicious input ke through SQL query manipulate karne ka attack.

Protection: Parameterized queries, prepared statements, least privilege.

### Q73. Authentication vs Authorization?

Authentication identity verify karta hai; authorization permissions decide karta hai.

### Q74. Backup ke types?

- Full
- Incremental
- Differential
- Logical
- Physical

### Q75. RPO vs RTO?

- RPO = Acceptable data loss.
- RTO = Acceptable recovery time.

### Q76. Replication vs Backup?

Replication availability improve kar sakti hai; backup historical recovery mein help karta hai. Replication backup ka replacement nahi.

---

# 11. Most Important SQL Practical Queries

Assume table:

`employees(id, name, department, salary, manager_id)`

### 1. All employees

```sql
SELECT * FROM employees;
```

### 2. Salary greater than 50000

```sql
SELECT *
FROM employees
WHERE salary > 50000;
```

### 3. Highest salary

```sql
SELECT MAX(salary)
FROM employees;
```

### 4. Second Highest Distinct Salary

```sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

Note: `LIMIT` syntax MySQL/PostgreSQL mein supported hai. Other DBMS mein alternative syntax ho sakti hai.

### 5. Department-wise employee count

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

### 6. Department-wise average salary

```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department;
```

### 7. Employees earning above average salary

```sql
SELECT *
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

### 8. Duplicate names find karna

```sql
SELECT name, COUNT(*)
FROM employees
GROUP BY name
HAVING COUNT(*) > 1;
```

### 9. Employees with NULL manager

```sql
SELECT *
FROM employees
WHERE manager_id IS NULL;
```

### 10. Employees ordered by salary

```sql
SELECT *
FROM employees
ORDER BY salary DESC;
```

### 11. Update employee salary

```sql
UPDATE employees
SET salary = 60000
WHERE id = 101;
```

### 12. Delete specific employee

```sql
DELETE FROM employees
WHERE id = 101;
```

**Warning:** UPDATE/DELETE se pehle WHERE condition verify karo. Bina WHERE ke multiple ya all rows affect ho sakti hain.

---

# 12. Important DBMS Differences – Quick Table

| Comparison                 | Main Difference                                   |
| -------------------------- | ------------------------------------------------- |
| DBMS vs RDBMS              | General database management vs relational model   |
| Primary vs Foreign Key     | Unique identification vs relationship reference   |
| Candidate vs Super Key     | Minimal unique key vs any unique super key        |
| WHERE vs HAVING            | Row filter vs group filter                        |
| DELETE vs TRUNCATE         | Row deletion vs all-row removal                   |
| UNION vs UNION ALL         | Duplicate removal vs duplicate retention          |
| INNER vs LEFT JOIN         | Only matching vs all left rows                    |
| Subquery vs Correlated     | Independent vs outer query dependent              |
| 2NF vs 3NF                 | Partial vs transitive dependency (simplified)     |
| COMMIT vs ROLLBACK         | Save vs cancel uncommitted work                   |
| S Lock vs X Lock           | Shared read vs exclusive access                   |
| Clustered vs Non-Clustered | Storage organization vs separate lookup structure |
| View vs Materialized View  | Stored query definition vs stored result          |
| SQL vs NoSQL               | Relational vs non-relational data models          |
| Replication vs Backup      | Availability vs recovery copy                     |
| RPO vs RTO                 | Data loss target vs recovery time target          |

---

# 13. MERN Developer ke liye DBMS Knowledge

MERN developer ko ye concepts especially strong rakhne chahiye:

1. Database, collection aur document.
2. MongoDB CRUD operations.
3. Schema design.
4. Embedding vs referencing.
5. MongoDB indexing.
6. Aggregation pipeline.
7. `$lookup`.
8. Pagination.
9. Data validation.
10. Authentication and authorization.
11. Password hashing.
12. Transactions.
13. Database backup and recovery.
14. Query optimization.
15. Mongoose models and relationships.

**Important:** MERN stack mein React directly MongoDB se connect nahi karta. Normal architecture:

```text
React
  |
  v
Node.js + Express API
  |
  v
Mongoose / MongoDB Driver
  |
  v
MongoDB
```

---

# 14. Practical DBMS Interview Preparation Tasks

- [ ] Create database and tables.
- [ ] Define Primary Key and Foreign Key.
- [ ] Practice INSERT, UPDATE, DELETE and SELECT.
- [ ] Practice all major JOIN types.
- [ ] Solve 10 GROUP BY and HAVING questions.
- [ ] Solve 10 subquery questions.
- [ ] Understand 1NF, 2NF and 3NF with examples.
- [ ] Explain ACID properties with bank transfer example.
- [ ] Understand indexing and execution plans.
- [ ] Create MongoDB database and collections.
- [ ] Practice MongoDB CRUD.
- [ ] Write aggregation pipelines.
- [ ] Practice embedding and referencing.
- [ ] Understand MongoDB transactions.
- [ ] Practice database backup and restore.

---

# 15. Final Quick Revision

- DBMS = Database management software.
- RDBMS = Relational database system.
- Schema = Structure; Instance = Current data.
- Entity = Object; Attribute = Property.
- Primary Key = Unique, non-NULL identifier.
- Foreign Key = Relationship reference.
- SQL = Relational database query language.
- DDL = Structure; DML = Data modification.
- JOIN = Combine related tables.
- Subquery = Query inside query.
- Normalization = Reduce redundancy and anomalies.
- ACID = Atomicity, Consistency, Isolation, Durability.
- Deadlock = Transactions waiting on each other.
- Index = Faster data lookup with storage/write cost.
- View = Virtual table based on query.
- Procedure = Stored SQL program/unit.
- EXPLAIN = Execution plan.
- NoSQL = Non-relational database family.
- MongoDB = Document database.
- Aggregation = Data processing pipeline.
- SQL Injection = Malicious query manipulation.
- Backup = Recoverable copy of data.
- RPO = Acceptable data loss.
- RTO = Acceptable recovery time.

---

# 16. Final DBMS MCQ Test

**Q1. DBMS ka main purpose kya hai?**

A. Only coding  
B. Data manage karna  
C. Only designing  
D. Only networking

**Q2. Primary Key mein kya allowed nahi hai?**

A. Unique values  
B. NULL values  
C. Integer values  
D. Text values

**Q3. Degree ka meaning kya hai?**

A. Number of rows  
B. Number of columns  
C. Number of databases  
D. Number of users

**Q4. DDL command ka example kaunsa hai?**

A. INSERT  
B. UPDATE  
C. CREATE  
D. SELECT

**Q5. GROUP BY ke baad groups filter karne ke liye kya use hota hai?**

A. WHERE  
B. HAVING  
C. ORDER BY  
D. LIMIT

**Q6. LEFT JOIN kya return karta hai?**

A. Only right table rows  
B. All left rows and matching right rows  
C. Only matching rows  
D. Cartesian product

**Q7. 2NF kis dependency ko remove karta hai?**

A. Partial dependency  
B. Multivalued dependency  
C. Join dependency  
D. No dependency

**Q8. ACID mein D ka matlab kya hai?**

A. Data  
B. Durability  
C. Dependency  
D. Database

**Q9. MongoDB kis type ka database hai?**

A. Graph  
B. Document  
C. Relational  
D. Only Key-Value

**Q10. RTO kya define karta hai?**

A. Acceptable data loss  
B. Recovery time target  
C. Password strength  
D. Query speed
