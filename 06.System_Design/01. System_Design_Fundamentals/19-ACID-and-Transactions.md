# Topic 19: ACID Properties & Transactions

## 1. Transaction Kya Hota Hai?

Database Transaction ek ya multiple database operations ka logical unit hota hai, jise ek complete operation ke roop mein execute kiya jata hai.

Simple words mein:

Transaction ka matlab hai database ke multiple operations ko ek single logical task ki tarah perform karna.

### Real-Life Example: Bank Transfer

Maan lo Rahul ke account mein ₹10,000 hain aur Aman ke account mein ₹5,000 hain.

Rahul ko Aman ke account mein ₹2,000 transfer karne hain.

Is process mein do operations honge:

1. Rahul ke account se ₹2,000 deduct karna.
2. Aman ke account mein ₹2,000 add karna.

Transaction ke baad:

| Account |  Before |  After |
| ------- | ------: | -----: |
| Rahul   | ₹10,000 | ₹8,000 |
| Aman    |  ₹5,000 | ₹7,000 |

Dono operations successfully complete hone chahiye.

Agar Rahul ke account se paise deduct ho gaye, lekin Aman ke account mein add nahi hue, to problem ho jayegi.

Database Transaction isi tarah ki problems ko handle karne mein help karta hai.

---

## 2. Transaction Ki Zaroorat Kyu Hoti Hai?

Maan lo kisi application mein ek operation ke liye multiple database queries execute hoti hain.

Agar beech mein koi query fail ho jaye, to database inconsistent state mein ja sakta hai.

Transaction ki help se hum:

- Multiple operations ko group kar sakte hain.
- Failure hone par changes rollback kar sakte hain.
- Data consistency maintain kar sakte hain.
- Concurrent operations ko control kar sakte hain.
- Successful changes ko permanently commit kar sakte hain.

---

## 3. ACID Properties Kya Hoti Hain?

ACID database transactions ki four important properties hain.

ACID ka full form:

- A – Atomicity
- C – Consistency
- I – Isolation
- D – Durability

In properties ka purpose reliable database transactions ensure karna hai.

---

## 4. Atomicity

Atomicity ka matlab hai:

**All or Nothing.**

Transaction ke saare operations successfully complete honge, ya failure ki situation mein transaction ke changes rollback honge.

### Example

Rahul ₹2,000 Aman ko transfer kar raha hai.

Do operations:

1. Rahul ke account se ₹2,000 deduct.
2. Aman ke account mein ₹2,000 add.

Suppose second operation fail ho gaya.

To transaction rollback hone par first operation ka change bhi undo ho jana chahiye.

### Diagram

```text
       Start Transaction
              |
              v
      Deduct ₹2000
              |
              v
       Add ₹2000
              |
         +----+----+
         |         |
       Success   Failure
         |         |
         v         v
       COMMIT    ROLLBACK
         |         |
         v         v
       Save      Undo
      Changes   Changes
```

### Atomicity Ka Benefit

- Partial updates prevent hote hain.
- Data corruption ka risk reduce hota hai.
- Multi-step operations reliable bante hain.

**Remember:** Atomicity = All or Nothing.

---

## 5. Consistency

Consistency ka matlab hai transaction database ko ek valid state se doosri valid state mein le jaye.

Database ke defined rules aur constraints violate nahi hone chahiye.

### Example

Maan lo bank mein:

Rahul = ₹10,000  
Aman = ₹5,000

Total balance = ₹15,000

Rahul ₹2,000 Aman ko transfer karta hai.

After transaction:

Rahul = ₹8,000  
Aman = ₹7,000

Total balance = ₹15,000

Total amount same hai.

### Consistency Ka Example: Constraints

Maan lo database mein age 18 ya usse zyada honi chahiye.

```sql
CREATE TABLE Users (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT CHECK (age >= 18)
);
```

Ab agar transaction age = 15 insert karne ki koshish karega, to database constraint violation ki wajah se reject kar sakta hai.

### Consistency Ka Benefit

- Database rules maintain hote hain.
- Invalid data prevent hota hai.
- Data integrity improve hoti hai.

**Remember:** Consistency = Valid State to Valid State.

---

## 6. Isolation

Isolation ka matlab hai concurrent transactions ko is tarah execute karna ki ek transaction ka incomplete data doosre transaction ke liye problematic na ho.

Simple words mein:

Multiple transactions ek saath execute ho sakti hain, lekin unka interaction database ke defined isolation level ke according controlled hona chahiye.

### Example

Maan lo Rahul ke account mein ₹5,000 hain.

