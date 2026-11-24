# 20. NoSQL Database and MongoDB

## 1. What is NoSQL?

**NoSQL** ka meaning commonly "Not Only SQL" hota hai.

NoSQL databases aise databases hote hain jo traditional relational tables ke alawa different data models use karte hain.

Inmein data store karne ke common formats hain:

- Document
- Key-Value
- Column-Family
- Graph

NoSQL databases flexible data structures aur distributed applications ke liye useful ho sakte hain.

## 2. Why Do We Need NoSQL?

Traditional relational databases mein data tables, rows aur columns mein organize hota hai.

Lekin modern applications mein:

- Large amounts of data.
- Frequently changing data structures.
- Flexible schema requirements.
- Distributed systems.
- High-volume read/write workloads.

jaise requirements ho sakti hain.

NoSQL databases in requirements ko handle karne ke different approaches provide karte hain.

**Important:** NoSQL ka matlab SQL ya relational databases se better hona nahi hai. Dono ke apne use cases hain.

## 3. Types of NoSQL Databases

NoSQL databases ke 4 major types hain.

### A. Document Database

Data documents ke form mein store hota hai, commonly JSON-like format mein.

Example:

```json
{
  "_id": 101,
  "name": "Rahul",
  "age": 22,
  "city": "Delhi"
}
```

Examples:

- MongoDB
- CouchDB

Useful for:

- User profiles.
- E-commerce products.
- Content management.
- Web applications.

### B. Key-Value Database

Data key-value pairs mein store hota hai.

Example:

```text
user:101 → Rahul
user:102 → Aman
user:103 → Ravi
```

Examples:

- Redis
- Amazon DynamoDB (supports key-value and document models)

Useful for:

- Caching.
- Session storage.
- Fast lookups.

### C. Column-Family Database

Data column families ke form mein organize hota hai.

Examples:

- Apache Cassandra
- HBase

Useful for:

- Large distributed datasets.
- High-volume writes.
- Distributed data workloads.

### D. Graph Database

Data nodes aur relationships ke form mein store hota hai.

Example:

```text
Rahul ---- FRIEND ---- Aman
  |
  |
FOLLOWS
  |
  |
 Ravi
```

Examples:

- Neo4j
- Amazon Neptune

Useful for:

- Social networks.
- Recommendation systems.
- Relationship analysis.
- Fraud detection.

## 4. What is MongoDB?

**MongoDB** ek popular NoSQL document database hai.

Ismein data BSON documents ke form mein store hota hai.

BSON ka full form hai:

**Binary JSON**

MongoDB documents JSON-like structure mein dikhte hain, lekin internally BSON representation use hoti hai.

Example:

```javascript
{
  _id: ObjectId("..."),
  name: "Rahul",
  age: 22,
  city: "Delhi"
}
```

MongoDB ka official website: https://www.mongodb.com/

## 5. MongoDB Basic Structure

MongoDB mein data organization:

```text
MongoDB Server
     |
     v
  Database
     |
     v
  Collection
     |
     v
  Document
     |
     v
   Fields
```

| MongoDB    | SQL Database                |
| ---------- | --------------------------- |
| Database   | Database                    |
| Collection | Table                       |
| Document   | Row                         |
| Field      | Column                      |
| `_id`      | Primary-key-like identifier |

Example:

```text
Database: CollegeDB

Collection: Students

Document:
{
  _id: 1,
  name: "Rahul",
  age: 22
}
```

## 6. MongoDB vs JSON vs BSON

### JSON

JSON ek text-based data interchange format hai.

Example:

```json
{
  "name": "Rahul",
  "age": 22
}
```

### BSON

BSON JSON-like documents ka binary representation hai.

Features:

- Binary format.
- Additional data types.
- Efficient internal processing.
- Document size and type information.

**Difference:**

| JSON              | BSON                                            |
| ----------------- | ----------------------------------------------- |
| Text format       | Binary format                                   |
| Human-readable    | Directly human-readable nahi                    |
| Common data types | Additional types support                        |
| Data interchange  | MongoDB internal storage/communication mein use |

## 7. Installing and Accessing MongoDB

MongoDB use karne ke common options:

1. MongoDB Atlas – Cloud database service.
2. MongoDB Community Server – Local installation.
3. MongoDB Shell (`mongosh`) – Command-line interface.
4. MongoDB Compass – GUI tool.

Official resources:

- MongoDB: https://www.mongodb.com/
- MongoDB Atlas: https://www.mongodb.com/products/platform/atlas
- MongoDB Compass: https://www.mongodb.com/products/tools/compass
- MongoDB Shell: https://www.mongodb.com/docs/mongodb-shell/

MERN development mein Atlas ya local MongoDB use kar sakte ho.

## 8. Creating and Selecting a Database

MongoDB Shell:

```javascript
use CollegeDB
```

Ye database select karta hai. Database generally tab actually create hota hai jab usmein data store kiya jata hai.

Current database:

```javascript
db;
```

All databases:

```javascript
show dbs
```

## 9. Creating a Collection

```javascript
db.createCollection("students");
```

Collections list:

```javascript
show collections
```

MongoDB collection ko first insert ke through automatically bhi create kar sakta hai.

## 10. Insert Documents – CREATE

### Insert One

```javascript
db.students.insertOne({
  name: "Rahul",
  age: 22,
  city: "Delhi",
});
```

### Insert Many

```javascript
db.students.insertMany([
  {
    name: "Aman",
    age: 23,
    city: "Noida",
  },
  {
    name: "Ravi",
    age: 21,
    city: "Meerut",
  },
]);
```

MongoDB automatically `_id` generate karta hai agar document mein `_id` provide nahi kiya gaya ho.

## 11. Read Documents – READ

### Find All

```javascript
db.students.find();
```

### Find One

```javascript
db.students.findOne({
  name: "Rahul",
});
```

### Find by Condition

```javascript
db.students.find({
  age: 22,
});
```

### Projection

Sirf selected fields:

```javascript
db.students.find({}, { name: 1, age: 1, _id: 0 });
```

`1` means include field; `0` means exclude field. `_id` ko exclude karne ka special exception hai.

## 12. MongoDB Query Operators

### Comparison Operators

| Operator | Meaning                      |
| -------- | ---------------------------- |
| `$eq`    | Equal                        |
| `$ne`    | Not equal                    |
| `$gt`    | Greater than                 |
| `$gte`   | Greater than or equal        |
| `$lt`    | Less than                    |
| `$lte`   | Less than or equal           |
| `$in`    | Value list mein present      |
| `$nin`   | Value list mein present nahi |

Example:

```javascript
db.students.find({
  age: { $gt: 20 },
});
```

Multiple values:

```javascript
db.students.find({
  city: { $in: ["Delhi", "Noida"] },
});
```

### Logical Operators

| Operator | Meaning                     |
| -------- | --------------------------- |
| `$and`   | All conditions true         |
| `$or`    | At least one condition true |
| `$not`   | Condition negate            |
| `$nor`   | All conditions false        |

Example:

```javascript
db.students.find({
  $or: [{ city: "Delhi" }, { age: 25 }],
});
```

## 13. Update Documents – UPDATE

### updateOne()

```javascript
db.students.updateOne({ name: "Rahul" }, { $set: { age: 23 } });
```

### updateMany()

```javascript
db.students.updateMany({ city: "Delhi" }, { $set: { status: "active" } });
```

### Common Update Operators

| Operator    | Purpose                       |
| ----------- | ----------------------------- |
| `$set`      | Field value set/update        |
| `$unset`    | Field remove                  |
| `$inc`      | Number increase/decrease      |
| `$push`     | Array mein element add        |
| `$pull`     | Matching array element remove |
| `$addToSet` | Unique element add            |

Example:

```javascript
db.students.updateOne({ name: "Rahul" }, { $inc: { age: 1 } });
```

## 14. Delete Documents – DELETE

### deleteOne()

```javascript
db.students.deleteOne({
  name: "Rahul",
});
```

### deleteMany()

```javascript
db.students.deleteMany({
  city: "Delhi",
});
```

Delete all documents:

```javascript
db.students.deleteMany({});
```

**Warning:** `deleteMany({})` collection ke saare documents delete kar sakta hai. Execute karne se pehle filter carefully check karo.

## 15. MongoDB CRUD Operations

CRUD ka meaning:

- C – Create
- R – Read
- U – Update
- D – Delete

| Operation | MongoDB Method            |
| --------- | ------------------------- |
| Create    | insertOne(), insertMany() |
| Read      | find(), findOne()         |
| Update    | updateOne(), updateMany() |
| Delete    | deleteOne(), deleteMany() |

