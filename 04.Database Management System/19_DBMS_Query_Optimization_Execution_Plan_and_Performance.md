# 19. Query Optimization in DBMS

## 1. What is Query Optimization?

**Query Optimization** DBMS ki process hai jisme database kisi SQL query ko execute karne ka efficient method choose karta hai.

Iska main goal hai:

- Query execution time reduce karna.
- Unnecessary data scanning avoid karna.
- CPU aur memory usage optimize karna.
- Disk I/O reduce karna.
- Overall database performance improve karna.

Example:

```sql
SELECT *
FROM Students
WHERE city = 'Delhi';
```

Database decide karega ki:

- Full table scan kare.
- Available index use kare.
- Ya koi doosra efficient execution method choose kare.

**Important:** Query optimizer generally automatically best estimated execution plan choose karta hai, lekin har situation mein actual fastest plan ki guarantee nahi hoti.

## 2. Why is Query Optimization Important?

Maan lo database mein 10 lakh records hain.

Agar query unnecessary columns aur records scan karti hai, to execution slow ho sakta hai.

Optimization se:

1. Response time improve hota hai.
2. Server resources save hote hain.
3. Heavy applications better perform karti hain.
4. Multiple users ko efficiently handle kiya ja sakta hai.
5. Database scalability improve hoti hai.

## 3. What is a Query Execution Plan?

**Query Execution Plan** ek roadmap hota hai jo batata hai ki database query ko execute kaise karega.

Example:

```sql
EXPLAIN
SELECT *
FROM Students
WHERE email = 'abc@gmail.com';
```

Execution plan mein ye details ho sakti hain:

- Table Scan
- Index Scan
- Index Seek
- Join method
- Estimated rows
- Estimated cost
- Sorting operation

Exact output DBMS ke according different hota hai.

## 4. Types of Query Execution

### A. Full Table Scan

Database table ke records ko scan karta hai.

Example:

```sql
SELECT *
FROM Students;
```

Ya aisi query jahan suitable index available nahi hai.

Useful ho sakta hai:

- Small tables mein.
- Jab large percentage of rows required hon.
- Jab optimizer ko full scan cheaper lage.

### B. Index Scan

Database index structure ko scan karta hai aur required records locate kar sakta hai.

Example:

```sql
SELECT *
FROM Students
WHERE email = 'abc@gmail.com';
```

Agar suitable index available hai, to optimizer uska use kar sakta hai.

### C. Index Seek

Kuch DBMS, especially SQL Server, mein index seek ka matlab hai index key ki help se specific range ya matching entries locate karna.

**Note:** Index scan hamesha bad aur index seek hamesha good nahi hota. Query, data distribution aur execution plan ko samajhna zaroori hai.

## 5. Query Optimization Techniques

### 1. Avoid SELECT *

Unnecessary columns retrieve mat karo.

Wrong:

```sql
SELECT *
FROM Students;
```

Better:

```sql
SELECT name, email
FROM Students;
```

Benefit:

- Less data transfer.
- Less memory usage in application.
- Covering/index-only access ka chance improve ho sakta hai.

### 2. Use Proper Indexes

Frequently searched columns par suitable index banao.

```sql
CREATE INDEX idx_email
ON Students(email);
```

Query:

```sql
SELECT *
FROM Students
WHERE email = 'abc@gmail.com';
```

Index ka actual benefit execution plan se verify karo.

### 3. Avoid Unnecessary DISTINCT

Wrong:

```sql
SELECT DISTINCT city
FROM Students;
```

Agar duplicates remove karna required nahi hai, to `DISTINCT` avoid karo.

`DISTINCT` sorting ya hashing jaisi additional processing require kar sakta hai.

### 4. Use WHERE to Filter Rows

Unnecessary records retrieve mat karo.

Wrong:

```sql
SELECT *
FROM Students;
```

Better:

```sql
SELECT name, age
FROM Students
WHERE age > 20;
```

### 5. Use LIMIT / Pagination

Bahut saare records ek saath retrieve mat karo.

```sql
SELECT *
FROM Students
LIMIT 10;
```

Large applications mein pagination use hoti hai.

**Note:** `LIMIT` MySQL/PostgreSQL syntax hai; SQL Server mein `TOP` ya `OFFSET/FETCH` use hota hai.