Do transactions almost same time par execute hoti hain:

- Transaction A: ₹4,000 withdraw karna chahti hai.
- Transaction B: ₹3,000 withdraw karna chahti hai.

Agar dono transactions same ₹5,000 balance ko independently read karke withdrawal allow kar dein, to account mein incorrect balance ya overdraft situation ho sakti hai.

Database locking, concurrency control aur isolation levels ki help se aisi problems handle ki ja sakti hain.

### Isolation Ka Benefit

- Concurrent operations safely handle hoti hain.
- Dirty reads aur other concurrency anomalies control hoti hain.
- Data correctness maintain karne mein help milti hai.

**Remember:** Isolation = Concurrent Transactions Ko Safely Handle Karna.

---

## 7. Durability

Durability ka matlab hai:

Jab transaction successfully COMMIT ho jati hai, to uske changes system failure ke baad bhi recoverable rehne chahiye.

### Example

Rahul ne Aman ko ₹2,000 transfer kiye.

Database ne transaction successfully commit kar di.

Ab agar uske baad server restart ho jaye, to committed transaction ka result lose nahi hona chahiye.

### Durability Ka Benefit

- Committed data survive karta hai.
- System crash ke baad recovery possible hoti hai.
- Database reliability improve hoti hai.

Durability ke liye databases transaction logs, write-ahead logging aur storage recovery mechanisms use kar sakte hain.

**Remember:** Durability = Committed Changes Persist Karna.

---

## 8. ACID Properties – Complete Summary

| Property    | Meaning                            | Simple Example                                  |
| ----------- | ---------------------------------- | ----------------------------------------------- |
| Atomicity   | All or Nothing                     | Dono bank transfer operations complete hon      |
| Consistency | Valid state maintain               | Total balance aur constraints valid rahen       |
| Isolation   | Concurrent transactions controlled | Simultaneous withdrawals safely handle hon      |
| Durability  | Committed changes persist          | Restart ke baad committed transfer available ho |

### ACID Yaad Rakhne Ki Trick

- A = All or Nothing
- C = Correct / Consistent Data
- I = Independent Transactions
- D = Data Durable

---

## 9. COMMIT Kya Hota Hai?

COMMIT ek transaction ko successfully complete karke uske changes database mein save karne ka operation hai.

Example:

```sql
BEGIN;

UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 1;

UPDATE Accounts
SET balance = balance + 2000
WHERE account_id = 2;

COMMIT;
```

Yahan COMMIT transaction ke changes ko successfully complete karta hai.

**Note:** Ye SQL syntax transaction support karne wale relational DBMS ke liye example hai.

---

## 10. ROLLBACK Kya Hota Hai?

ROLLBACK ka use transaction ke uncommitted changes ko undo karne ke liye hota hai.

Example:

```sql
BEGIN;

UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 1;

UPDATE Accounts
SET balance = balance + 2000
WHERE account_id = 2;

ROLLBACK;
```

Yahan transaction commit nahi hui. ROLLBACK dono updates ke uncommitted changes undo kar dega.

### COMMIT vs ROLLBACK

| COMMIT                             | ROLLBACK                                         |
| ---------------------------------- | ------------------------------------------------ |
| Transaction changes save karta hai | Uncommitted changes undo karta hai               |
| Successful completion              | Failure ya cancellation par use ho sakta hai     |
| Changes persist karte hain         | Previous state restore karne mein help karta hai |

---

## 11. Transaction Ka Complete Flow

```text
          BEGIN
            |
            v
       Operation 1
            |
            v
       Operation 2
            |
            v
       Operation 3
            |
            v
      All Successful?
         /     \
       Yes      No
        |        |
        v        v
      COMMIT  ROLLBACK
        |        |
        v        v
     Changes  Undo Changes
      Saved
```

### Transaction States

Database transaction lifecycle mein commonly ye states describe ki jati hain:

1. Active – Transaction execute ho rahi hai.
2. Partially Committed – Last statement execute ho chuka hai, commit processing complete nahi hui.
3. Committed – Transaction successfully complete ho gayi.
4. Failed – Transaction aage execute nahi ho sakti.
5. Aborted – Transaction rollback ho gayi.
6. Terminated – Transaction ka lifecycle finish ho gaya.

---

## 12. ACID Transactions Ka SQL Example

Maan lo hum bank transfer implement kar rahe hain.

### Accounts Table

| account_id | name  | balance |
| ---------- | ----- | ------: |
| 1          | Rahul |   10000 |
| 2          | Aman  |    5000 |

