# 16. DBMS Concurrency Control and Locking

## 1. Concurrency Control kya hota hai?

Jab multiple transactions database par simultaneously operations perform karti hain, to unke execution ko safely manage karne ki technique ko **Concurrency Control** kehte hain.

Iska main purpose:

- Data consistency maintain karna.
- Lost updates prevent karna.
- Dirty reads jaise problems control karna.
- Transactions ko safely execute karna.
- Database integrity maintain karna.

### Example

Suppose account balance ₹5,000 hai.

- Transaction T1 ₹1,000 withdraw karna chahti hai.
- Transaction T2 ₹500 withdraw karna chahti hai.

Dono transactions same time par old balance read karke update kar dein, to ek update lost ho sakta hai.

Concurrency control is problem ko prevent karne mein help karta hai.

---

## 2. Concurrency Problems

### A. Lost Update

Jab ek transaction ka update doosri transaction ke update se overwrite ho jata hai.

Example:

```text
Initial Balance = 5000

T1 reads 5000
T2 reads 5000

T1 subtracts 1000 → 4000
T2 subtracts 500  → 4500

T1 writes 4000
T2 writes 4500
```

Expected balance = 3500

Actual balance = 4500

T1 ka update lost ho gaya.

### B. Dirty Read

Ek transaction doosri transaction ka uncommitted data read kar leti hai.

```text
T1 updates balance = 4000
T2 reads balance = 4000
T1 rolls back
```

T2 ne uncommitted value read ki.

### C. Non-Repeatable Read

Same transaction mein same row ko dobara read karne par different value milti hai.

### D. Phantom Read

Same query ko dobara execute karne par matching rows ka set change ho jata hai.

### E. Incorrect Summary

Ek transaction aggregate calculation kar rahi hoti hai, jaise total balance, jab doosri transaction multiple rows update kar rahi hoti hai. Calculation inconsistent combination of values read kar sakti hai.

---

## 3. Locking kya hoti hai?

**Locking** ek concurrency control technique hai jisme database kisi data item par access ko control karta hai.

Transaction operation ke according lock acquire karti hai.

Main lock types:

1. Shared Lock (S Lock)
2. Exclusive Lock (X Lock)

---

## 4. Shared Lock (S Lock)

Shared lock mainly reading ke liye use hota hai.

- Multiple transactions same data par shared lock le sakti hain.
- Shared lock ke saath reading possible hoti hai.
- Conflicting exclusive lock generally allowed nahi hota.

Example:

```text
T1 → S Lock on Account A
T2 → S Lock on Account A

Both can read Account A.
```

### SQL Example

Kuch databases mein:

```sql
BEGIN;

SELECT *
FROM accounts
WHERE account_id = 1
FOR SHARE;

COMMIT;
```

Exact syntax aur supported lock modes DBMS ke according vary karte hain.

---

## 5. Exclusive Lock (X Lock)

Exclusive lock writing ya updating ke liye use hota hai.

- Ek data item par conflicting exclusive lock allow nahi hota.
- Other transactions ke conflicting reads/writes block ho sakte hain.
- Lock release hone ke baad waiting transaction proceed kar sakti hai.

Example:

```text
T1 → X Lock on Account A
T2 → Requests S Lock on Account A

T2 waits until conflicting lock is released.
```

### SQL Example

```sql
BEGIN;

SELECT *
FROM accounts
WHERE account_id = 1
FOR UPDATE;

UPDATE accounts
SET balance = balance - 500
WHERE account_id = 1;

COMMIT;
```

`FOR UPDATE` commonly selected rows ko update ke liye lock karne mein use hota hai. Exact behavior DBMS-specific hai.

---

## 6. Lock Compatibility Matrix

| Existing Lock | Requested S    | Requested X    |
| ------------- | -------------- | -------------- |
| S             | Compatible     | Not compatible |
| X             | Not compatible | Not compatible |

Simple meaning:

- S + S = Allowed
- S + X = Conflict
- X + S = Conflict
- X + X = Conflict

---

## 7. Two-Phase Locking (2PL)

**2PL** ek locking protocol hai jo serializability ensure karne ke liye use hota hai.

Isme transaction ke two phases hote hain:

### Phase 1: Growing Phase

- Transaction locks acquire kar sakti hai.
- Existing locks release nahi kar sakti.

### Phase 2: Shrinking Phase

- Transaction locks release kar sakti hai.
- New locks acquire nahi kar sakti.

```text
GROWING PHASE
Acquire Lock
Acquire Lock
Acquire Lock
      |
      v
SHRINKING PHASE
Release Lock
Release Lock
Release Lock
```