### 6. Avoid Unnecessary Subqueries

Kuch situations mein JOIN ya EXISTS better plan provide kar sakta hai.

Subquery:

```sql
SELECT name
FROM Students
WHERE department_id IN (
    SELECT id
    FROM Departments
    WHERE department_name = 'IT'
);
```

Alternative JOIN:

```sql
SELECT s.name
FROM Students s
JOIN Departments d
ON s.department_id = d.id
WHERE d.department_name = 'IT';
```

Dono ka result same ho sakta hai, lekin performance execution plan aur data par depend karti hai.

### 7. Use EXISTS for Existence Checks

Agar sirf check karna hai ki related record exist karta hai ya nahi, to `EXISTS` useful ho sakta hai.

```sql
SELECT s.name
FROM Students s
WHERE EXISTS (
    SELECT 1
    FROM Enrollments e
    WHERE e.student_id = s.id
);
```

Optimizer ise efficiently execute kar sakta hai.

### 8. Avoid Functions on Indexed Columns When Possible

Example:

```sql
SELECT *
FROM Students
WHERE YEAR(created_at) = 2026;
```

Column par function lagane se normal index ka use difficult ho sakta hai, depending on DBMS and available expression indexes.

Better range condition:

```sql
SELECT *
FROM Students
WHERE created_at >= '2026-01-01'
AND created_at < '2027-01-01';
```

Isse ordinary index use karne ka better chance ho sakta hai.

### 9. Use Proper JOIN Conditions

JOIN mein suitable indexed columns aur correct conditions use karo.

```sql
SELECT s.name, d.department_name
FROM Students s
JOIN Departments d
ON s.department_id = d.id;
```

JOIN condition missing hone par unintended Cartesian product create ho sakta hai.

### 10. Avoid Unnecessary Sorting

```sql
SELECT *
FROM Students
ORDER BY name;
```

Agar sorting required nahi hai, to `ORDER BY` avoid karo.

Suitable index kuch cases mein sorting cost reduce kar sakta hai.

## 6. Query Optimizer

**Query Optimizer** DBMS ka component hai jo query ke possible execution plans evaluate karke ek efficient plan select karta hai.

Main responsibilities:

1. Query analysis.
2. Possible execution plans generate karna.
3. Available indexes consider karna.
4. Join order decide karna.
5. Join methods select karna.
6. Estimated cost compare karna.
7. Execution plan choose karna.

## 7. Types of Query Optimization

### A. Rule-Based Optimization

Rules ya predefined transformations ki help se query optimize ki jaati hai.

Example:

- Unnecessary conditions simplify karna.
- Selection ko earlier apply karna.
- Unnecessary operations remove karna.

### B. Cost-Based Optimization

Database different execution plans ki estimated cost compare karta hai.

Cost estimate mein ye factors include ho sakte hain:

- CPU cost.
- Disk I/O.
- Memory.
- Number of rows.
- Index availability.
- Data statistics.

Modern relational DBMS generally cost-based optimization use karte hain, often with rule-based transformations too.

## 8. Query Processing Steps

SQL query execute hone ka simplified flow:

```text
SQL Query
    |
    v
Parser and Validation
    |
    v
Query Rewrite
    |
    v
Query Optimizer
    |
    v
Execution Plan
    |
    v
Query Execution Engine
    |
    v
Result
```

**Explanation:**

1. Parser: SQL syntax check karta hai.
2. Validation: Tables, columns aur permissions check hoti hain.
3. Query Rewrite: Query transformations apply ho sakti hain.
4. Optimizer: Efficient execution plan choose karta hai.
5. Execution Engine: Selected plan execute karta hai.
6. Result: Output return hota hai.

Exact internal architecture DBMS-specific hoti hai.

## 9. Join Optimization

Jab multiple tables JOIN hoti hain, database ko decide karna hota hai ki join kaise perform kiya jaye.

### A. Nested Loop Join

Ek table ke records ke liye doosri table mein matching records search kiye jaate hain.

Useful ho sakta hai:

- Small outer table.
- Indexed lookup.

### B. Hash Join

Database ek input ke records se hash table build karta hai aur doosre input se matching records find karta hai.

Useful ho sakta hai:

- Large equality joins.
- Jab suitable index available na ho.