### SQL Transaction

```sql
BEGIN;

UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 1;

UPDATE Accounts
SET balance = balance + 2000
WHERE account_id = 2;

COMMIT;
```

Agar kisi operation mein error aaye, to application ya database ke transaction handling mechanism ke through ROLLBACK karna chahiye.

### Better Example With Error Handling

```sql
BEGIN;

UPDATE Accounts
SET balance = balance - 2000
WHERE account_id = 1;

UPDATE Accounts
SET balance = balance + 2000
WHERE account_id = 2;

-- If everything succeeds:
COMMIT;

-- If an error occurs before commit:
-- ROLLBACK;
```

**Important:** Real banking application mein sufficient balance check, account validation, concurrency control aur transaction failure handling bhi required hain. Sirf do UPDATE statements enough nahi hain.

---

## 13. Transaction Isolation Levels

Isolation levels define karte hain ki concurrent transactions ek doosre ke changes ko kitna observe kar sakti hain.

Common SQL isolation levels:

1. Read Uncommitted
2. Read Committed
3. Repeatable Read
4. Serializable

### 13.1 Read Uncommitted

Ye lowest standard isolation level hai.

Transaction uncommitted changes bhi read kar sakti hai.

Isse Dirty Read ho sakta hai.

### 13.2 Read Committed

Transaction sirf committed data read karti hai.

Dirty Read prevent hota hai.

Lekin same transaction ke andar repeated query par different result mil sakta hai.

### 13.3 Repeatable Read

Same transaction ke andar same row ko dobara read karne par database ke isolation semantics ke according stable result milta hai.

Phantom reads ka behavior DBMS implementation aur isolation semantics par depend kar sakta hai.

### 13.4 Serializable

Ye strongest standard isolation level hai.

Concurrent transactions ka result aisa hona chahiye jaise transactions kisi serial order mein execute hui hon.

Concurrency kam ho sakti hai aur conflicts/retries badh sakte hain.

### Comparison Table

| Isolation Level  | Dirty Read | Non-Repeatable Read | Phantom Read                                              |
| ---------------- | ---------- | ------------------- | --------------------------------------------------------- |
| Read Uncommitted | Possible   | Possible            | Possible                                                  |
| Read Committed   | Prevented  | Possible            | Possible                                                  |
| Repeatable Read  | Prevented  | Prevented           | Standard level allows; DBMS may provide stronger behavior |
| Serializable     | Prevented  | Prevented           | Prevented                                                 |

**Important:** Real behavior database engine aur its implementation par depend karta hai. Ye table standard SQL isolation model ka simplified overview hai.

---

## 14. Concurrency Problems

Jab multiple transactions ek saath execute hoti hain, to kuch problems aa sakti hain.

### 14.1 Dirty Read

Jab ek transaction doosri transaction ke uncommitted changes read kar leti hai.

Example:

1. Transaction A balance update karti hai.
2. Transaction A ne abhi COMMIT nahi kiya.
3. Transaction B updated balance read kar leti hai.
4. Transaction A rollback kar deti hai.

Transaction B ne aisa data read kiya jo ultimately committed hi nahi hua.

### 14.2 Non-Repeatable Read

Jab same transaction ke andar same row ko do baar read karne par different values milti hain.

Example:

1. Transaction A balance = ₹5,000 read karti hai.
2. Transaction B balance = ₹7,000 update karke commit karti hai.
3. Transaction A dobara balance read karti hai.
4. Ab balance = ₹7,000 milta hai.

### 14.3 Phantom Read

Jab same transaction mein same condition se query repeat karne par matching rows ka set change ho jata hai.

Example:

1. Transaction A query karti hai: age > 18.
2. Transaction B ek new user insert karti hai jiska age 25 hai aur commit karti hai.
3. Transaction A same query dobara karti hai.
4. Ab extra matching row mil sakti hai.

### 14.4 Lost Update

Jab do transactions ek hi data ko update karti hain aur ek transaction ka change doosri transaction ke change se overwrite ho jata hai.

Example:

Initial balance = ₹5,000.

- Transaction A balance read karti hai: ₹5,000.
- Transaction B bhi balance read karti hai: ₹5,000.
- A ₹1,000 add karke ₹6,000 write karti hai.
- B ₹500 add karke ₹5,500 write karti hai.

Expected balance ₹6,500 tha, lekin final balance ₹5,500 ho gaya.

Ye lost update problem hai.

---

## 15. Locking Kya Hota Hai?

Locking ek concurrency control technique hai jo simultaneous transactions ke access ko control karti hai.