**Important:** 2PL mein transaction ka lock release karna start ho gaya, to woh naye locks acquire nahi kar sakti.

---

## 8. Strict Two-Phase Locking (Strict 2PL)

Strict 2PL, 2PL ka stricter form hai.

Isme transaction apne exclusive (write) locks commit ya abort hone tak hold karti hai.

Benefits:

- Dirty writes prevent hote hain.
- Cascading rollback avoid hota hai.
- Recoverability easier hoti hai.
- Serializability maintain hoti hai.

### Basic Difference

| 2PL                                              | Strict 2PL                            |
| ------------------------------------------------ | ------------------------------------- |
| Growing aur shrinking phases                     | Same two phases                       |
| Locks shrinking phase mein release ho sakte hain | Exclusive locks commit/abort tak held |
| Cascading rollback possible                      | Cascading rollback prevent hota hai   |

**Note:** Rigorous 2PL mein shared aur exclusive dono locks transaction ke end tak hold kiye jaate hain.

---

## 9. Deadlock

Deadlock tab hota hai jab two or more transactions ek doosre ke locked resources ka wait karti rehti hain.

### Example

```text
T1 locks A
T2 locks B

T1 waits for B
T2 waits for A
```

```text
T1 ─── waits for B ───> T2
 ^                       |
 |                       |
 └──── waits for A ──────┘
```

Dono transactions proceed nahi kar pati jab tak DBMS deadlock resolve na kare.

### Deadlock ke Four Necessary Conditions

1. **Mutual Exclusion:** Resource ek time par limited transaction ko milta hai.
2. **Hold and Wait:** Transaction resource hold karke doosre resource ka wait karti hai.
3. **No Preemption:** Resource forcibly remove nahi kiya ja sakta.
4. **Circular Wait:** Transactions circular chain mein ek doosre ka wait karti hain.

### Deadlock Handling

| Method     | Meaning                                    |
| ---------- | ------------------------------------------ |
| Prevention | Necessary conditions break karna           |
| Avoidance  | Unsafe allocation avoid karna              |
| Detection  | Deadlock identify karna                    |
| Recovery   | Victim transaction abort/rollback karna    |
| Timeout    | Long wait ke baad transaction cancel karna |

### Deadlock Prevention Tips

- Locks consistent order mein acquire karo.
- Transactions short rakho.
- Unnecessary locks avoid karo.
- Proper indexes use karo.
- Database ke deadlock detection mechanism ko use karo.

---

## 10. Starvation

Starvation tab hoti hai jab kisi transaction ko repeatedly resource ya lock nahi milta aur woh bahut long time tak wait karti rehti hai.

Example:

High-priority transactions repeatedly execute ho rahi hain aur low-priority transaction ko chance nahi mil raha.

### Deadlock vs Starvation

| Deadlock                                      | Starvation                                    |
| --------------------------------------------- | --------------------------------------------- |
| Transactions circular wait mein ho sakti hain | Transaction ko repeatedly resource nahi milta |
| Multiple transactions involved ho sakti hain  | Ek transaction bhi starve ho sakti hai        |
| Deadlock detection se resolve ho sakta hai    | Fair scheduling se reduce ho sakti hai        |

---

## 11. Timestamp-Based Concurrency Control

Timestamp ordering ek concurrency control technique hai.

Har transaction ko ek unique logical timestamp assign hota hai.

Example:

```text
T1 = Timestamp 10
T2 = Timestamp 20
T3 = Timestamp 30
```

Older transaction ka timestamp smaller hota hai.

Database read/write operations ko timestamp ordering rules ke according allow ya reject karta hai.

### Basic Idea

- Older transaction ko earlier order diya jata hai.
- Conflicting operation agar timestamp order violate kare, transaction abort/restart ho sakti hai.
- Is approach mein traditional locking ki requirement nahi hoti.

### Advantages

- Deadlock nahi hota due to waiting for locks, because basic timestamp ordering doesn't use lock waits.
- Serializability enforce kar sakta hai.

### Disadvantages

- Transactions repeatedly abort ho sakti hain.
- High contention mein performance issue ho sakta hai.

---

## 12. MVCC (Multi-Version Concurrency Control)

MVCC ka full form **Multi-Version Concurrency Control** hai.

Is technique mein database data ke multiple versions maintain karta hai.

Reader aur writer ko manage karne ke liye versions ka use hota hai.

### Example

Suppose account balance:

```text
Old Version = 5000
New Version = 4500
```

Ek read transaction apne snapshot ke according old version read kar sakti hai, jabki writer new version create kar raha ho.

### Benefits

- Readers aur writers ke beech blocking reduce ho sakti hai.
- Consistent snapshots mil sakte hain.
- Read-heavy workloads mein useful ho sakta hai.

