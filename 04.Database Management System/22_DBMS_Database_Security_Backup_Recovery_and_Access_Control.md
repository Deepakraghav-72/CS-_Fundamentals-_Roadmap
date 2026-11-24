# 22. Database Security, Backup, Recovery and Access Control

## 1. Database Security kya hai?

Database Security ka matlab database ko unauthorized access, data theft, modification, deletion aur attacks se protect karna hai.

**Main goals – CIA Triad**

| Goal            | Meaning                                 |
| --------------- | --------------------------------------- |
| Confidentiality | Data sirf authorized users dekh sakein  |
| Integrity       | Data accurate aur correct rahe          |
| Availability    | Zarurat padne par database available ho |

Example: Banking application mein customer ka balance private bhi hona chahiye, correct bhi aur accessible bhi.

## 2. Authentication vs Authorization

| Authentication                    | Authorization                       |
| --------------------------------- | ----------------------------------- |
| User ki identity verify karta hai | User ki permissions check karta hai |
| Who are you?                      | What can you do?                    |
| Login, password, OTP              | Read, Insert, Update, Delete        |

Example:

- Login karke identity verify karna = Authentication.
- Login ke baad sirf apna profile edit kar pana = Authorization.

## 3. Database Users and Roles

Database mein har user ko required permissions hi deni chahiye.

**RBAC (Role-Based Access Control):** Permissions users ke bajaye roles ko assign hoti hain.

Example:

| Role      | Permission                     |
| --------- | ------------------------------ |
| Admin     | Full database access           |
| Developer | Required tables par read/write |
| Analyst   | Mostly read-only               |
| Guest     | Limited access                 |

**Principle of Least Privilege:** User ko sirf utni permissions do jitni uske kaam ke liye zaroori hain.

## 4. GRANT and REVOKE

SQL mein permissions dene aur wapas lene ke liye use hote hain.

```sql
-- User ko SELECT permission dena
GRANT SELECT ON employees TO user1;

-- Permission wapas lena
REVOKE SELECT ON employees FROM user1;
```

Note: Exact syntax aur supported privileges DBMS ke according vary kar sakte hain.

## 5. Password Security

Passwords ko database mein plain text form mein store nahi karna chahiye.

**Password Hashing:** Password ko one-way hash function se convert karke store karte hain.

Recommended password hashing algorithms:

- Argon2id
- bcrypt
- scrypt
- PBKDF2

**Salt:** Har password ke saath unique random value add ki jaati hai, jisse same passwords ke hashes bhi different ho sakte hain.

### Hashing vs Encryption

| Hashing                               | Encryption                            |
| ------------------------------------- | ------------------------------------- |
| Generally one-way                     | Reversible with key                   |
| Original value recover nahi kar sakte | Correct key se decrypt kar sakte hain |
| Password storage                      | Sensitive data protection             |

Important: Normal fast hashes jaise SHA-256 ko directly password storage ke liye use nahi karna chahiye.

## 6. Database Encryption

Encryption ka purpose data ko unreadable format mein protect karna hai.

**A. Encryption at Rest**

Stored data ko protect karta hai.

Example: Database files aur backups ki encryption.

**B. Encryption in Transit**

Network par transfer hote waqt data ko protect karta hai.

Example: TLS/HTTPS connection.

**C. TDE (Transparent Data Encryption)**

Database files ko storage level par encrypt karta hai. Isse application ko generally normal queries mein changes nahi karne padte.

**Key Management:** Encryption keys ko securely store, restrict, rotate aur backup karna zaroori hai.

## 7. SQL Injection Attack

SQL Injection ek attack hai jisme attacker input ke through malicious SQL query execute karwane ki koshish karta hai.

**Unsafe example:**

```javascript
const query = "SELECT * FROM users WHERE email = '" + email + "'";
```

Agar input ko directly query mein joda jaye, to SQL injection ka risk hota hai.

**Safe approach – Parameterized Query:**

```javascript
const result = await db.query("SELECT * FROM users WHERE email = ?", [email]);
```

Placeholder syntax database driver ke according change ho sakti hai.

### SQL Injection se protection

1. Parameterized queries / prepared statements use karo.
2. User input ko SQL string ke saath concatenate mat karo.
3. Least privilege follow karo.
4. Input validation karo.
5. Database errors aur sensitive details users ko expose mat karo.
6. Database drivers aur software updated rakho.

**Important:** ORM use karne se automatically har SQL injection vulnerability solve nahi hoti. Raw queries mein bhi parameterization zaroori hai.

## 8. Other Database Security Practices

- Strong authentication aur MFA where supported.
- Role-based permissions.
- TLS connections.
- Private network ya IP allowlisting.
- Regular security patches.
- Audit logs aur monitoring.
- Sensitive data masking.
- Secrets ko environment variables ya secret manager mein rakhna.
- Database ko unnecessarily public internet par expose na karna.

## 9. MongoDB Security

MERN stack mein MongoDB security ke important points:

1. Authentication enable rakho.
2. Database users ko proper roles do.
3. MongoDB ko public internet par openly expose mat karo.
4. Network access ko restrict karo.
5. TLS use karo.
6. Connection string aur credentials secret rakho.
7. Regular backups lo.
8. Database aur dependencies updated rakho.

**Mongoose example:**

```javascript
import mongoose from "mongoose";

await mongoose.connect(process.env.MONGO_URI);
```

`.env` example:

```env
MONGO_URI=mongodb://username:password@host:27017/mydb
```

`.env` ko GitHub par upload nahi karna chahiye. `.gitignore` mein add karo.

## 10. Database Backup kya hai?

Backup ka matlab database ki extra copy banana, taaki data delete, corrupt ya lost hone par recover kiya ja sake.

Example: Server crash ho gaya, lekin backup available hai. Backup se database restore kiya ja sakta hai.

### Types of Backup

| Type                | Meaning                                     |
| ------------------- | ------------------------------------------- |
| Full Backup         | Complete database ka backup                 |
| Incremental Backup  | Last backup ke baad ke changes              |
| Differential Backup | Last full backup ke baad ke changes         |
| Logical Backup      | SQL commands / logical records ke form mein |
| Physical Backup     | Actual database files ka backup             |

### Full vs Incremental vs Differential

Example:

- Monday: Full backup
- Tuesday: Changes ka backup
- Wednesday: Changes ka backup

**Incremental:** Har backup mein previous backup ke baad ke changes.

**Differential:** Har backup mein last full backup ke baad ke changes.

## 11. 3-2-1 Backup Rule

Reliable backup ke liye 3-2-1 rule follow kar sakte hain.

- 3 copies of data.
- 2 different storage media.
- 1 copy offsite.

Additional protection: Ek immutable ya offline copy bhi rakho, taaki ransomware backup ko bhi modify/delete na kar sake.

## 12. Database Recovery

Recovery ka matlab failure ya data loss ke baad database ko usable state mein wapas lana.

Recovery ke common methods:

- Backup restore.
- Transaction logs.
- Write-Ahead Logging (WAL).
- Binary logs.
- Point-in-Time Recovery (PITR).

**Point-in-Time Recovery:** Database ko kisi specific time tak restore karna, agar required backups aur logs available hon.

Example: 2:00 PM par galti se data delete hua. PITR se database ko 1:59 PM ke aas-paas ki state mein restore kiya ja sakta hai.

## 13. RPO vs RTO

| RPO                             | RTO                                           |
| ------------------------------- | --------------------------------------------- |
| Recovery Point Objective        | Recovery Time Objective                       |
| Kitna data loss acceptable hai? | Service kitne time mein restore honi chahiye? |
| Time mein measure hota hai      | Time mein measure hota hai                    |

Example:

- RPO = 15 minutes: Maximum acceptable data loss approximately last 15 minutes ka hai.
- RTO = 1 hour: Service ko target ke according 1 hour ke andar restore karna hai.

## 14. Replication vs Backup

| Replication                                        | Backup                                         |
| -------------------------------------------------- | ---------------------------------------------- |
| Data ki copies dusre server par maintain karta hai | Data ki separate recoverable copy banata hai   |
| Availability improve karta hai                     | Data recovery mein help karta hai              |
| Accidental deletion replicate ho sakti hai         | Older backup se recovery possible ho sakti hai |

**Important:** Replication backup ka replacement nahi hai.

RAID bhi backup ka replacement nahi hai. RAID disk failure tolerance improve kar sakta hai, lekin accidental deletion ya ransomware se complete protection nahi deta.

## 15. Common Database Backup Commands

Commands DBMS-specific hoti hain.

### PostgreSQL

Backup:

```bash
pg_dump -U username -d database_name -F c -f backup.dump
```

Restore:

```bash
pg_restore -U username -d database_name backup.dump
```

### MySQL

Backup:

```bash
mysqldump -u username -p database_name > backup.sql
```

Restore:

```bash
mysql -u username -p database_name < backup.sql
```

### MongoDB

Backup:

```bash
mongodump --uri="YOUR_MONGO_URI" --out="./backup"
```

Restore:

```bash
mongorestore --uri="YOUR_MONGO_URI" ./backup
```

Note: Credentials ko public code ya command history mein expose mat karo. Production backup/restore commands ko actual DB version aur environment ke according verify karo.

## 16. MERN Stack mein Database Security

MERN application mein basic security flow:

```text
React Frontend
      |
      v
Node.js + Express Backend
      |
      v
Authentication + Authorization
      |
      v
MongoDB Database
```

Important practices:

- Passwords ko bcrypt/Argon2id jaise password hashing algorithm se hash karo.
- JWT/session ko securely handle karo.
- Backend par authorization check karo.
- MongoDB credentials `.env` mein rakho.
- User input validate karo.
- MongoDB queries safely construct karo.
- Production mein TLS aur restricted network access use karo.
- Automated backups aur restore testing rakho.