### C. Merge Join

Dono inputs sorted order mein hote hain aur database matching rows merge karta hai.

Useful ho sakta hai:

- Sorted inputs.
- Large joins.

| Join Type   | Main Idea                                       |
| ----------- | ----------------------------------------------- |
| Nested Loop | One input ke records ke liye doosre mein search |
| Hash Join   | Hash table se matching                          |
| Merge Join  | Sorted inputs ko merge karna                    |

Optimizer data aur cost ke according join method choose karta hai.

## 10. Database Statistics

Database statistics data ke baare mein information provide karti hain.

Examples:

- Total rows.
- Distinct values.
- Value distribution.
- NULL values.
- Index statistics.

Optimizer statistics ki help se estimate karta hai ki query kitne records return karegi.

Agar statistics outdated hon, to optimizer poor execution plan choose kar sakta hai.

Statistics update karne ki commands DBMS-specific hoti hain.

## 11. Query Cost

Query cost database ke resources ke estimated usage ko represent karti hai.

Important factors:

- Disk I/O.
- CPU operations.
- Memory usage.
- Network transfer.
- Rows processed.

**Important:** EXPLAIN mein estimated cost usually DBMS-specific internal units mein hoti hai. Isse directly milliseconds samajhna galat hai.

## 12. SQL Query Optimization vs Database Optimization

| Query Optimization             | Database Optimization                             |
| ------------------------------ | ------------------------------------------------- |
| Individual query improve karna | Overall database performance improve karna        |
| SQL structure, indexes, joins  | Configuration, memory, storage, indexes, workload |
| Execution plan focus           | Complete system focus                             |

## 13. Query Optimization in MongoDB

MongoDB mein query performance improve karne ke liye:

### Create Index

```javascript
db.users.createIndex({ email: 1 });
```

### Explain Query

```javascript
db.users
  .find({
    email: "abc@gmail.com",
  })
  .explain("executionStats");
```

Important fields:

- `nReturned`: Returned documents.
- `totalDocsExamined`: Examined documents.
- `totalKeysExamined`: Examined index keys.
- `executionTimeMillis`: Reported execution time.

### Projection

Unnecessary fields return mat karo:

```javascript
db.users.find({ city: "Delhi" }, { name: 1, email: 1, _id: 0 });
```

### Limit

```javascript
db.users.find().limit(10);
```

### Compound Index

```javascript
db.users.createIndex({
  city: 1,
  age: 1,
});
```

### Aggregation Optimization

```javascript
db.orders.aggregate([
  { $match: { status: "delivered" } },
  { $group: { _id: "$userId", total: { $sum: "$amount" } } },
]);
```

Jahan logically possible ho, `$match` ko pipeline ke early stage mein rakhna unnecessary documents process hone se bacha sakta hai.

MongoDB optimizer kuch pipeline stages ko automatically reorder ya optimize bhi kar sakta hai.

## 14. Query Optimization in MERN Stack

MERN applications mein database performance important hai.

Example:

```javascript
const users = await User.find({
  city: "Delhi",
})
  .select("name email")
  .limit(20);
```

Performance improve karne ke methods:

1. Frequently queried fields par suitable indexes.
2. Unnecessary fields retrieve na karna.
3. Pagination use karna.
4. Large data ke liye efficient queries.
5. MongoDB `explain()` se execution analyze karna.
6. N+1 query problems avoid karna.
7. Database connection pooling use karna.
8. Aggregation pipelines efficiently design karna.

**Remember:** Fast backend ke liye sirf fast JavaScript enough nahi; database queries bhi efficient honi chahiye.

## 15. Common Mistakes

1. Har query mein `SELECT *` use karna.
2. Har column par index bana dena.
3. `EXPLAIN` check na karna.
4. Unnecessary ORDER BY aur DISTINCT use karna.
5. Large result sets bina pagination retrieve karna.
6. JOIN condition miss karna.
7. Query cost ko actual milliseconds samajhna.
8. Assume karna ki index always use hoga.
9. Outdated statistics ignore karna.
10. Query performance test kiye bina optimization karna.

## 16. Interview Questions and Answers

**Q1. What is Query Optimization?**

SQL query ko efficiently execute karne ka best estimated method choose karne ki process.

**Q2. What is a Query Optimizer?**

