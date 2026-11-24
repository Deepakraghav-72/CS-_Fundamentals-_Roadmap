# 15. DBMS Transactions and ACID Properties

## 1. Transaction kya hoti hai?

**Transaction** database operations ka ek group hota hai, jo ek logical unit ki tarah execute hota hai.

Transaction ya to successfully complete hoti hai ya failure par uske changes rollback kiye jaate hain (jab transaction properly configured aur supported ho).

### Example – Bank Transfer

Rahul ke account mein ₹5,000 hain aur Aman ke account mein ₹2,000.

Rahul ko Aman ko ₹1,000 transfer karne hain.

Do operations honge:

1. Rahul ke account se ₹1,000 deduct.
2. Aman ke account mein ₹1,000 add.

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```

Agar beech mein error aata hai, to transaction ko rollback kiya ja sakta hai:

```sql
ROLLBACK;
```

**Important:** Real banking transfer mein sufficient balance, valid accounts aur concurrent updates handle karne ke liye additional checks aur appropriate locking/isolation bhi required hain.

---

## 2. Transaction ki Need

Transactions ka use hota hai:

- Bank transfers.
- Online payments.
- E-commerce orders.
- Ticket booking.
- Inventory management.
- User registration with multiple database operations.
- Multiple related records ko safely update karna.

Without transactions, ek operation successful aur doosra failed ho sakta hai, jisse inconsistent data create ho sakta hai.

---

## 3. ACID Properties

ACID transaction ki four important properties hain.

| Property        | Meaning                            |
| --------------- | ---------------------------------- |
| A – Atomicity   | All operations or none             |
| C – Consistency | Valid database state maintain      |
| I – Isolation   | Concurrent transactions controlled |
| D – Durability  | Committed changes persistent       |

### A. Atomicity

Atomicity ka meaning hai: Transaction ke saare operations complete honge ya transaction ke changes undo honge.

Example:

- Rahul ke account se ₹1,000 deduct hua.
- Aman ke account mein ₹1,000 add nahi hua.

Atomic transaction failure par Rahul ka deduction bhi rollback hona chahiye.

**Remember:** All or Nothing.

### B. Consistency

Consistency ensure karti hai ki transaction database ko ek valid state se doosri valid state mein le jaye.

Example:

Bank transfer mein:

- Account balance allowed rules follow kare.
- Required constraints violate na hon.
- Total money transfer ke dauran logically preserve rahe.

Consistency database constraints aur application rules par depend karti hai.

### C. Isolation

Isolation ka meaning hai concurrent transactions ek doosre ke incomplete changes ko uncontrolled way mein affect na karein.

Example:

Do users same time par ek hi account ka balance update kar rahe hain. Database ko ensure karna hoga ki updates safely handle hon.

Isolation ke different levels hote hain, jaise:

- Read Uncommitted
- Read Committed
- Repeatable Read
- Serializable

### D. Durability

Durability ka meaning hai ki successful COMMIT ke baad changes failures ya restart ke baad bhi persistent rehne chahiye.

Example:

Aman ko ₹1,000 receive ho gaye aur transaction commit ho gayi. Server restart hone par bhi committed balance preserve rehna chahiye.

**Remember:** Committed data should persist.

---

## 4. ACID Real-Life Example

Online shopping mein order place karte time:

1. Order create hota hai.
2. Payment record update hota hai.
3. Inventory quantity reduce hoti hai.

Agar payment record create ho gaya lekin order save nahi hua, to inconsistency ho sakti hai.

Transaction aur appropriate application design related operations ko safely coordinate karte hain.

| ACID        | Shopping Example                          |
| ----------- | ----------------------------------------- |
| Atomicity   | Related operations fail hone par rollback |
| Consistency | Stock aur order rules valid               |
| Isolation   | Multiple users ki purchases safely handle |
| Durability  | Committed order persistent                |

---

## 5. Transaction States

Transaction execution ke common states:

```text
        ACTIVE
           |
           v
 PARTIALLY COMMITTED
           |
           v
       COMMITTED

ACTIVE / PARTIALLY COMMITTED
           |
           v
         FAILED
           |
           v
        ABORTED