### Shared Lock

Shared Lock ka use reading ke liye hota hai.

Multiple transactions shared locks ke through same data read kar sakti hain, subject to DBMS rules.

### Exclusive Lock

Exclusive Lock ka use writing ke liye hota hai.

Jab ek transaction exclusive lock hold karti hai, to conflicting reads/writes ko block ya otherwise control kiya ja sakta hai.

### Comparison

| Shared Lock                 | Exclusive Lock                      |
| --------------------------- | ----------------------------------- |
| Reading ke liye             | Writing ke liye                     |
| Multiple compatible readers | Conflicting access restricted       |
| Data modify nahi karta      | Data modification protect karta hai |

Actual locking behavior database engine par depend karta hai.

---

## 16. Deadlock Kya Hota Hai?

Deadlock tab hota hai jab do ya zyada transactions ek doosre ke locks/resources ka wait karte hue stuck ho jati hain.

### Example

- Transaction A ne Resource 1 lock kiya.
- Transaction B ne Resource 2 lock kiya.
- A ko Resource 2 chahiye.
- B ko Resource 1 chahiye.

Dono ek doosre ka wait karengi.

```text
Transaction A
     |
     v
Waiting for Resource 2
     |
     v
Resource 2 locked by B

Transaction B
     |
     v
Waiting for Resource 1
     |
     v
Resource 1 locked by A
```

### Deadlock Handle Kaise Karte Hain?

- Database deadlock detect kar sakta hai.
- Ek transaction abort ki ja sakti hai.
- Application safe retry kar sakti hai.
- Transactions ko short rakha ja sakta hai.
- Resources ko consistent order mein lock kiya ja sakta hai.

---

## 17. ACID vs BASE

Distributed systems aur NoSQL discussions mein BASE ek important concept hai.

BASE ka full form:

- Basically Available
- Soft State
- Eventual Consistency

### ACID

ACID transactional reliability aur database correctness par focus karta hai.

### BASE

BASE distributed systems mein availability aur eventual consistency jaise design approaches ko describe karta hai.

### Comparison

| ACID                                   | BASE                                                        |
| -------------------------------------- | ----------------------------------------------------------- |
| Transaction guarantees par focus       | Distributed availability aur eventual consistency par focus |
| Strong transactional behavior common   | Temporary inconsistency acceptable ho sakti hai             |
| Banking-style transactions mein useful | Some large distributed workloads mein useful                |

**Important:** ACID aur BASE ko simple SQL vs NoSQL rule mat samajhna. NoSQL databases bhi ACID transactions support kar sakte hain. Ye different design properties aur trade-offs ko describe karte hain.

---

## 18. ACID in MongoDB

MongoDB ek NoSQL document database hai.

MongoDB mein:

- Single-document writes atomic hoti hain.
- Multi-document transactions supported hain.
- Replica sets aur sharded clusters par transaction support available hai.

Example:

```javascript
const session = await mongoose.startSession();

try {
  session.startTransaction();

  await Account.updateOne(
    { _id: senderId },
    { $inc: { balance: -2000 } },
    { session },
  );

  await Account.updateOne(
    { _id: receiverId },
    { $inc: { balance: 2000 } },
    { session },
  );

  await session.commitTransaction();
} catch (error) {
  await session.abortTransaction();
  throw error;
} finally {
  await session.endSession();
}
```

### Code Explanation

1. Session start hota hai.
2. Transaction start hoti hai.
3. Sender ke account se amount deduct hota hai.
4. Receiver ke account mein amount add hota hai.
5. Sab successful hone par commit hota hai.
6. Error aane par abort hota hai.
7. Finally session end hota hai.

**Important:** Ye illustrative Mongoose example hai. Production money-transfer implementation mein sufficient balance checks, transaction retry handling, idempotency, currency handling aur concurrent updates ki protection bhi implement karni hogi.

---

## 19. ACID vs Distributed Transactions in Microservices

Monolithic application mein agar multiple operations ek hi relational database mein hain, to ek database transaction unhe cover kar sakti hai.

Microservices mein situation different ho sakti hai.

Example:

```text
Order Service
     |
     v
Order Database

Payment Service
     |
     v
Payment Database

Inventory Service
     |
     v
Inventory Database
```

Yahan teen different services aur databases hain.

Ek normal local database transaction automatically teeno databases ko cover nahi karti.

Is problem ko distributed transaction problem kaha jata hai.

### Common Approaches

1. Saga Pattern
2. Two-Phase Commit (2PC), where supported and appropriate
3. Event-driven coordination
4. Compensating transactions