## 16. MongoDB Data Types

MongoDB BSON mein multiple data types support karta hai.

| Data Type  | Example                           |
| ---------- | --------------------------------- |
| String     | `"Rahul"`                         |
| Double     | `22.5`                            |
| Int32      | `22`                              |
| Int64      | Large integer                     |
| Boolean    | `true`                            |
| Null       | `null`                            |
| Array      | `[10, 20, 30]`                    |
| Object     | `{city: "Delhi"}`                 |
| ObjectId   | `ObjectId("...")`                 |
| Date       | `ISODate("2026-11-06T00:00:00Z")` |
| Decimal128 | Precise decimal values            |
| Binary     | Binary data                       |

## 17. Embedded Documents and Arrays

MongoDB documents ke andar nested documents aur arrays store kar sakta hai.

### Embedded Document

```javascript
{
  name: "Rahul",
  address: {
    city: "Delhi",
    pincode: 110001
  }
}
```

Access:

```javascript
db.students.find({
  "address.city": "Delhi",
});
```

### Array

```javascript
{
  name: "Rahul",
  skills: ["HTML", "CSS", "JavaScript"]
}
```

Search:

```javascript
db.students.find({
  skills: "JavaScript",
});
```

**Benefit:** Related data ko ek document mein organize kar sakte hain.

## 18. MongoDB Relationships

MongoDB mein related data ko do common methods se represent kar sakte hain.

### A. Embedding

Related data same document ke andar store hota hai.

```javascript
{
  name: "Rahul",
  address: {
    city: "Delhi",
    pincode: 110001
  }
}
```

Useful when:

- Data frequently together read hota hai.
- Relationship one-to-one ya one-to-few ho.
- Related data document ke saath naturally belong karta ho.

### B. Referencing

Related document ka ID store karte hain.

Students:

```javascript
{
  _id: 1,
  name: "Rahul",
  courseId: 101
}
```

Courses:

```javascript
{
  _id: 101,
  courseName: "MERN Stack"
}
```

Useful when:

- Data large ya independently managed ho.
- Relationship many-to-many ho.
- Data multiple documents mein reuse hota ho.

**Important:** MongoDB mein embedding aur referencing ka choice use case par depend karta hai.

## 19. MongoDB Aggregation

Aggregation ka use data processing aur analysis ke liye hota hai.

Aggregation pipeline multiple stages mein data process karti hai.

Example:

```javascript
db.students.aggregate([
  {
    $match: { city: "Delhi" },
  },
  {
    $group: {
      _id: "$city",
      totalStudents: { $sum: 1 },
    },
  },
]);
```

### Important Aggregation Stages

| Stage      | Purpose                                   |
| ---------- | ----------------------------------------- |
| `$match`   | Documents filter                          |
| `$group`   | Grouping                                  |
| `$project` | Fields select/reshape                     |
| `$sort`    | Sorting                                   |
| `$limit`   | Limit results                             |
| `$skip`    | Skip results                              |
| `$unwind`  | Array elements separate                   |
| `$lookup`  | Another collection se join-like operation |
| `$count`   | Documents count                           |

### Example – Sort and Limit

```javascript
db.students.aggregate([{ $sort: { age: -1 } }, { $limit: 5 }]);
```

## 20. MongoDB Indexing

Indexing queries ko fast karne mein help karti hai.

### Create Index

```javascript
db.students.createIndex({
  email: 1,
});
```

### Compound Index

```javascript
db.students.createIndex({
  city: 1,
  age: -1,
});
```

### Unique Index

```javascript
db.students.createIndex({ email: 1 }, { unique: true });
```

### View Indexes

```javascript
db.students.getIndexes();
```

### Explain Query

```javascript
db.students
  .find({
    email: "abc@gmail.com",
  })
  .explain("executionStats");
```

**Remember:** Index reads improve kar sakta hai, lekin storage aur write operations par maintenance cost add karta hai.

## 21. MongoDB Transactions

Transaction multiple database operations ko ek logical unit mein execute karne mein help karti hai.

Example:

Bank transfer:

1. Sender ka balance decrease.
2. Receiver ka balance increase.
3. Dono operations successful hone chahiye.

MongoDB transactions multi-document operations ke liye support karti hain.

Important:

- Multi-document transactions ke liye replica set ya sharded cluster required hota hai.
- Standalone MongoDB deployment mein multi-document transactions supported nahi hoti.
- Single-document writes atomic hoti hain.

