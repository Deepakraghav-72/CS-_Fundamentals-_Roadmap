# 17. Database Indexing in DBMS

## 1. What is Indexing?

**Indexing** DBMS ki technique hai jo database mein data ko quickly search aur retrieve karne mein help karti hai.

Example: Book mein kisi topic ko find karne ke liye hum index page dekhte hain. Waise hi database index records ko quickly locate karne mein help karta hai.

Without Index:

- Database ko bahut saare records scan karne pad sakte hain.
- Isse query slow ho sakti hai.

With Index:

- Database index ki help se required record tak jaldi pahunch sakta hai.
- Read/search performance improve ho sakti hai.

## 2. Why Do We Need Indexing?

Maan lo `Students` table mein 1 lakh records hain.

```sql
SELECT * FROM Students
WHERE email = 'abc@gmail.com';
```

Agar `email` par index nahi hai, to database ko table ke bahut saare records check karne pad sakte hain.

Agar `email` par suitable index hai, to database matching record ko efficiently locate kar sakta hai.

**Benefits:**

- Faster SELECT queries.
- Faster searching and filtering.
- JOIN operations mein help.
- ORDER BY aur GROUP BY queries mein help, depending on index and query plan.
- Unique values enforce karne mein help.

**Disadvantages:**

- Extra storage space.
- INSERT, UPDATE aur DELETE ke time index maintenance.
- Too many indexes performance ko hurt kar sakte hain.

## 3. Creating an Index in SQL

Basic syntax:

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

Example:

```sql
CREATE INDEX idx_student_email
ON Students(email);
```

Ab database `email` par index use kar sakta hai, agar query planner ko beneficial lage.

Index delete karna:

```sql
DROP INDEX idx_student_email;
```

**Note:** `DROP INDEX` ki exact syntax DBMS ke according change ho sakti hai.

## 4. Types of Indexes

### A. Primary Index

Textbook terminology mein primary index generally ordered data file ke primary key/search key par based index ko refer karta hai.

Important:

- Ye term different DBMS books aur systems mein different meanings mein use ho sakti hai.
- Primary key aur primary index exactly same concept nahi hain.
- Har DBMS primary key ke liye same physical indexing structure use nahi karta.

### B. Secondary Index

Secondary index kisi aise column par banaya gaya index hai jo table ki primary storage ordering ka main key nahi hota.

Example:

```sql
CREATE INDEX idx_student_city
ON Students(city);
```

Ab `city` ke basis par searching improve ho sakti hai.

### C. Clustered Index

Clustered index data rows ki storage organization ko index key ke according arrange karta hai.

Example:

```sql
CREATE CLUSTERED INDEX idx_student_id
ON Students(student_id);
```

**Important:** Clustered index ki implementation DBMS-specific hoti hai.

- SQL Server mein clustered index rows ki storage order define karta hai.
- MySQL InnoDB mein primary key clustered storage ke liye use hoti hai.
- PostgreSQL mein SQL Server jaisa permanently maintained clustered index nahi hota; `CLUSTER` command table ko ek baar reorganize kar sakti hai.

Aam taur par ek table ki ek hi primary clustered storage ordering hoti hai.

### D. Non-Clustered Index

Non-clustered index table ke actual rows se logically separate structure hota hai. Ismein indexed key aur corresponding row tak pahunchne ke liye reference/pointer hota hai.

Example:

```sql
CREATE INDEX idx_student_name
ON Students(name);
```

**General difference:**

| Clustered Index                        | Non-Clustered Index                     |
| -------------------------------------- | --------------------------------------- |
| Data storage organization se connected | Separate index structure                |
| Rows index key ke according organized  | Index entries rows ko locate karti hain |
| Generally one main clustered ordering  | Multiple non-clustered indexes possible |
| Range scans mein useful                | Searching aur filtering mein useful     |

Exact behavior DBMS par depend karta hai.

## 5. Dense and Sparse Index

### Dense Index

Dense index mein har search-key value ya record ke liye index entry hoti hai.

- Searching fast ho sakti hai.
- Index size comparatively bada hota hai.

### Sparse Index

Sparse index mein har record ki entry nahi hoti. Usually selected entries, jaise har data block ke liye ek entry, rakhi jaati hain.

- Storage comparatively kam.
- Search ke liye index entry ke baad data block scan karna pad sakta hai.
- Commonly ordered data file ke saath explain kiya jata hai.