### Saga Example

```text
Create Order
     |
     v
Reserve Inventory
     |
     v
Process Payment
     |
     +------ Success
     |          |
     |          v
     |       Confirm Order
     |
     +------ Failure
                |
                v
        Release Inventory
                |
                v
          Cancel Order
```

Saga Pattern ko hum HLD mein detail mein padhenge.

---

## 20. ACID Properties Kahan Important Hain?

ACID properties especially important hoti hain jahan data correctness aur transactions critical hote hain.

Examples:

1. Banking Applications
2. Payment Systems
3. E-commerce Orders
4. Inventory Management
5. Ticket Booking
6. Financial Applications
7. Account Management

Example:

Agar railway ticket booking mein same seat do users ko assign ho jaye, to serious problem ho sakti hai.

Database transactions aur concurrency control is type ki problems ko prevent karne mein help karte hain.

---

## 21. Common Interview Questions

### Q1. What is a Database Transaction?

Database operations ka logical unit jo ek complete task ke roop mein execute hota hai.

### Q2. What is ACID?

ACID ka full form Atomicity, Consistency, Isolation aur Durability hai.

### Q3. What is Atomicity?

Transaction ke operations all-or-nothing principle follow karte hain.

### Q4. What is Consistency?

Transaction database ko ek valid state se doosri valid state mein le jati hai.

### Q5. What is Isolation?

Concurrent transactions ko defined isolation rules ke according control karna.

### Q6. What is Durability?

Committed changes system failure ke baad bhi recoverable rehne chahiye.

### Q7. What is COMMIT?

Transaction ke changes successfully commit karna.

### Q8. What is ROLLBACK?

Uncommitted transaction changes undo karna.

### Q9. What is Dirty Read?

Doosri transaction ke uncommitted changes ko read karna.

### Q10. What is Deadlock?

Jab transactions ek doosre ke locked resources ka wait karte hue stuck ho jati hain.

### Q11. What is Isolation Level?

Isolation level define karta hai ki concurrent transactions ek doosre ke changes ko kaise observe kar sakti hain.

### Q12. Do NoSQL databases support ACID?

Kuch NoSQL databases ACID transactions support karte hain. MongoDB iska example hai.

---

## 22. Practical Tasks

1. ACID ka full form yaad karo.
2. Bank transfer ka transaction flow draw karo.
3. COMMIT aur ROLLBACK ki SQL queries likho.
4. Dirty Read aur Lost Update ke examples banao.
5. Four standard isolation levels revise karo.
6. Shared Lock aur Exclusive Lock ka difference likho.
7. Deadlock ka diagram banao.
8. MongoDB transaction example ko samjho.

---

## 23. Quick Revision

| Concept             | Meaning                                        |
| ------------------- | ---------------------------------------------- |
| Transaction         | Logical unit of database operations            |
| ACID                | Atomicity, Consistency, Isolation, Durability  |
| Atomicity           | All or Nothing                                 |
| Consistency         | Valid database state maintain                  |
| Isolation           | Concurrent transaction control                 |
| Durability          | Committed changes persist                      |
| COMMIT              | Changes save                                   |
| ROLLBACK            | Uncommitted changes undo                       |
| Dirty Read          | Uncommitted data read                          |
| Non-Repeatable Read | Same row ki repeated read par different value  |
| Phantom Read        | Repeated query par matching rows ka set change |
| Lost Update         | Ek update doosre update se overwrite           |
| Locking             | Concurrent access control                      |
| Deadlock            | Transactions ek doosre ka wait karti rahen     |
| ACID                | Transaction reliability                        |
| BASE                | Distributed system design approach             |

---

## 24. Final Checklist

- [ ] Transaction kya hai samajh sakte ho.
- [ ] ACID ka full form bata sakte ho.
- [ ] Atomicity explain kar sakte ho.
- [ ] Consistency explain kar sakte ho.
- [ ] Isolation explain kar sakte ho.
- [ ] Durability explain kar sakte ho.
- [ ] COMMIT aur ROLLBACK differentiate kar sakte ho.
- [ ] Isolation levels samajh sakte ho.
- [ ] Dirty Read aur Lost Update explain kar sakte ho.
- [ ] Locking aur Deadlock samajh sakte ho.
- [ ] ACID aur BASE ka difference bata sakte ho.
- [ ] MongoDB transactions ka basic flow samajh sakte ho.
- [ ] Distributed transactions ka basic concept samajh sakte ho.

**Topic 19 Complete – ACID Properties & Transactions**