Transactions unnecessary use karne se performance overhead aa sakta hai.

## 22. MongoDB Security

Important security practices:

1. Authentication enable karo.
2. Strong passwords use karo.
3. Role-Based Access Control (RBAC) use karo.
4. Network access restrict karo.
5. TLS encryption use karo.
6. Database credentials environment variables mein rakho.
7. Regular backups lo.
8. Database ko unnecessarily public internet par expose mat karo.

Example environment variable:

```env
MONGODB_URI=mongodb_connection_string
```

Node.js mein:

```javascript
const uri = process.env.MONGODB_URI;
```

Actual password ya connection string GitHub par upload nahi karni chahiye.

## 23. MongoDB in MERN Stack

MERN ka full form:

- M – MongoDB
- E – Express.js
- R – React.js
- N – Node.js

Architecture:

```text
        React.js
        Frontend
           |
           v
       Express.js
           |
           v
        Node.js
           |
           v
        MongoDB
         Database
```

Example flow:

1. User React form fill karta hai.
2. React API request send karta hai.
3. Express route request receive karta hai.
4. Node.js backend logic execute karta hai.
5. Mongoose MongoDB se communicate karta hai.
6. MongoDB result return karta hai.
7. Backend response React ko send karta hai.

**Important:** Browser/frontend ko directly database credentials dekar MongoDB se connect nahi karna chahiye. Backend API ke through database access hota hai.

## 24. Mongoose Introduction

**Mongoose** Node.js ke liye MongoDB object modeling library hai.

Ye provide karta hai:

- Schema definition.
- Models.
- Validation.
- Middleware/hooks.
- Query helpers.
- Relationships ke liye populate.

Example:

```javascript
const mongoose = require("mongoose");

const studentSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
    unique: true,
  },
  age: {
    type: Number,
    min: 1,
  },
});

const Student = mongoose.model("Student", studentSchema);
```

Insert:

```javascript
const student = await Student.create({
  name: "Rahul",
  email: "rahul@gmail.com",
  age: 22,
});
```

Find:

```javascript
const students = await Student.find();
```

Find by ID:

```javascript
const student = await Student.findById(id);
```

Update:

```javascript
await Student.findByIdAndUpdate(id, { age: 23 }, { runValidators: true });
```

Delete:

```javascript
await Student.findByIdAndDelete(id);
```

**Note:** Mongoose `unique: true` ko generally MongoDB unique index declare karne ke liye use karta hai; ye normal validation rule nahi hai. Duplicate values par MongoDB duplicate-key error de sakta hai.

## 25. MongoDB Advantages

1. Flexible document structure.
2. JSON-like data representation.
3. Nested documents aur arrays support.
4. Horizontal scaling through sharding.
5. Replication and high availability.
6. Aggregation framework.
7. MERN applications ke saath easy integration.
8. Different data structures ke liye suitable.

## 26. MongoDB Disadvantages

1. Flexible schema se inconsistent data ka risk.
2. Poor document design se performance problems.
3. Large indexes extra storage lete hain.
4. Complex joins ke liye relational DBMS kabhi better fit ho sakta hai.
5. Transactions aur distributed operations planning require karte hain.
6. Schema validation aur data consistency carefully manage karni padti hai.

## 27. Common Mistakes

1. MongoDB ko SQL database samajhna.
2. Collection aur document confuse karna.
3. BSON ko normal JSON samajhna.
4. Har relationship mein embedding use karna.
5. Har relationship mein referencing use karna.
6. Har field par index bana dena.
7. MongoDB transactions ko standalone server par multi-document transactions ke liye available samajhna.
8. Mongoose `unique` ko normal validator samajhna.
9. Connection string GitHub par upload kar dena.
10. React frontend se directly database connect karna.

## 28. Interview Questions and Answers

**Q1. What is NoSQL?**

NoSQL databases relational tables ke alawa document, key-value, column-family aur graph jaise data models use karte hain.

**Q2. What is MongoDB?**

MongoDB ek NoSQL document database hai jo BSON documents store karta hai.

**Q3. What is BSON?**

BSON ka full form Binary JSON hai. Ye MongoDB ka binary document representation hai.

**Q4. What is a Collection?**

Collection MongoDB mein documents ka group hota hai; SQL table se conceptually similar hai.

**Q5. What is a Document?**