| Dense Index                 | Sparse Index                     |
| --------------------------- | -------------------------------- |
| More index entries          | Fewer index entries              |
| More storage                | Less storage                     |
| Direct lookup more detailed | Block-level search may be needed |

Ye mainly textbook indexing concepts hain; modern DBMS internals mein implementation vary karti hai.

## 6. B-Tree and B+ Tree Index

Database indexes commonly balanced tree structures ka use karte hain.

### B-Tree

B-Tree ek self-balancing search tree hai.

- Keys sorted order mein hoti hain.
- Internal aur leaf nodes dono mein data entries ho sakti hain.
- Search, insertion aur deletion efficient hote hain.

### B+ Tree

B+ Tree, B-Tree family ka structure hai.

- Internal nodes mainly keys aur child pointers store karte hain.
- Actual data entries/record references generally leaf nodes mein hoti hain.
- Leaf nodes linked ho sakte hain.
- Range queries aur ordered traversal ke liye useful hai.

Example:

```text
              [30 | 60]
             /    |    \
            /     |     \
        [10,20] [40,50] [70,80]
```

Ye sirf simplified illustration hai, exact database implementation nahi.

**B-Tree vs B+ Tree**

| B-Tree                                                  | B+ Tree                                |
| ------------------------------------------------------- | -------------------------------------- |
| Data entries internal aur leaf nodes mein ho sakti hain | Data entries generally leaf nodes mein |
| Leaf linking required nahi                              | Leaves commonly linked                 |
| Range traversal comparatively less convenient           | Range queries ke liye efficient        |
| Tree structure                                          | Tree structure                         |

## 7. Hash Index

Hash index hash function ki help se key ko location/bucket se map karta hai.

Example:

```text
email → Hash Function → Bucket → Record
```

Useful for:

- Equality searches.
- Exact-match lookups.

Example:

```sql
SELECT *
FROM Students
WHERE email = 'abc@gmail.com';
```

**Limitations:**

- Range queries ke liye generally suitable nahi.
- Sorted order provide nahi karta.
- Hash collisions handle karne padte hain.
- Har DBMS hash indexes support nahi karta ya same behavior provide nahi karta.

## 8. Single-Column and Composite Index

### Single-Column Index

Sirf ek column par index.

```sql
CREATE INDEX idx_city
ON Students(city);
```

### Composite Index

Do ya more columns par combined index.

```sql
CREATE INDEX idx_city_age
ON Students(city, age);
```

Ye queries mein useful ho sakta hai:

```sql
SELECT *
FROM Students
WHERE city = 'Delhi'
AND age = 22;
```

### Column Order Matters

Index `(city, age)` ka order important hai.

Many database systems mein leftmost-prefix principle apply hota hai:

- `WHERE city = 'Delhi'` — index useful ho sakta hai.
- `WHERE city = 'Delhi' AND age = 22` — index useful ho sakta hai.
- `WHERE age = 22` — same index generally utna useful nahi hota.

Exact index usage query planner aur DBMS par depend karta hai.

## 9. Unique Index

Unique index ensure karta hai ki indexed key values duplicate na hon.

```sql
CREATE UNIQUE INDEX idx_unique_email
ON Students(email);
```

Isse duplicate email values insert karne se roka ja sakta hai.

**Note:** NULL values ke rules DBMS ke according differ karte hain.

## 10. Covering Index

Covering index aisa index hai jisme query ke required columns available hote hain.

Example query:

```sql
SELECT name, city
FROM Students
WHERE student_id = 101;
```

Agar suitable index mein `student_id`, `name` aur `city` available hain, to database ko original table row access karne ki zarurat nahi pad sakti.

Kuch DBMS `INCLUDE` syntax support karte hain:

```sql
CREATE INDEX idx_student_id
ON Students(student_id)
INCLUDE (name, city);
```

Syntax aur support DBMS-specific hain.

## 11. Partial / Filtered Index

Partial index sirf selected rows ke liye create hota hai.

Example:

```sql
CREATE INDEX idx_active_students
ON Students(email)
WHERE status = 'active';
```

Is index mein sirf active students ke records included honge.

**Benefit:** Index size reduce ho sakta hai aur specific queries improve ho sakti hain.

Note: Partial/filtered index support aur syntax DBMS-specific hain.

## 12. Functional / Expression Index

Kisi column ke expression ya function result par index create karna functional indexing kehlata hai.

Example (DBMS support ke according):

```sql
CREATE INDEX idx_lower_email
ON Students(LOWER(email));
```