## 17. Backup Testing and Disaster Recovery

Sirf backup bana lena sufficient nahi hai. Restore test bhi karna zaroori hai.

Checklist:

- [ ] Automatic backups configured hain.
- [ ] Backup encryption enabled hai.
- [ ] Backup offsite ya separate storage par hai.
- [ ] Backup retention policy defined hai.
- [ ] Restore regularly test hota hai.
- [ ] RPO aur RTO defined hain.
- [ ] Access permissions restricted hain.
- [ ] Recovery process documented hai.

**Disaster Recovery Plan:** Aisa documented plan jo major failure ke baad database aur application ko restore karne mein help kare.

## 18. Important Interview Questions

**Q1. Database Security kya hai?**

Database ko unauthorized access, data theft, modification aur loss se protect karna.

**Q2. CIA Triad kya hai?**

Confidentiality, Integrity aur Availability.

**Q3. Authentication vs Authorization?**

Authentication identity verify karta hai; authorization permissions check karta hai.

**Q4. SQL Injection kya hai?**

Malicious input ke through SQL query manipulate ya execute karne ka attack.

**Q5. SQL Injection kaise prevent karte hain?**

Parameterized queries, prepared statements, validation aur least privilege se.

**Q6. Hashing vs Encryption?**

Hashing generally one-way hoti hai; encryption key ke through reversible hoti hai.

**Q7. Full vs Incremental Backup?**

Full complete data copy karta hai; incremental previous backup ke baad ke changes save karta hai.

**Q8. RPO vs RTO?**

RPO acceptable data loss define karta hai; RTO acceptable recovery time.

**Q9. Replication backup ka replacement kyun nahi hai?**

Accidental deletion ya corruption replica par bhi copy ho sakti hai.

**Q10. 3-2-1 rule kya hai?**

3 copies, 2 different media, 1 offsite copy.

**Q11. Point-in-Time Recovery kya hai?**

Database ko kisi specific past time ki state mein restore karna.

**Q12. TDE kya hai?**

Transparent Data Encryption database storage files ko encrypt karta hai.

## 19. Practical Tasks

1. Authentication aur authorization ka difference apne words mein likho.
2. SQL GRANT aur REVOKE ke examples banao.
3. SQL Injection ka unsafe aur safe example samjho.
4. Full, incremental aur differential backup compare karo.
5. RPO aur RTO ka practical example banao.
6. MongoDB connection string ko `.env` mein store karo.
7. Apne MongoDB database ka backup aur restore process practice karo.

## 20. Quick Revision

- Database security data ko protect karti hai.
- CIA = Confidentiality, Integrity, Availability.
- Authentication = Identity verification.
- Authorization = Permission checking.
- RBAC = Role-Based Access Control.
- Least Privilege = Minimum required permissions.
- GRANT = Permission dena.
- REVOKE = Permission wapas lena.
- Hashing = Generally one-way.
- Encryption = Key se reversible.
- SQL Injection = Malicious SQL manipulation.
- Parameterized queries injection risk kam karti hain.
- Full Backup = Complete copy.
- Incremental = Previous backup ke baad changes.
- Differential = Last full backup ke baad changes.
- RPO = Acceptable data loss.
- RTO = Acceptable recovery time.
- Replication != Backup.
- RAID != Backup.
- 3-2-1 = 3 copies, 2 media, 1 offsite.
- PITR = Specific time par recovery.

## 21. MCQ Practice

**Q1. CIA Triad mein C ka matlab kya hai?**

A. Control  
B. Confidentiality  
C. Connection  
D. Communication

**Q2. User ki identity verify kaun karta hai?**

A. Authorization  
B. Authentication  
C. Encryption  
D. Backup

**Q3. Least Privilege ka kya meaning hai?**

A. Sabko admin access  
B. Minimum required permissions  
C. No password  
D. Public access

**Q4. SQL Injection se protection ke liye kya use karna chahiye?**

A. String concatenation  
B. Plain text password  
C. Parameterized queries  
D. Public database

**Q5. Password storage ke liye kaunsa suitable hai?**

A. Plain text  
B. Argon2id  
C. Base64  
D. Simple encoding

**Q6. Complete database copy kis backup mein hoti hai?**

A. Incremental  
B. Differential  
C. Full  
D. Partial

**Q7. RPO kya define karta hai?**

A. Acceptable data loss  
B. Database speed  
C. User permissions  
D. Query execution time

**Q8. Replication ke baare mein correct statement kya hai?**

A. Hamesha backup ka replacement hai  
B. Accidental deletion ko zaroor rokta hai  
C. Availability improve kar sakta hai, lekin backup ka replacement nahi  
D. Encryption algorithm hai

**Q9. 3-2-1 rule mein kitni copies recommended hain?**

A. 1  
B. 2  
C. 3  
D. 5

**Q10. PITR ka full form kya hai?**

A. Point-in-Time Recovery  
B. Process-in-Table Record  
C. Primary Index Transfer  
D. Password Integrity Test