Document MongoDB ka individual data record hota hai.

**Q6. What is `_id`?**

`_id` document ka unique identifier field hota hai. Agar provide na ho, MongoDB normally ObjectId generate karta hai.

**Q7. What is CRUD?**

Create, Read, Update and Delete.

**Q8. What is Aggregation?**

Aggregation multiple pipeline stages ke through data process aur analyze karti hai.

**Q9. What is Embedding?**

Related data ko same document ke andar store karna.

**Q10. What is Referencing?**

Related document ka ID store karke usse connect karna.

**Q11. What is Mongoose?**

Node.js ke liye MongoDB object modeling library.

**Q12. What is Sharding?**

Large data ko multiple servers/shards mein distribute karne ki technique.

**Q13. What is Replication?**

Data ki copies multiple members par maintain karna, commonly high availability ke liye.

**Q14. Does MongoDB support transactions?**

Yes. Multi-document transactions replica sets aur sharded clusters par supported hain.

**Q15. What is the default MongoDB index?**

`_id` field par unique index.

## 29. Practical Tasks

1. MongoDB database `CollegeDB` create/use karo.
2. `students` collection banao.
3. 5 student documents insert karo.
4. `find()` aur `findOne()` practice karo.
5. `$gt`, `$lt`, `$in` operators use karo.
6. `$set` aur `$inc` se update karo.
7. `deleteOne()` aur `deleteMany()` practice karo.
8. Embedded address document banao.
9. Aggregation se city-wise student count nikalo.
10. Email par unique index banao.
11. Mongoose se Student model create karo.
12. Express API ke through MongoDB mein student insert karo.

## 30. Quick Revision

| Term        | Meaning                          |
| ----------- | -------------------------------- |
| NoSQL       | Non-relational data models       |
| MongoDB     | Document database                |
| BSON        | Binary JSON                      |
| Database    | Collections ka group             |
| Collection  | Documents ka group               |
| Document    | Individual record                |
| Field       | Document ki property             |
| CRUD        | Create, Read, Update, Delete     |
| Embedding   | Same document mein related data  |
| Referencing | ID se related data connect       |
| Aggregation | Data processing pipeline         |
| Index       | Faster data retrieval            |
| Sharding    | Data distribution                |
| Replication | Data copies maintain karna       |
| Mongoose    | Node.js MongoDB modeling library |
| `_id`       | Unique document identifier       |

**Remember:** MongoDB MERN Stack ka database hai. MongoDB documents store karta hai, Mongoose Node.js se MongoDB interaction ko organize karta hai, aur Express APIs ke through frontend ko data provide karta hai.

## 31. MCQ Practice – 10 Questions

**Q1. NoSQL ka commonly used meaning kya hai?**

A. No Software Query Language  
B. Not Only SQL  
C. New Operating SQL  
D. Network SQL

**Q2. MongoDB kis type ka database hai?**

A. Document Database  
B. Graph Database only  
C. Relational Database  
D. File System

**Q3. BSON ka full form kya hai?**

A. Binary JSON  
B. Basic SQL Object Network  
C. Binary SQL  
D. Boolean System Object Notation

**Q4. MongoDB mein collection kis ke similar hai?**

A. SQL Table  
B. SQL Column  
C. SQL Database  
D. SQL Index

**Q5. MongoDB mein documents insert karne ke liye kya use hota hai?**

A. insertOne()  
B. findOne()  
C. deleteOne()  
D. dropIndex()

**Q6. MongoDB mein default unique index kis field par hota hai?**

A. name  
B. age  
C. _id  
D. email

**Q7. Aggregation mein filtering ke liye kaunsa stage use hota hai?**

A. $match  
B. $group  
C. $sort  
D. $limit

**Q8. Mongoose kya hai?**

A. CSS Framework  
B. MongoDB Object Modeling Library  
C. Operating System  
D. Programming Language

**Q9. MERN ka M kya represent karta hai?**

A. MySQL  
B. MongoDB  
C. MariaDB  
D. Microsoft SQL

**Q10. MongoDB mein multi-document transactions ke liye kya required hai?**

A. Standalone server only  
B. Replica set ya sharded cluster  
C. HTML page  
D. CSS file

### Answer Key

1-B, 2-A, 3-A, 4-A, 5-A, 6-C, 7-A, 8-B, 9-B, 10-B

---

**Topic 20 Complete – NoSQL and MongoDB.**