### Limitations

- Multiple versions storage consume karti hain.
- Old versions ki cleanup required hoti hai.
- Write conflicts phir bhi possible hain.

**Examples:** PostgreSQL aur MySQL InnoDB MVCC techniques use karte hain. Implementation details different hain.

---

## 13. Pessimistic vs Optimistic Concurrency Control

### Pessimistic Concurrency Control

Assume karta hai ki conflict ho sakta hai, isliye operations se pehle locks use karta hai.

Example: Row lock lekar update karna.

### Optimistic Concurrency Control

Assume karta hai ki conflicts relatively uncommon hain.

- Read phase
- Validation phase
- Write phase

Agar conflict detect hota hai, transaction retry ya abort ho sakti hai.

### Comparison

| Pessimistic                                      | Optimistic                                      |
| ------------------------------------------------ | ----------------------------------------------- |
| Locks commonly use                               | Validation commonly use                         |
| High-conflict workloads mein useful ho sakta hai | Low-conflict workloads mein useful ho sakta hai |
| Waiting/blocking possible                        | Retry/abort possible                            |
| Lock management overhead                         | Validation overhead                             |

---

## 14. Serializability

Serializability ka meaning hai concurrent transactions ka result kisi valid serial execution ke equivalent hona.

### Serial Schedule

Ek transaction complete hone ke baad doosri execute hoti hai.

```text
T1 → T1 → T1 → T2 → T2 → T2
```

### Concurrent Schedule

Operations interleave hoti hain.

```text
T1 → T2 → T1 → T2 → T1 → T2
```

Agar concurrent schedule ka result kisi serial schedule ke equivalent hai, to woh serializable hai.

### Conflict Serializability

Do operations conflict karti hain jab:

1. Different transactions ki hon.
2. Same data item access karti hon.
3. At least ek operation write ho.

Conflicting pairs:

- Read–Write
- Write–Read
- Write–Write

Read–Read conflict nahi karta.

### Precedence Graph

Conflict serializability check karne ke liye precedence graph use hota hai.

Rules:

- Har transaction ek node hoti hai.
- Conflicting operation order ke according directed edge banti hai.
- Agar graph acyclic hai, schedule conflict-serializable hai.
- Agar graph mein cycle hai, schedule conflict-serializable nahi hai.

---

## 15. Recoverability Concepts

### Recoverable Schedule

Agar T2, T1 ke written data ko read karti hai, to T2 ka commit T1 ke commit ke baad hona chahiye.

### Cascading Rollback

Ek transaction rollback hone par us par dependent multiple transactions ko bhi rollback karna pade.

### Cascadeless Schedule

Transactions sirf committed data read karti hain.

### Strict Schedule

Kisi transaction ke data item ko write karne ke baad, jab tak writer commit/abort na ho, doosri transaction us item ko read ya write nahi kar sakti.

### Comparison

| Schedule    | Meaning                                          |
| ----------- | ------------------------------------------------ |
| Recoverable | Reader commits after writer commits              |
| Cascadeless | Only committed data is read                      |
| Strict      | Uncommitted writes cannot be read or overwritten |

Relationship:

```text
Strict ⇒ Cascadeless ⇒ Recoverable
```

---

## 16. Concurrency Control in MERN / MongoDB

MongoDB concurrent operations handle karne ke liye atomicity, document-level concurrency control, transactions aur other mechanisms provide karta hai.

### Atomic Update Example

```javascript
await Account.updateOne(
  {
    _id: accountId,
    balance: { $gte: 500 },
  },
  {
    $inc: { balance: -500 },
  },
);
```

Yahan balance condition aur update same atomic document operation mein execute hote hain.

Application ko result check karna chahiye ki document actually update hua ya nahi.

### Optimistic Concurrency in Mongoose

Mongoose version key (`__v`) aur optimistic concurrency configuration ka use karke conflicting updates detect kar sakta hai.

Concept:

1. Document read karo.
2. Version check karo.
3. Update attempt karo.
4. Version conflict ho to retry ya error handle karo.

### Important

- MongoDB single-document writes atomic hote hain.
- Multiple documents ke operations ke liye transaction use ki ja sakti hai.
- MongoDB multi-document transactions supported replica set ya sharded cluster par available hoti hain.
- Application-level business rules aur retry handling bhi important hain.

---

## 17. Common Mistakes