Ye query mein help kar sakta hai:

```sql
SELECT *
FROM Students
WHERE LOWER(email) = 'abc@gmail.com';
```

## 13. When Should We Create an Index?

Index generally useful ho sakta hai jab:

1. Column frequently WHERE mein use hota ho.
2. Column JOIN conditions mein use hota ho.
3. Column frequently ORDER BY mein use hota ho.
4. Column selective ho, yani values records ko achhe se distinguish karti hon.
5. Query frequently run hoti ho aur performance issue ho.

**Avoid unnecessary indexes when:**

- Table bahut small ho.
- Column mein bahut few distinct values hon aur query planner ko index useful na lage.
- Table par frequent INSERT/UPDATE/DELETE hota ho.
- Index ka use rarely hota ho.
- Extra storage aur maintenance cost justify na hoti ho.

Foreign key columns par index useful ho sakta hai, lekin har DBMS automatically foreign key ke liye index create nahi karta.

## 14. Index Selectivity

**Selectivity** batati hai ki kisi indexed column ki values kitni uniquely records ko identify karti hain.

Example:

| Column | Example values      | Selectivity |
| ------ | ------------------- | ----------- |
| Email  | Mostly unique       | High        |
| City   | Repeated cities     | Medium/Low  |
| Gender | Few repeated values | Low         |

High-selectivity columns exact search ke liye often useful hote hain.

Lekin index ka decision sirf selectivity par nahi hota. Query type, table size, data distribution aur cost estimate bhi matter karte hain.

## 15. How to Check Index Usage?

SQL mein query execution plan check karne ke liye:

```sql
EXPLAIN
SELECT *
FROM Students
WHERE email = 'abc@gmail.com';
```

Kuch DBMS mein:

```sql
EXPLAIN ANALYZE
SELECT *
FROM Students
WHERE email = 'abc@gmail.com';
```

Execution plan se pata chal sakta hai:

- Index Scan
- Index Seek (DBMS-specific terminology)
- Table/Sequential Scan
- Estimated cost
- Actual execution details (supported plans mein)

**Important:** Index create karne ke baad bhi database har query mein index use kare, ye guaranteed nahi hai. Optimizer kabhi full table scan ko better samajh sakta hai.

## 16. Indexing in MongoDB

MongoDB mein bhi indexes searching ko fast karte hain.

### Default Index

MongoDB har collection mein `_id` field par default unique index create karta hai.

### Single-Field Index

```javascript
db.students.createIndex({ email: 1 });
```

`1` = ascending order.

`-1` = descending order.

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

### TTL Index

TTL index specified time ke baad eligible documents ko automatically expire/delete karne mein help karta hai.

```javascript
db.sessions.createIndex({ createdAt: 1 }, { expireAfterSeconds: 3600 });
```

### Text Index

Text search ke liye:

```javascript
db.articles.createIndex({ title: "text" });
```

### Check Indexes

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

### Drop Index

```javascript
db.students.dropIndex("email_1");
```

## 17. Indexing in MERN Stack

MERN stack mein MongoDB indexing important hai.

Example using Mongoose:

```javascript
const userSchema = new mongoose.Schema({
  name: String,
  email: {
    type: String,
    required: true,
    unique: true,
  },
  age: Number,
});

userSchema.index({ age: 1 });
```

Ya MongoDB collection par:

```javascript
db.users.createIndex({ email: 1 });
```

**Practical example:**

Agar application mein users ko email se frequently search karte hain, to email index useful ho sakta hai.

Lekin har field par index banana sahi nahi hai, kyunki writes aur storage par extra cost aati hai.

## 18. Common Mistakes

1. Har column par index create kar dena.
2. Sochna ki index har query ko fast karega.
3. Composite index mein column order ignore karna.
4. Index ko free performance improvement samajhna.
5. Clustered index ko har DBMS mein same tarah samajhna.
6. Hash index ko range queries ke liye use karna.
7. Index banane ke baad execution plan check na karna.
8. Primary key aur primary index ko universally identical samajhna.

## 19. Interview Questions and Answers

**Q1. What is indexing in DBMS?**

Indexing ek technique hai jo database records ko efficiently search aur retrieve karne mein help karti hai.

**Q2. Why is indexing used?**

SELECT, WHERE, JOIN aur suitable sorting queries ki performance improve karne ke liye.

**Q3. What is a clustered index?**