```

### States

| State               | Meaning                                                |
| ------------------- | ------------------------------------------------------ |
| Active              | Transaction execute ho rahi hai                        |
| Partially Committed | Last statement execute ho gaya, commit process pending |
| Committed           | Transaction successfully commit ho gayi                |
| Failed              | Transaction continue nahi kar sakti                    |
| Aborted             | Transaction ke changes rollback ho gaye                |
| Terminated          | Transaction execution finish                           |

---

## 6. COMMIT Command

`COMMIT` current transaction ke changes permanently save karta hai.

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

COMMIT;
```

COMMIT ke baad transaction ke changes normally rollback nahi kiye ja sakte using the same transaction.

---

## 7. ROLLBACK Command

`ROLLBACK` current uncommitted transaction ke changes undo karta hai.

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

ROLLBACK;
```

Ab update ka effect undo ho jayega.

**Important:** Rollback behavior aur transaction boundaries DBMS aur configuration par depend kar sakti hain.

---

## 8. SAVEPOINT Command

SAVEPOINT transaction ke andar ek checkpoint create karta hai.

Isse poori transaction rollback karne ke bajaye selected point tak rollback kar sakte hain.

### Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

SAVEPOINT first_update;

UPDATE accounts
SET balance = balance + 500
WHERE account_id = 2;

ROLLBACK TO SAVEPOINT first_update;

COMMIT;
```

Yahan second update undo ho jayega, lekin first update commit ho jayega.

**Note:** Exact syntax aur SAVEPOINT behavior DBMS ke according vary kar sakta hai.

---

## 9. Transaction Commands Comparison

| Command                   | Work                                    |
| ------------------------- | --------------------------------------- |
| BEGIN / START TRANSACTION | Transaction start                       |
| COMMIT                    | Changes save                            |
| ROLLBACK                  | Uncommitted changes undo                |
| SAVEPOINT                 | Checkpoint create                       |
| ROLLBACK TO SAVEPOINT     | Selected checkpoint tak undo            |
| RELEASE SAVEPOINT         | Checkpoint remove (DBMS support varies) |

---

## 10. Concurrency kya hoti hai?

Jab multiple transactions same time par execute hoti hain, use concurrency kehte hain.

Example:

- Transaction T1 account balance read karti hai.
- Transaction T2 bhi same balance read karti hai.
- Dono balance update karne ki koshish karti hain.

Agar proper concurrency control na ho, to data inconsistency ho sakti hai.

### Common Concurrency Problems

**1. Dirty Read**

Ek transaction doosri transaction ka uncommitted data read kar leti hai.

Example:

- T1 balance 5,000 se 4,000 karti hai.
- T2 4,000 read kar leti hai.
- T1 rollback ho jati hai.

T2 ne aisa data read kiya jo commit hi nahi hua tha.

**2. Non-Repeatable Read**

Same transaction mein same row ko do baar read karne par different committed values milti hain.

Example:

- T1 balance 5,000 read karti hai.
- T2 balance 6,000 update karke commit karti hai.
- T1 dobara read karti hai aur 6,000 milta hai.

**3. Phantom Read**

Same query ko dobara execute karne par additional ya missing rows mil sakti hain, kyunki doosri transaction ne matching rows insert/delete ki hain.

**4. Lost Update**

Do transactions same data read karke update karti hain. Ek transaction ka update doosri transaction ke update ko overwrite kar sakta hai.

---

## 11. Isolation Levels

SQL databases commonly four standard isolation levels provide karte hain.

| Isolation Level  | Dirty Read | Non-Repeatable Read | Phantom Read                      |
| ---------------- | ---------- | ------------------- | --------------------------------- |
| Read Uncommitted | Possible   | Possible            | Possible                          |
| Read Committed   | Prevented  | Possible            | Possible                          |
| Repeatable Read  | Prevented  | Prevented           | Standard allows; DBMS may prevent |
| Serializable     | Prevented  | Prevented           | Prevented                         |

**Important:**

- Actual implementation DBMS ke according differ kar sakti hai.
- MVCC aur locking different databases mein behavior change kar sakte hain.
- Snapshot isolation ko standard isolation levels ke saath confuse nahi karna chahiye.

### Example Syntax