DBMS ka component jo possible execution plans mein se efficient plan choose karta hai.

**Q3. What is EXPLAIN?**

Query ka execution plan inspect karne ke liye use hota hai.

**Q4. What is a Full Table Scan?**

Database table ke records ko scan karta hai, instead of locating records through a selective index lookup.

**Q5. What is Cost-Based Optimization?**

Different execution plans ki estimated cost compare karke plan choose karna.

**Q6. What is a Hash Join?**

Hash table ki help se matching records find karne wala join method.

**Q7. What is a Nested Loop Join?**

Ek input ke records ke liye doosre input mein matching records search karna.

**Q8. Why are database statistics important?**

Optimizer ko rows aur data distribution estimate karne mein help karti hain.

**Q9. Does an index always improve query performance?**

Nahi. Index storage aur write-maintenance cost badhata hai; optimizer full scan bhi choose kar sakta hai.

**Q10. How do you optimize MongoDB queries?**

Suitable indexes, projection, limit, efficient aggregation aur `explain("executionStats")` ka use karke.

## 17. Practical Tasks

1. Students table par email index create karo.
2. `EXPLAIN` se query execution plan check karo.
3. `SELECT *` ko selected columns se replace karo.
4. JOIN query ka execution plan compare karo.
5. MongoDB mein `createIndex()` use karo.
6. MongoDB query par `explain("executionStats")` run karo.
7. Pagination aur limit implement karo.
8. Ek slow query identify karke uski performance improve karo.

## 18. Quick Revision

| Term               | Meaning                                    |
| ------------------ | ------------------------------------------ |
| Query Optimization | Query execution improve karna              |
| Query Optimizer    | Efficient plan choose karne wala component |
| Execution Plan     | Query execute karne ka roadmap             |
| Full Table Scan    | Table records scan karna                   |
| Index Scan         | Index structure scan karna                 |
| Index Seek         | Index se targeted lookup                   |
| Rule-Based         | Rules ke according optimization            |
| Cost-Based         | Estimated cost ke according optimization   |
| Nested Loop Join   | Repeated matching search                   |
| Hash Join          | Hash table based matching                  |
| Merge Join         | Sorted inputs ko merge karna               |
| Statistics         | Data distribution ki information           |
| EXPLAIN            | Execution plan inspect karna               |

**Remember:** Query optimization ka main goal minimum unnecessary resource usage ke saath required result efficiently retrieve karna hai.

## 19. MCQ Practice – 10 Questions

**Q1. Query Optimization ka main purpose kya hai?**

A. Query slow karna  
B. Query performance improve karna  
C. Database delete karna  
D. Table rename karna

**Q2. Query execution plan check karne ke liye kya use hota hai?**

A. EXPLAIN  
B. INSERT  
C. DROP  
D. GRANT

**Q3. Query Optimizer ka kaam kya hai?**

A. HTML generate karna  
B. Execution plan choose karna  
C. User password create karna  
D. Table delete karna

**Q4. Hash Join kis structure ka use karta hai?**

A. Stack  
B. Hash Table  
C. Queue  
D. Linked List only

**Q5. Full Table Scan mein kya hota hai?**

A. Table records scan hote hain  
B. Sirf index delete hota hai  
C. Database close hota hai  
D. Table rename hoti hai

**Q6. Cost-Based Optimization kis basis par plan choose karti hai?**

A. Randomly  
B. Estimated cost  
C. Table name  
D. User name

**Q7. Query mein unnecessary columns avoid karne ke liye kya use karna chahiye?**

A. SELECT *  
B. Specific column names  
C. DROP  
D. TRUNCATE

**Q8. Database statistics kiski help karti hain?**

A. Query Optimizer  
B. Browser  
C. CSS  
D. HTML

**Q9. MongoDB mein query execution analyze karne ke liye kya use hota hai?**

A. explain("executionStats")  
B. dropDatabase()  
C. insertOne() only  
D. renameCollection()

**Q10. Kya index har query ko faster banata hai?**

A. Always  
B. Never  
C. Not necessarily  
D. Sirf DELETE ko

### Answer Key

1-B, 2-A, 3-B, 4-B, 5-A, 6-B, 7-B, 8-A, 9-A, 10-C

---

**Topic 19 Complete – Query Optimization.**
