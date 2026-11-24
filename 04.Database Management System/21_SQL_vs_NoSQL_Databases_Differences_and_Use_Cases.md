# 21. SQL vs NoSQL Databases

## 1. Introduction

Databases mainly do broad categories mein samjhe ja sakte hain:

1. **SQL Databases:** Relational databases jo tables, rows aur columns mein data organize karte hain.
2. **NoSQL Databases:** Non-relational data models use karte hain, jaise document, key-value, graph aur column-family.

Examples:

| SQL Databases   | NoSQL Databases |
| --------------- | --------------- |
| MySQL           | MongoDB         |
| PostgreSQL      | Cassandra       |
| SQL Server      | Redis           |
| Oracle Database | Neo4j           |

**Important:** SQL database ka matlab SQL language use karne wala relational DBMS hai. NoSQL databases bhi kuch query languages aur SQL-like interfaces provide kar sakte hain.

## 2. What is SQL Database?

SQL database ek relational database hota hai jo data ko tables mein store karta hai.

Example: Students table

| id  | name  | age | city   |
| --- | ----- | --- | ------ |
| 1   | Rahul | 22  | Delhi  |
| 2   | Aman  | 23  | Noida  |
| 3   | Ravi  | 21  | Meerut |

Data ko SQL queries se access karte hain:

```sql
SELECT *
FROM Students
WHERE age > 21;
```

**Examples:** MySQL, PostgreSQL, SQL Server.

## 3. What is NoSQL Database?

NoSQL database non-relational data models use karta hai.

Example MongoDB document:

```javascript
{
  _id: 101,
  name: "Rahul",
  age: 22,
  city: "Delhi",
  skills: ["HTML", "CSS", "JavaScript"]
}
```

Ismein nested objects aur arrays naturally store ho sakte hain.

**Examples:** MongoDB, Redis, Cassandra, Neo4j.

## 4. SQL vs NoSQL – Main Differences

| Feature          | SQL                                              | NoSQL                                   |
| ---------------- | ------------------------------------------------ | --------------------------------------- |
| Data Model       | Relational                                       | Non-relational models                   |
| Structure        | Tables                                           | Documents, key-value, graph, columns    |
| Schema           | Generally predefined                             | Often flexible                          |
| Query Language   | SQL                                              | Database-specific APIs/languages        |
| Relationships    | JOINs and foreign keys                           | Embedding, references, graph edges etc. |
| Transactions     | Strong transaction support                       | Varies by database                      |
| Scaling          | Commonly vertical; horizontal options also exist | Often designed for distributed scaling  |
| Data Consistency | Commonly strong ACID support                     | Varies by system and configuration      |
| Examples         | MySQL, PostgreSQL                                | MongoDB, Redis, Cassandra               |

**Remember:** Ye general comparison hai. Modern SQL aur NoSQL databases dono mein transactions, replication aur horizontal scaling ki different capabilities ho sakti hain.

## 5. Schema Difference

### SQL – Structured Schema

SQL databases mein generally tables aur columns pehle define karte hain.

```sql
CREATE TABLE Students (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  age INT,
  city VARCHAR(100)
);
```

Table ke records defined structure follow karte hain.

### NoSQL – Flexible Schema

MongoDB example:

```javascript
{
  name: "Rahul",
  age: 22
}
```

Another document:

```javascript
{
  name: "Aman",
  age: 23,
  skills: ["JavaScript", "React"]
}
```

Documents same collection mein different fields rakh sakte hain.

**Important:** Flexible schema ka matlab schema bilkul nahi hota, aisa nahi hai. MongoDB mein schema validation aur Mongoose schemas bhi use kar sakte hain.

## 6. Relationship Handling

### SQL Relationships

Relational databases mein relationships foreign keys aur JOINs se establish ki jaati hain.

Example:

Students:

| id  | name  |
| --- | ----- |
| 1   | Rahul |
| 2   | Aman  |

Courses:

| id  | student_id | course |
| --- | ---------- | ------ |
| 101 | 1          | MERN   |
| 102 | 2          | Python |

JOIN:

```sql
SELECT s.name, c.course
FROM Students s
JOIN Courses c
ON s.id = c.student_id;
```

### NoSQL Relationships

MongoDB mein two common approaches:

**A. Embedding**

```javascript
{
  name: "Rahul",
  address: {
    city: "Delhi",
    pincode: 110001
  }
}
```

**B. Referencing**

```javascript
{
  name: "Rahul",
  courseId: 101
}
```

Related document ko ID se refer karte hain.

MongoDB mein `$lookup` aggregation stage JOIN-like operation provide karti hai.

## 7. Scaling – Vertical vs Horizontal

### Vertical Scaling

Ek server ki capacity increase karna.

Example:

- More RAM.
- More CPU.
- Faster storage.

```text
Small Server
     |
     v
Powerful Server
```

### Horizontal Scaling

Multiple servers add karke workload distribute karna.

```text
       Application
            |
      Load Balancer
       /    |    \
      v     v     v
   Server Server Server
```