1. Shared aur Exclusive locks ko same samajhna.
2. 2PL ke growing aur shrinking phases confuse karna.
3. Strict 2PL ko Rigorous 2PL samajhna.
4. Deadlock aur starvation ko same samajhna.
5. MVCC ko locking ka exact opposite samajhna.
6. Read–Read operations ko conflicting samajhna.
7. Precedence graph mein cycle ka meaning bhoolna.
8. Timestamp ordering ko traditional locking protocol samajhna.
9. Assume karna ki concurrency control sirf SQL databases mein hota hai.

---

## 18. Interview Questions and Answers

**Q1. What is concurrency control?**

It manages simultaneous transactions while maintaining database consistency and isolation.

**Q2. What is a Shared Lock?**

A read-oriented lock that allows compatible shared reads.

**Q3. What is an Exclusive Lock?**

A lock used for writing that conflicts with other shared and exclusive locks on the same item.

**Q4. What is 2PL?**

Two-Phase Locking is a protocol with growing and shrinking phases.

**Q5. What is Strict 2PL?**

A 2PL variant that holds exclusive locks until commit or abort.

**Q6. What is a deadlock?**

Transactions wait for resources held by each other, creating a cycle of waiting.

**Q7. What is starvation?**

A transaction waits indefinitely or excessively because it repeatedly fails to get the required resource.

**Q8. What is MVCC?**

A concurrency technique that maintains multiple versions of data.

**Q9. What is serializability?**

A property where a concurrent schedule produces a result equivalent to a valid serial schedule.

**Q10. What is conflict serializability?**

A schedule is conflict-serializable if it can be transformed into a serial schedule by swapping non-conflicting operations.

**Q11. What is a precedence graph?**

A directed graph used to check conflict serializability.

**Q12. What is the difference between optimistic and pessimistic concurrency control?**

Pessimistic control commonly locks resources early; optimistic control validates for conflicts before accepting writes.

---

## 19. Practical Tasks

1. Shared aur Exclusive Lock ka example samjho.
2. 2PL ke growing aur shrinking phases ka schedule banao.
3. Deadlock ka wait-for graph draw karo.
4. Deadlock aur starvation ke examples compare karo.
5. MVCC ka version-based example banao.
6. Given schedule ka precedence graph banao.
7. Check karo ki graph cyclic hai ya acyclic.
8. MongoDB mein conditional atomic update implement karo.

---

## 20. Quick Revision

- Concurrency Control = Safe simultaneous execution.
- Shared Lock = Read lock.
- Exclusive Lock = Write lock.
- 2PL = Growing + Shrinking.
- Strict 2PL = Exclusive locks held till transaction end.
- Deadlock = Circular waiting.
- Starvation = Repeatedly resource na milna.
- Timestamp Ordering = Logical timestamps ke basis par execution.
- MVCC = Multiple data versions.
- Pessimistic = Locks first.
- Optimistic = Validate conflicts.
- Serializability = Equivalent to a serial execution.
- Precedence Graph = Conflict serializability check.
- Acyclic graph = Conflict-serializable.
- Strict Schedule = Uncommitted writes cannot be read or overwritten.

---

## 21. MCQ Practice – 10 Questions

**Q1. Concurrency Control ka purpose kya hai?**

A. Data consistency maintain karna  
B. Database delete karna  
C. CPU manufacture karna  
D. HTML render karna

**Q2. Shared Lock kis operation ke liye hota hai?**

A. Read  
B. Write only  
C. Drop  
D. Delete database

**Q3. 2PL mein kitne phases hote hain?**

A. One  
B. Two  
C. Three  
D. Four

**Q4. Strict 2PL mein exclusive locks kab release hote hain?**

A. Transaction commit/abort hone par  
B. Immediately after acquisition  
C. Database startup par  
D. Query likhte hi

**Q5. Deadlock mein kya hota hai?**

A. Circular waiting  
B. Automatic backup  
C. Data compression  
D. Index creation

**Q6. MVCC ka full form kya hai?**

A. Multiple Value Control Command  
B. Multi-Version Concurrency Control  
C. Main Virtual Computer Control  
D. Multi Variable Cache Control

**Q7. Conflict serializability check karne ke liye kya use hota hai?**

A. Precedence Graph  
B. HTML  
C. CSS  
D. DNS

**Q8. Acyclic precedence graph kya indicate karta hai?**

A. Conflict-serializable schedule  
B. Deadlock always  
C. Database corruption  
D. SQL error

**Q9. Read–Read operations same data item par kya hain?**

A. Conflict  
B. Non-conflicting  
C. Always deadlock  
D. Always rollback

**Q10. Optimistic concurrency control mein conflict kab check hota hai?**

A. Validation phase  
B. HTML phase  
C. Database installation  
D. Server shutdown

### Answer Key

1-A, 2-A, 3-B, 4-A, 5-A, 6-B, 7-A, 8-A, 9-B, 10-A