```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

Exact syntax DBMS-specific ho sakti hai.

---

## 12. Locking in Transactions

Locking ka use concurrent transactions ke data access ko control karne ke liye hota hai.

### A. Shared Lock (S Lock)

- Reading ke liye use hota hai.
- Multiple transactions shared locks le sakti hain.
- Conflicting exclusive lock ko block kar sakta hai.

### B. Exclusive Lock (X Lock)

- Writing/update ke liye use hota hai.
- Generally conflicting shared aur exclusive locks ko prevent karta hai.

### Comparison

| Shared Lock                    | Exclusive Lock                 |
| ------------------------------ | ------------------------------ |
| Read-oriented                  | Write-oriented                 |
| Compatible shared reads        | Conflicting access blocked     |
| Multiple shared locks possible | Conflicting locks allowed nahi |

---

## 13. Deadlock in Transactions

Deadlock tab hota hai jab two or more transactions ek doosre ke resources ka wait karti rehti hain.

Example:

- T1 ne Resource A lock kiya aur B ka wait kar rahi hai.
- T2 ne Resource B lock kiya aur A ka wait kar rahi hai.

```text
T1 holds A → waits for B
T2 holds B → waits for A
```

Dono transactions wait karti rahengi jab tak DBMS deadlock detect karke kisi transaction ko abort na kare ya koi timeout mechanism trigger na ho.

### Deadlock Prevention

- Locks consistent order mein acquire karna.
- Transactions short rakhna.
- Unnecessary locks avoid karna.
- DBMS deadlock detection aur timeout mechanisms use karna.

---

## 14. Autocommit

Autocommit mode mein har successful SQL statement automatically commit ho sakti hai.

Example:

```sql
UPDATE students
SET marks = 90
WHERE id = 1;
```

Agar autocommit enabled hai, to statement successful hone par changes automatically commit ho sakte hain.

Multiple statements ko ek transaction mein execute karne ke liye explicit transaction start karni pad sakti hai.

**Note:** Default autocommit behavior database driver aur DBMS par depend karta hai.

---

## 15. Transactions in MERN Stack

MERN mein MongoDB aur Mongoose transactions support karte hain.

MongoDB transactions multiple document operations ko atomic unit mein execute kar sakti hain, supported deployment configuration mein.

### Mongoose Transaction Example

```javascript
const session = await mongoose.startSession();