Aisa index jo table ki row storage organization ko index key ke according arrange karta hai. Exact implementation DBMS-specific hai.

**Q4. What is a non-clustered index?**

Table rows se separate index structure jo key aur row reference ki help se records locate karta hai.

**Q5. What is a composite index?**

Ek se zyada columns par banaya gaya index.

**Q6. What is a unique index?**

Aisa index jo indexed key values ki uniqueness enforce karta hai.

**Q7. What is a B+ Tree?**

Balanced tree structure jisme data entries generally leaf nodes mein hoti hain aur leaf nodes commonly linked hote hain.

**Q8. What is a hash index?**

Hash function based index jo equality lookups ke liye useful hota hai.

**Q9. Can indexes slow down a database?**

Haan. INSERT, UPDATE aur DELETE ke time indexes maintain karne padte hain.

**Q10. Does every query use an index?**

Nahi. Query optimizer cost aur available statistics ke according index ya table scan choose karta hai.

**Q11. What is a covering index?**

Aisa index jisme query ke required columns available hon, jisse table row access avoid ho sakta hai.

**Q12. Which index does MongoDB create by default?**

Har collection mein `_id` field par unique index.

## 20. Practical Tasks

1. Students table ke `email` column par index create karo.
2. `city` aur `age` par composite index banao.
3. Email par unique index create karo.
4. SQL `EXPLAIN` se query execution plan check karo.
5. MongoDB mein `createIndex()` use karo.
6. MongoDB mein `getIndexes()` se indexes dekho.
7. Ek query ko index ke saath aur bina index ke compare karo.

## 21. Quick Revision

| Term                | Meaning                                        |
| ------------------- | ---------------------------------------------- |
| Indexing            | Fast data retrieval technique                  |
| Clustered Index     | Row storage organization se connected index    |
| Non-Clustered Index | Separate index structure                       |
| Dense Index         | More detailed index entries                    |
| Sparse Index        | Selected index entries                         |
| B-Tree              | Balanced search tree                           |
| B+ Tree             | Leaf-oriented balanced tree                    |
| Hash Index          | Equality lookup ke liye useful                 |
| Composite Index     | Multiple columns ka index                      |
| Unique Index        | Duplicate key values prevent karta hai         |
| Covering Index      | Query ke required columns index mein available |
| Selectivity         | Values ki uniqueness/discrimination            |
| EXPLAIN             | Query execution plan inspect karna             |

**Remember:** Indexing reads ko fast kar sakti hai, lekin extra storage aur write-maintenance cost ke saath aati hai. Best index wahi hai jo actual query workload ko improve kare.

## 22. MCQ Practice – 10 Questions

**Q1. Indexing ka main purpose kya hai?**

A. Data delete karna  
B. Data retrieval fast karna  
C. Table rename karna  
D. Database close karna

**Q2. B+ Tree mein data entries generally kahan hoti hain?**

A. Sirf root mein  
B. Sirf internal nodes mein  
C. Leaf nodes mein  
D. Database log mein

**Q3. Hash index kis type ki query ke liye useful hai?**

A. Equality search  
B. Range search  
C. Sorting only  
D. Table deletion

**Q4. Composite index mein kya hota hai?**

A. Multiple tables  
B. Multiple columns  
C. Multiple databases  
D. Multiple users

**Q5. Unique index kya ensure karta hai?**

A. Duplicate indexed key values na hon  
B. Table empty ho  
C. Rows sorted alphabetically hon  
D. Database encrypted ho

**Q6. Index ka disadvantage kya hai?**

A. Extra storage  
B. Write operations par maintenance cost  
C. Dono A aur B  
D. Koi disadvantage nahi

**Q7. MongoDB mein default index kis field par hota hai?**

A. name  
B. email  
C. age  
D. _id

**Q8. Query execution plan dekhne ke liye kaunsa SQL command use hota hai?**

A. DELETE  
B. EXPLAIN  
C. INSERT  
D. GRANT

**Q9. Composite index `(city, age)` mein generally leftmost column kaunsa hai?**

A. age  
B. city  
C. Dono independent hain  
D. Koi nahi

**Q10. Kya database har query mein index use karta hai?**

A. Haan, always  
B. Nahi, optimizer decide karta hai  
C. Sirf INSERT mein  
D. Sirf DELETE mein

### Answer Key

1-B, 2-C, 3-A, 4-B, 5-A, 6-C, 7-D, 8-B, 9-B, 10-B

---

**Topic 17 Complete – Database Indexing.**