SQL aur NoSQL dono systems vertical aur horizontal scaling support kar sakte hain, lekin implementation aur complexity differ karti hai.

MongoDB sharding ke through horizontal scaling support karta hai.

## 8. ACID vs BASE

### ACID

ACID ka full form:

- Atomicity
- Consistency
- Isolation
- Durability

Ye database transactions ki important properties hain.

### BASE

BASE commonly distributed systems ke design philosophy ko describe karta hai:

- Basically Available
- Soft State
- Eventual Consistency

**Meaning:**

1. Basically Available: System availability maintain karne par focus karta hai.
2. Soft State: Replicas ka state temporary differences dikha sakta hai.
3. Eventual Consistency: Agar updates stop ho jayein aur system converge kare, to replicas eventually consistent ho sakte hain.

**Important:** BASE ko har NoSQL database ki mandatory property nahi samajhna chahiye. NoSQL systems consistency ke different models support karte hain.

## 9. CAP Theorem

CAP theorem distributed data systems ke baare mein important concept hai.

CAP stands for:

- Consistency
- Availability
- Partition Tolerance

### C – Consistency

Har successful read latest committed write ko observe kare, as defined by the system's consistency guarantee.

### A – Availability

Har request ko non-failing node se response mile, even if response latest data na ho.

### P – Partition Tolerance

Network partition hone par system operate karne ki ability.

**Important Concept:**

Network partition ke time distributed system ko consistency aur availability ke beech trade-off karna pad sakta hai.

- CP: Partition ke time consistency preserve karne ke liye kuch requests reject/delay ho sakti hain.
- AP: Partition ke time availability maintain kar sakta hai, lekin temporary stale data possible hai.

CAP ka matlab ye nahi hai ki system normal conditions mein sirf C, A ya P mein se ek hi choose kar sakta hai.

## 10. When Should We Use SQL?

SQL databases generally suitable hain jab:

1. Data highly structured ho.
2. Complex JOINs required hon.
3. Relationships important hon.
4. Strong transactional consistency required ho.
5. Data integrity constraints important hon.
6. Financial transactions handle karni hon.

Examples:

- Banking systems.
- Payroll systems.
- Inventory management.
- Reservation systems.
- Enterprise applications.

## 11. When Should We Use NoSQL?

NoSQL databases useful ho sakte hain jab:

1. Data structure flexible ho.
2. Nested documents naturally fit hote hon.
3. Large distributed workloads hon.
4. Rapidly changing application requirements hon.
5. Specific workload ke liye high horizontal scalability required ho.

Examples:

- Content management.
- Product catalogs.
- User profiles.
- Caching.
- Event data.
- Social applications.

**Note:** Use-case ke according SQL bhi in applications ke liye suitable ho sakta hai. Technology selection actual requirements par depend karti hai.

## 12. SQL vs NoSQL – Advantages and Disadvantages

### SQL Advantages

- Structured data.
- Strong relational model.
- Mature transaction support.
- Complex joins and queries.
- Constraints and data integrity.

### SQL Disadvantages

- Schema changes planning require kar sakte hain.
- Complex distributed scaling challenging ho sakti hai.
- Highly nested data ko represent karna less natural ho sakta hai.

### NoSQL Advantages

- Multiple data models.
- Flexible document structures.
- Distributed architecture options.
- Specific workloads ke liye scalable.
- Nested data naturally represent kar sakta hai.

### NoSQL Disadvantages

- Database-specific query languages.
- Flexible schema se inconsistent data ka risk.
- Complex relationships ke liye additional application logic.
- Transaction and consistency behavior system-specific.

## 13. SQL vs NoSQL in MERN Stack

MERN stack mein:

- MongoDB = NoSQL database.
- Express.js = Backend framework.
- React.js = Frontend library.
- Node.js = JavaScript runtime.

Architecture:

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

MERN mein MongoDB choose karne ke reasons:

1. JSON-like documents.
2. JavaScript ecosystem ke saath convenient data handling.
3. Nested objects aur arrays.
4. Mongoose integration.
5. Flexible document modeling.

Example Mongoose schema:

```javascript
const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
    unique: true,
  },
  skills: [String],
});
```

Lekin MERN stack use karne ka matlab ye nahi ki SQL database use nahi kar sakte. Node.js aur Express PostgreSQL/MySQL ke saath bhi work kar sakte hain.

## 14. Can We Use SQL and NoSQL Together?

Yes. Ek application multiple databases use kar sakti hai.

Example:

```text
       Application
            |
       Backend API
        /       \
       v         v
   PostgreSQL   MongoDB
       |         |
   Payments   User Content
```

Possible use cases:

- PostgreSQL: Payments aur financial records.
- MongoDB: Flexible content aur product information.
- Redis: Caching aur sessions.

Is architecture ko polyglot persistence kaha jaata hai.

**Polyglot Persistence:** Different data requirements ke liye different database technologies use karna.

## 15. Common Mistakes