try {
  session.startTransaction();

  await Account.updateOne(
    { _id: senderId },
    { $inc: { balance: -1000 } },
    { session },
  );

  await Account.updateOne(
    { _id: receiverId },
    { $inc: { balance: 1000 } },
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

### Explanation

- `startSession()` – Session create karta hai.
- `startTransaction()` – Transaction start karta hai.
- `{ session }` – Operations ko same transaction se connect karta hai.
- `commitTransaction()` – Changes commit karta hai.
- `abortTransaction()` – Transaction abort karta hai.
- `endSession()` – Session close karta hai.

**Important:**

1. MongoDB multi-document transactions ke liye replica set ya sharded cluster configuration required hoti hai; standalone server par normal multi-document transactions available nahi hoti.
2. Transaction ke andar sufficient balance aur valid account checks bhi required hain.
3. Real payment systems mein retry handling, idempotency aur concurrency protection bhi zaroori hain.
4. Mongoose transaction API aur MongoDB driver version ke according implementation details vary kar sakti hain.

---

## 16. Common Mistakes

1. COMMIT aur ROLLBACK ka difference bhoolna.
2. SAVEPOINT ko separate transaction samajhna.
3. ACID properties ko sirf definitions ke form mein yaad karna, examples na samajhna.
4. Dirty Read aur Non-Repeatable Read ko same samajhna.
5. Isolation levels ko locking ke saath confuse karna.
6. Har SQL statement automatically rollback ho jayegi, aisa assume karna.
7. MongoDB standalone deployment par multi-document transaction assume karna.
8. Long-running transactions ko harmless samajhna.

---

## 17. Interview Questions and Answers

**Q1. What is a transaction?**

A transaction is a logical unit of database operations executed as one unit.

**Q2. What are ACID properties?**

Atomicity, Consistency, Isolation and Durability.

**Q3. What is Atomicity?**

All operations succeed together, or the transaction's changes are rolled back.

**Q4. What is Consistency?**

A transaction preserves database rules and constraints, moving the database between valid states.

**Q5. What is Isolation?**

Concurrent transactions are controlled so their execution does not create unacceptable interference.

**Q6. What is Durability?**

Committed changes persist even after a crash or restart, according to the database's durability guarantees.

**Q7. What is COMMIT?**

It saves the current transaction's changes.

**Q8. What is ROLLBACK?**

It undoes uncommitted changes in the current transaction.

**Q9. What is SAVEPOINT?**

It creates a checkpoint inside a transaction.

**Q10. What is a Dirty Read?**

Reading data written by another transaction before that transaction commits.

**Q11. What is a Deadlock?**

A situation where transactions wait indefinitely for resources held by each other, until the DBMS resolves it.

**Q12. Can MongoDB support ACID transactions?**

Yes. MongoDB supports atomic single-document operations and multi-document transactions in supported deployments.

---

## 18. Practical Tasks

1. Two accounts create karo aur SQL transaction se money transfer simulate karo.
2. COMMIT aur ROLLBACK practice karo.
3. SAVEPOINT create karke partial rollback karo.
4. Dirty Read aur Non-Repeatable Read examples samjho.
5. Four isolation levels compare karo.
6. Shared aur Exclusive locks ka concept samjho.
7. Mongoose mein transaction example implement karo.

---

## 19. Quick Revision

- Transaction = Logical unit of database operations.
- ACID = Atomicity, Consistency, Isolation, Durability.
- Atomicity = All or Nothing.
- Consistency = Valid database state.
- Isolation = Safe concurrent execution.
- Durability = Committed changes persist.
- COMMIT = Save changes.
- ROLLBACK = Undo uncommitted changes.
- SAVEPOINT = Checkpoint.
- Concurrency = Multiple transactions at the same time.
- Dirty Read = Uncommitted data read.
- Non-Repeatable Read = Same row ki values change.
- Phantom Read = Repeated query mein matching rows change.
- Lost Update = Ek update doosre ko overwrite kar de.
- Shared Lock = Read-oriented.
- Exclusive Lock = Write-oriented.
- Deadlock = Transactions ek doosre ka wait karti rahen.
- Autocommit = Statement automatically commit.

---

## 20. MCQ Practice – 10 Questions

**Q1. ACID ka A kya hai?**

A. Access  
B. Atomicity  
C. Accuracy  
D. Allocation

**Q2. COMMIT ka use kya hai?**

A. Changes save karna  
B. Database delete karna  
C. Table rename karna  
D. Query stop karna

**Q3. ROLLBACK kya karta hai?**

A. Changes undo karta hai  
B. Changes duplicate karta hai  
C. Index create karta hai  
D. Database restart karta hai

**Q4. Dirty Read mein kya hota hai?**

A. Uncommitted data read hota hai  
B. Database delete hota hai  
C. Table lock permanently ho jati hai  
D. Data encrypt hota hai

**Q5. SAVEPOINT ka purpose kya hai?**

A. Checkpoint create karna  
B. New database create karna  
C. User delete karna  
D. Index drop karna

**Q6. Durability kis cheez ko guarantee karti hai?**

A. Committed data persistence  
B. Query formatting  
C. Faster CPU  
D. Automatic indexing

**Q7. Lost Update kab hota hai?**

A. Ek update doosre update ko overwrite kar deta hai  
B. Table create hoti hai  
C. Database backup hota hai  
D. Query execute nahi hoti

**Q8. Shared Lock mainly kis operation ke liye hota hai?**

A. Read  
B. Delete only  
C. Database drop  
D. Server restart

**Q9. Deadlock mein kya hota hai?**

A. Transactions ek doosre ke resources ka wait karti hain  
B. All queries instantly complete hoti hain  
C. Database automatically delete hota hai  
D. All records duplicate hote hain

**Q10. MongoDB multi-document transactions ke liye generally kya required hai?**

A. Only standalone deployment  
B. Replica set ya sharded cluster  
C. Only browser  
D. Only HTML

### Answer Key

1-B, 2-A, 3-A, 4-A, 5-A, 6-A, 7-A, 8-A, 9-A, 10-B