1. SQL ko sirf MySQL samajhna.
2. NoSQL ko completely schema-less samajhna.
3. NoSQL ko always faster samajhna.
4. SQL ko horizontal scaling support na karne wala samajhna.
5. Har NoSQL database ko MongoDB jaisa samajhna.
6. Har NoSQL database ko BASE-only samajhna.
7. CAP theorem ko incorrectly interpret karna.
8. MongoDB mein relationships impossible samajhna.
9. MERN mein SQL database use nahi ho sakta, aisa samajhna.

## 16. Interview Questions and Answers

**Q1. What is the main difference between SQL and NoSQL?**

SQL relational tables use karta hai, jabki NoSQL document, key-value, graph aur column-family jaise data models use karta hai.

**Q2. Is MongoDB SQL or NoSQL?**

MongoDB NoSQL document database hai.

**Q3. Which database is better, SQL or NoSQL?**

Koi universal winner nahi. Requirements, data model, transactions, queries aur scalability ke according choose karte hain.

**Q4. What is schema flexibility?**

Documents ya records mein different fields allow karna, subject to database validation rules.

**Q5. What is horizontal scaling?**

Multiple servers add karke workload distribute karna.

**Q6. What is vertical scaling?**

Existing server ki hardware capacity increase karna.

**Q7. What is CAP theorem?**

Distributed systems mein network partition ke time consistency aur availability ke trade-off ko explain karta hai.

**Q8. What is BASE?**

Basically Available, Soft State, Eventual Consistency.

**Q9. Can MongoDB perform JOIN-like operations?**

Yes, MongoDB aggregation ka `$lookup` stage JOIN-like operation provide karta hai.

**Q10. Can SQL and NoSQL databases be used together?**

Yes. Application different requirements ke liye multiple databases use kar sakti hai.

**Q11. Is MongoDB always faster than MySQL?**

No. Performance workload, schema design, queries, indexes aur configuration par depend karti hai.

**Q12. What is Polyglot Persistence?**

Ek application mein different requirements ke according multiple database technologies use karna.

## 17. Practical Tasks

1. SQL aur NoSQL ke data models compare karo.
2. Students table ko MongoDB document mein represent karo.
3. SQL foreign key relationship banao.
4. MongoDB mein embedding aur referencing implement karo.
5. MongoDB `$lookup` practice karo.
6. Vertical aur horizontal scaling ka diagram banao.
7. CAP theorem ke CP aur AP examples samjho.
8. Ek MERN application ke liye SQL aur NoSQL selection justify karo.

## 18. Quick Revision

| Concept              | Meaning                                        |
| -------------------- | ---------------------------------------------- |
| SQL                  | Relational database approach                   |
| NoSQL                | Non-relational data models                     |
| Schema               | Data structure definition                      |
| JOIN                 | Related tables combine karna                   |
| Embedding            | Same document mein related data                |
| Referencing          | IDs se documents connect karna                 |
| Vertical Scaling     | Server capacity increase                       |
| Horizontal Scaling   | More servers add                               |
| ACID                 | Transaction properties                         |
| BASE                 | Distributed system design philosophy           |
| CAP                  | Consistency, Availability, Partition Tolerance |
| Polyglot Persistence | Multiple database technologies                 |

**Remember:** SQL vs NoSQL ka decision popularity ke basis par nahi, application ki actual data aur business requirements ke basis par lena chahiye.

## 19. MCQ Practice – 10 Questions

**Q1. SQL databases generally kis model par based hote hain?**

A. Relational  
B. Graph only  
C. Key-Value only  
D. File System

**Q2. MongoDB kis category mein aata hai?**

A. SQL  
B. NoSQL  
C. Operating System  
D. Programming Language

**Q3. SQL database mein data generally kaise organize hota hai?**

A. Tables  
B. Only images  
C. Only graphs  
D. Only files

**Q4. Horizontal scaling ka meaning kya hai?**

A. RAM remove karna  
B. More servers add karna  
C. Table delete karna  
D. Database rename karna

**Q5. Vertical scaling ka meaning kya hai?**

A. Existing server capacity increase karna  
B. Multiple databases delete karna  
C. Network disconnect karna  
D. Data encrypt karna

**Q6. ACID ka A kya hai?**

A. Availability  
B. Atomicity  
C. Accuracy  
D. Automation

**Q7. CAP theorem mein P kya represent karta hai?**

A. Performance  
B. Partition Tolerance  
C. Programming  
D. Processing

**Q8. MongoDB mein JOIN-like operation ke liye kya use hota hai?**

A. $lookup  
B. $delete  
C. $remove  
D. $connect

**Q9. Different databases ko ek application mein use karna kya kehlata hai?**

A. Normalization  
B. Polyglot Persistence  
C. Encapsulation  
D. Compilation

**Q10. SQL vs NoSQL mein best choice kis basis par honi chahiye?**

A. Sirf popularity  
B. Sirf database name  
C. Application requirements  
D. Sirf programming language

### Answer Key

1-A, 2-B, 3-A, 4-B, 5-A, 6-B, 7-B, 8-A, 9-B, 10-C

---

**Topic 21 Complete – SQL vs NoSQL.**
