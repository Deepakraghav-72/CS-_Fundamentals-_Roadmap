# 06. Keys in DBMS – Primary Key, Foreign Key, Candidate Key, Super Key, Composite Key and Alternate Key

## 1. What are Keys in DBMS?

DBMS mein **Key** ek attribute (column) ya attributes ka group hota hai jo table ke records ko uniquely identify karne ya tables ke beech relationship establish karne mein help karta hai.

Simple words mein:

Key ka use database mein kisi particular row ko identify karne, duplicate records ko prevent karne aur tables ke beech connection banane ke liye hota hai.

### Example

Consider a `Students` table:

| Student_ID | Name  | Email           | Course |
| ---------- | ----- | --------------- | ------ |
| 101        | Rahul | rahul@gmail.com | BCA    |
| 102        | Aman  | aman@gmail.com  | BCA    |
| 103        | Ravi  | ravi@gmail.com  | BBA    |

Yahan:

- `Student_ID` har student ke liye unique hai.
- `Email` bhi har student ke liye unique ho sakta hai.
- `Name` unique nahi hai, kyunki same name ke multiple students ho sakte hain.

Isliye `Student_ID` aur `Email` records ko uniquely identify karne ke liye use ho sakte hain.

## 2. Why are Keys Important?

Keys database mein multiple important tasks perform karti hain:

1. **Unique Identification:** Har record ko uniquely identify karna.
2. **Prevent Duplicates:** Duplicate values ko prevent karna, according to the selected constraint.
3. **Establish Relationships:** Different tables ke beech relationship banana.
4. **Data Integrity:** Database mein correct aur consistent data maintain karna.
5. **Referential Integrity:** Ensure karna ki foreign key kisi valid referenced record ko point kare.
6. **Efficient Data Retrieval:** Keys par indexes hone se searching fast ho sakti hai.

> Important: Key aur Index same cheez nahi hain. Key data rules define karti hai; index searching aur retrieval performance improve karne ka structure hai.

## 3. Types of Keys in DBMS

DBMS mein commonly ye keys use hoti hain:

1. Super Key
2. Candidate Key
3. Primary Key
4. Alternate Key
5. Foreign Key
6. Composite Key
7. Simple Key
8. Natural Key
9. Surrogate Key
10. Unique Key
11. Secondary Key
12. Partial Key

---

## 4. Super Key

**Definition:**

A Super Key is a set of one or more attributes that can uniquely identify every row in a table.

Simple words mein, ek ya multiple columns ka aisa combination jo kisi bhi row ko uniquely identify kar sake, Super Key kehlata hai.

### Example

| Student_ID | Email       | Name  |
| ---------- | ----------- | ----- |
| 101        | a@gmail.com | Aman  |
| 102        | b@gmail.com | Rahul |
| 103        | c@gmail.com | Ravi  |

Assume:

- `Student_ID` unique hai.
- `Email` unique hai.

Possible Super Keys:

- Student_ID
- Email
- Student_ID + Name
- Email + Name
- Student_ID + Email
- Student_ID + Email + Name

In sab combinations se row uniquely identify ho sakti hai.

### Important Point

Super Key mein unnecessary extra attributes ho sakte hain.

For example:

`Student_ID` alone is enough to identify a student.

But:

`Student_ID + Name` bhi Super Key hai, although `Name` extra attribute hai.

---

## 5. Candidate Key

**Definition:**

A Candidate Key is a minimal Super Key that uniquely identifies every row in a table.

Simple words mein, Super Key ka aisa smallest possible combination jisme koi unnecessary column na ho, Candidate Key kehlata hai.

### Example

| Student_ID | Email       | Name  |
| ---------- | ----------- | ----- |
| 101        | a@gmail.com | Aman  |
| 102        | b@gmail.com | Rahul |
| 103        | c@gmail.com | Ravi  |

Assume `Student_ID` aur `Email` dono unique hain.

Candidate Keys:

- Student_ID
- Email

`Student_ID + Name` Candidate Key nahi hai, kyunki `Name` remove karne ke baad bhi `Student_ID` uniquely identify kar sakta hai.

### Properties

- Candidate Key uniquely identify karti hai.
- Ye minimal Super Key hoti hai.
- Isme unnecessary attributes nahi hote.
- Ek table mein multiple Candidate Keys ho sakti hain.

### Super Key vs Candidate Key

| Super Key                      | Candidate Key               |
| ------------------------------ | --------------------------- |
| Uniquely identify karti hai    | Uniquely identify karti hai |
| Extra attributes ho sakte hain | Extra attributes nahi hote  |
| Minimal hona necessary nahi    | Minimal hona necessary hai  |
| Multiple possible combinations | Minimal unique combinations |

**Remember:** Every Candidate Key is a Super Key, but every Super Key is not a Candidate Key.

---

## 6. Primary Key

**Definition:**

A Primary Key is a Candidate Key selected to uniquely identify every record in a table.

Simple words mein, jab multiple Candidate Keys available hoti hain, tab unmein se ek ko main identifier ke roop mein select kiya jaata hai. Use Primary Key kehte hain.

### Example

| Student_ID (PK) | Email       | Name  |
| --------------- | ----------- | ----- |
| 101             | a@gmail.com | Aman  |
| 102             | b@gmail.com | Rahul |
| 103             | c@gmail.com | Ravi  |

Yahan `Student_ID` Primary Key hai.

### Properties of Primary Key

1. Primary Key ki value unique honi chahiye.
2. Primary Key NULL nahi ho sakti.
3. Ek table mein sirf ek Primary Key constraint hota hai.
4. Primary Key single column ya multiple columns se ban sakti hai.
5. Primary Key stable honi chahiye; unnecessary changes avoid karne chahiye.

### SQL Example

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Email VARCHAR(100)
);
```

Insert records:

```sql
INSERT INTO Students
VALUES (101, 'Aman', 'aman@gmail.com');

INSERT INTO Students
VALUES (102, 'Rahul', 'rahul@gmail.com');
```

Duplicate Primary Key:

```sql
INSERT INTO Students
VALUES (101, 'Ravi', 'ravi@gmail.com');
```

Ye insert fail hoga, kyunki `Student_ID = 101` already exist karta hai.

NULL Primary Key:

```sql
INSERT INTO Students
VALUES (NULL, 'Ravi', 'ravi@gmail.com');
```

Ye bhi fail hoga, kyunki Primary Key NULL allow nahi karti.

---

## 7. Alternate Key

**Definition:**

An Alternate Key is a Candidate Key that is not selected as the Primary Key.

Simple words mein, table mein jitni Candidate Keys hoti hain, unmein se ek Primary Key ban jaati hai. Baaki Candidate Keys Alternate Keys kehlati hain.

### Example

| Student_ID | Email       | Name  |
| ---------- | ----------- | ----- |
| 101        | a@gmail.com | Aman  |
| 102        | b@gmail.com | Rahul |
| 103        | c@gmail.com | Ravi  |

Assume:

- `Student_ID` unique hai.
- `Email` unique hai.

Candidate Keys:

- Student_ID
- Email

Agar `Student_ID` ko Primary Key select kiya:

- Primary Key = Student_ID
- Alternate Key = Email

### SQL Example

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Name VARCHAR(50)
);
```

Yahan:

- `Student_ID` Primary Key hai.
- `Email` par UNIQUE constraint hai.
- Email ek Alternate Key ke roop mein use ho sakti hai, assuming it is a candidate key.

---

## 8. Foreign Key

**Definition:**

A Foreign Key is an attribute or set of attributes in one table that references a candidate key (commonly a Primary Key) or another eligible unique key in the same or another table.

Simple words mein, Foreign Key ka use do tables ke beech relationship establish karne ke liye hota hai.

### Example

**Customers Table**

| Customer_ID (PK) | Name  |
| ---------------- | ----- |
| 1                | Aman  |
| 2                | Rahul |
| 3                | Ravi  |

**Orders Table**

| Order_ID (PK) | Order_Name | Customer_ID (FK) |
| ------------- | ---------- | ---------------- |
| 101           | Laptop     | 1                |
| 102           | Mobile     | 2                |
| 103           | Keyboard   | 1                |

Yahan:

- `Customers.Customer_ID` Primary Key hai.
- `Orders.Customer_ID` Foreign Key hai.

Foreign Key batati hai ki kaunsa order kis customer ka hai.

### Referential Integrity

Referential Integrity ek rule hai jo ensure karta hai ki Foreign Key ki non-NULL value referenced table mein valid referenced key value se match kare.

Example:

Customers table mein Customer_ID = 1, 2, 3 available hain.

Orders table mein:

```text
Customer_ID = 1  Valid
Customer_ID = 2  Valid
Customer_ID = 3  Valid
Customer_ID = 5  Invalid (if customer 5 does not exist)
```

Agar Foreign Key constraint properly applied hai, to invalid reference insert nahi ho payega.

Foreign Key NULL bhi ho sakti hai, agar column par NOT NULL constraint nahi laga hai.

### SQL Example

```sql
CREATE TABLE Customers (
    Customer_ID INT PRIMARY KEY,
    Name VARCHAR(50)
);
```

```sql
CREATE TABLE Orders (
    Order_ID INT PRIMARY KEY,
    Order_Name VARCHAR(50),
    Customer_ID INT,

    FOREIGN KEY (Customer_ID)
    REFERENCES Customers(Customer_ID)
);
```

### Foreign Key with ON DELETE CASCADE

```sql
CREATE TABLE Orders (
    Order_ID INT PRIMARY KEY,
    Customer_ID INT,

    FOREIGN KEY (Customer_ID)
    REFERENCES Customers(Customer_ID)
    ON DELETE CASCADE
);
```

Meaning:

Agar referenced customer delete hota hai, to us customer se related orders bhi automatically delete ho sakte hain.

### Other Referential Actions

| Action      | Meaning                                                                                             |
| ----------- | --------------------------------------------------------------------------------------------------- |
| CASCADE     | Parent change/delete hone par related child records bhi change/delete ho sakte hain                 |
| SET NULL    | Parent delete/update hone par FK NULL set ho sakti hai, if allowed                                  |
| RESTRICT    | Referenced record ko delete/update karne se rokta hai when dependent records exist                  |
| NO ACTION   | Constraint violation hone par operation reject hota hai; exact timing DBMS par depend kar sakti hai |
| SET DEFAULT | FK ko default value par set karta hai, if supported and valid                                       |

> Important: CASCADE ka use carefully karna chahiye. Galat configuration se important child records delete ho sakte hain. Exact syntax aur behavior DBMS ke according vary kar sakte hain.

---

## 9. Composite Key

**Definition:**

A Composite Key is a key that consists of two or more attributes which together uniquely identify a record.

Simple words mein, jab ek single column se record uniquely identify nahi hota, tab multiple columns ko combine karke key banayi jaati hai.

### Example

**Student_Courses Table**

| Student_ID | Course_ID | Enrollment_Date |
| ---------- | --------- | --------------- |
| 101        | C01       | 2026-01-10      |
| 101        | C02       | 2026-01-12      |
| 102        | C01       | 2026-01-15      |

Yahan:

- Student_ID alone unique nahi hai.
- Course_ID alone unique nahi hai.
- Student_ID + Course_ID ka combination unique hai.

Therefore:

`(Student_ID, Course_ID)` = Composite Primary Key.

### SQL Example

```sql
CREATE TABLE Student_Courses (
    Student_ID INT,
    Course_ID VARCHAR(10),
    Enrollment_Date DATE,

    PRIMARY KEY (Student_ID, Course_ID)
);
```

### Important Points

- Composite Key mein two or more columns hote hain.
- Individual columns unique hona necessary nahi hai.
- Combined values unique honi chahiye.
- Composite Key Primary Key, Candidate Key ya Foreign Key ke roop mein use ho sakti hai, depending on context.

**Composite Key vs Concatenated Value:**

Composite Key ka matlab multiple columns ko logically key banana hai. Unhe string mein jodna necessary nahi hai.

---

## 10. Simple Key

**Definition:**

A Simple Key is a key that consists of only one attribute.

Example:

```text
Student_ID = 101
```

Agar `Student_ID` alone uniquely identify karta hai, to ye Simple Key ho sakti hai.

### Simple Key vs Composite Key

| Simple Key                         | Composite Key                         |
| ---------------------------------- | ------------------------------------- |
| One column                         | Two or more columns                   |
| Example: Student_ID                | Example: Student_ID + Course_ID       |
| Single attribute se identification | Combined attributes se identification |

---

## 11. Natural Key

**Definition:**

A Natural Key is a key based on a real-world meaningful attribute of an entity.

Simple words mein, jo value real life mein already kisi entity ko identify karne ke kaam aati hai, use Natural Key kehte hain.

### Examples

- Email address
- Passport number
- Vehicle registration number
- Government-issued identification number

### Advantages

- Meaningful hoti hai.
- Real-world data se directly related hoti hai.
- Extra artificial ID ki requirement kabhi-kabhi avoid kar sakti hai.

### Disadvantages

- Value change ho sakti hai.
- Privacy concerns ho sakte hain.
- Kabhi-kabhi value lengthy hoti hai.
- Business rules change hone par key problematic ho sakti hai.

Example: Kisi user ka email address change ho sakta hai. Isliye email ko Primary Key banana har system ke liye best choice nahi hota.

---

## 12. Surrogate Key

**Definition:**

A Surrogate Key is an artificial identifier created by the system, which has no direct business meaning.

Simple words mein, jab hum kisi record ko identify karne ke liye khud ek ID generate karte hain, use Surrogate Key kehte hain.

### Example

| User_ID | Name  | Email           |
| ------- | ----- | --------------- |
| 1       | Aman  | aman@gmail.com  |
| 2       | Rahul | rahul@gmail.com |
| 3       | Ravi  | ravi@gmail.com  |

Yahan `User_ID` ek Surrogate Key hai.

### Examples of Surrogate Keys

- Auto-increment integer
- UUID
- Generated unique identifier

### SQL Example

Auto-increment syntax DBMS-specific hota hai.

MySQL example:

```sql
CREATE TABLE Users (
    User_ID INT AUTO_INCREMENT PRIMARY KEY,
    Name VARCHAR(50),
    Email VARCHAR(100) UNIQUE
);
```

PostgreSQL example:

```sql
CREATE TABLE Users (
    User_ID INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    Name VARCHAR(50),
    Email VARCHAR(100) UNIQUE
);
```

### Advantages

- Usually stable hoti hai.
- Real-world data change hone se identifier change nahi hota.
- Relationships manage karna easy hota hai.
- Compact integer IDs indexing ke liye useful ho sakti hain.

### Disadvantages

- Extra column maintain karna padta hai.
- Business meaning represent nahi karti.
- Sequential IDs ko public expose karne se record count ya enumeration ka risk ho sakta hai.

> Security Tip: Sirf ID ko difficult-to-guess banane se authorization secure nahi hota. Har request mein user ki permission aur record ownership verify karna zaroori hai.

---

## 13. Unique Key

**Definition:**

A UNIQUE constraint ensures that values in a column or a combination of columns are unique according to the DBMS rules.

Simple words mein, UNIQUE constraint duplicate values ko prevent karta hai.

### SQL Example

```sql
CREATE TABLE Users (
    User_ID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Username VARCHAR(50) UNIQUE
);
```

Yahan:

- User_ID Primary Key hai.
- Email UNIQUE hai.
- Username UNIQUE hai.

### Primary Key vs Unique Key

| Primary Key                          | Unique Key                           |
| ------------------------------------ | ------------------------------------ |
| Main row identifier                  | Unique values enforce karti hai      |
| NULL allowed nahi                    | NULL handling DBMS-specific hai      |
| One Primary Key constraint per table | Multiple UNIQUE constraints possible |
| Table ki primary identification      | Additional uniqueness rules          |

### Important NULL Point

Different DBMS UNIQUE constraints mein NULL ko differently handle kar sakte hain.

For example:

- PostgreSQL by default multiple NULL values allow karta hai in a UNIQUE column.
- SQL Server generally UNIQUE constraint mein ek NULL allow karta hai.
- MySQL UNIQUE index mein multiple NULL values allow karta hai.

Isliye kabhi bhi ye assume mat karna ki UNIQUE har DBMS mein NULL ko same way handle karta hai.

---

## 14. Secondary Key

**Definition:**

Secondary Key is an attribute or set of attributes used mainly for searching or retrieving records, and it may not uniquely identify a row.

Example:

| Student_ID | Name  | City   |
| ---------- | ----- | ------ |
| 101        | Aman  | Delhi  |
| 102        | Rahul | Meerut |
| 103        | Ravi  | Delhi  |

Yahan `City` se Delhi ke students search kiye ja sakte hain.

Lekin City unique nahi hai, kyunki multiple students Delhi mein ho sakte hain.

So, some textbooks call `City` a Secondary Key.

> Note: Secondary Key ki terminology different textbooks aur database contexts mein vary karti hai. Isse Alternate Key ke saath confuse nahi karna chahiye.

---

## 15. Partial Key

**Definition:**

A Partial Key is an attribute of a weak entity that uniquely identifies the weak entity only within the context of its owner entity.

Ye concept ER Model mein use hota hai.

### Example

Suppose:

- Employee ek strong entity hai.
- Dependent ek weak entity hai.

Ek employee ke multiple dependents ho sakte hain.

Dependent table:

| Employee_ID | Dependent_Name |
| ----------- | -------------- |
| 101         | Rahul          |
| 101         | Priya          |
| 102         | Rahul          |

Yahan `Dependent_Name` alone globally unique nahi hai.

Lekin:

`Employee_ID + Dependent_Name`

Weak entity ko identify kar sakta hai, assuming each employee ke dependents ke names unique hain.

Is example mein `Dependent_Name` Partial Key hai.

---

## 16. Complete Example – Keys in a Database

Ab ek practical database example dekhte hain.

### Students Table

| Student_ID | Email           | Name  |
| ---------- | --------------- | ----- |
| 101        | aman@gmail.com  | Aman  |
| 102        | rahul@gmail.com | Rahul |
| 103        | ravi@gmail.com  | Ravi  |

Assume:

- Student_ID unique hai.
- Email unique hai.

Keys:

- Super Keys: Student_ID, Email, Student_ID + Name, etc.
- Candidate Keys: Student_ID, Email.
- Primary Key: Student_ID.
- Alternate Key: Email.

### Courses Table

| Course_ID | Course_Name |
| --------- | ----------- |
| C01       | MERN        |
| C02       | DSA         |
| C03       | Python      |

- Course_ID = Primary Key.

### Enrollments Table

| Student_ID | Course_ID | Enrollment_Date |
| ---------- | --------- | --------------- |
| 101        | C01       | 2026-01-10      |
| 101        | C02       | 2026-01-12      |
| 102        | C01       | 2026-01-15      |

Keys:

- Student_ID + Course_ID = Composite Primary Key.
- Student_ID = Foreign Key referencing Students.
- Course_ID = Foreign Key referencing Courses.

### Relationship Diagram

```text
+------------------+
|     STUDENTS     |
+------------------+
| Student_ID (PK)  |
| Email (UNIQUE)   |
| Name             |
+------------------+
         |
         | 1
         |
         | Many
+------------------------+
|      ENROLLMENTS       |
+------------------------+
| Student_ID (PK, FK)    |
| Course_ID  (PK, FK)    |
| Enrollment_Date        |
+------------------------+
         |
         | Many
         |
         | 1
+------------------+
|     COURSES      |
+------------------+
| Course_ID (PK)   |
| Course_Name      |
+------------------+
```

Enrollments table many-to-many relationship ko resolve karti hai.

---

## 17. Key, Constraint and Index – Difference

Ye three concepts related hain, lekin same nahi hain.

| Concept    | Meaning                                                         |
| ---------- | --------------------------------------------------------------- |
| Key        | Attributes jo identification ya relationship mein use hote hain |
| Constraint | Rules jo data par apply hote hain                               |
| Index      | Data retrieval ko efficient banane wala structure               |

Examples:

- PRIMARY KEY = Key + uniqueness and NOT NULL rules.
- FOREIGN KEY = Referential integrity constraint.
- UNIQUE = Uniqueness constraint.
- INDEX = Searching performance improve karne ka structure.

> Important: Primary Key aur UNIQUE constraint create karne par many DBMS automatically supporting unique index create karte hain, but exact implementation DBMS-specific hoti hai.

---

## 18. Keys in MongoDB and MERN Stack

MERN Stack mein MongoDB database use hota hai.

MongoDB relational database ki tarah traditional Primary Key aur Foreign Key constraints use nahi karta.

### MongoDB _id Field

MongoDB collection ke har document mein `_id` field hoti hai.

Example:

```javascript
{
    _id: ObjectId("..."),
    name: "Aman",
    email: "aman@gmail.com",
    age: 22
}
```

Important points:

- `_id` document ka unique identifier hota hai.
- Agar `_id` provide nahi karte, MongoDB normally automatically generate karta hai.
- `_id` collection mein unique hota hai.
- `_id` ko MongoDB mein primary identifier ke roop mein samajh sakte hain.

### MongoDB Reference Example

Users collection:

```javascript
{
    _id: ObjectId("..."),
    name: "Aman"
}
```

Orders collection:

```javascript
{
    _id: ObjectId("..."),
    product: "Laptop",
    userId: ObjectId("...")
}
```

Yahan `userId` Users collection ke `_id` ko refer kar sakta hai.

### Mongoose Example

```javascript
const orderSchema = new mongoose.Schema({
  product: String,

  userId: {
    type: mongoose.Schema.Types.ObjectId,
    ref: "User",
  },
});
```

Important:

- `ref` Mongoose ko batata hai ki reference kis model se related hai.
- `ref` automatically relational Foreign Key constraint create nahi karta.
- MongoDB by default SQL-style referential integrity enforce nahi karta.
- Application-level validation, proper deletion handling aur transactions ki zaroorat ho sakti hai.

### Interview Point

**Q: Does MongoDB support Foreign Keys?**

Answer:

MongoDB does not provide traditional relational Foreign Key constraints. References can be stored between documents, but referential integrity is generally managed by application logic.

---

## 19. Important Differences – Quick Comparison

### Primary Key vs Foreign Key

| Primary Key                        | Foreign Key                                      |
| ---------------------------------- | ------------------------------------------------ |
| Row ko uniquely identify karti hai | Tables ke beech relationship establish karti hai |
| Unique honi chahiye                | Values repeat ho sakti hain                      |
| NULL allowed nahi                  | NULL allowed ho sakti hai, if defined            |
| Table mein one PK constraint       | Multiple FK constraints possible                 |
| Referenced key ban sakti hai       | Referencing key hoti hai                         |

### Candidate Key vs Alternate Key

| Candidate Key             | Alternate Key                                        |
| ------------------------- | ---------------------------------------------------- |
| Minimal Super Key         | Unselected Candidate Key                             |
| Primary Key ban sakti hai | Primary Key select hone ke baad baaki Candidate Keys |
| Multiple ho sakti hain    | Zero ya multiple ho sakti hain                       |

### Natural Key vs Surrogate Key

| Natural Key                   | Surrogate Key                  |
| ----------------------------- | ------------------------------ |
| Real-world meaning rakhti hai | Artificially generate hoti hai |
| Example: Email                | Example: User_ID               |
| Change ho sakti hai           | Usually stable hoti hai        |
| Privacy concern ho sakta hai  | Business meaning nahi hota     |

---

## 20. Common Mistakes

1. **Super Key aur Candidate Key ko same samajhna.**
   - Candidate Key minimal Super Key hoti hai.

2. **Sochna ki ek table mein sirf ek Candidate Key ho sakti hai.**
   - Multiple Candidate Keys ho sakti hain.

3. **Primary Key aur Foreign Key ko confuse karna.**
   - PK identifies rows; FK establishes references.

4. **Sochna ki Foreign Key values always unique hoti hain.**
   - Foreign Key values repeat ho sakti hain.

5. **Sochna ki Foreign Key NULL nahi ho sakti.**
   - NULL allowed hai, if column permits it.

6. **Composite Key mein har individual column unique hona necessary samajhna.**
   - Combined values unique honi chahiye.

7. **UNIQUE constraint ke NULL behavior ko har DBMS mein same samajhna.**
   - NULL handling DBMS-specific hai.

8. **Sochna ki Mongoose `ref` automatically Foreign Key constraint bana deta hai.**
   - MongoDB mein traditional FK constraint automatically enforce nahi hota.

9. **Sequential ID ko security samajhna.**
   - Authorization aur ownership checks zaroori hain.

10. **CASCADE ka use bina consequences samjhe karna.**
    - Parent delete hone par child data bhi delete ho sakta hai.

---

## 21. Interview Questions and Answers

### Q1. What is a Key in DBMS?

A Key is an attribute or set of attributes used to identify records uniquely or establish relationships between tables.

### Q2. What is a Super Key?

A Super Key is any set of one or more attributes that uniquely identifies a row in a table.

### Q3. What is a Candidate Key?

A Candidate Key is a minimal Super Key with no unnecessary attributes.

### Q4. What is a Primary Key?

A Primary Key is the Candidate Key selected to uniquely identify records in a table. It cannot contain NULL values.

### Q5. What is an Alternate Key?

Candidate Keys that are not selected as the Primary Key are called Alternate Keys.

### Q6. What is a Foreign Key?

A Foreign Key is an attribute or group of attributes that references an eligible key in another or the same table.

### Q7. Can a table have multiple Primary Keys?

A table can have only one Primary Key constraint, but that Primary Key can contain multiple columns.

### Q8. Can a Foreign Key contain duplicate values?

Yes. Multiple rows can reference the same parent record.

### Q9. Can a Foreign Key contain NULL?

Yes, if the column is not defined as NOT NULL and the DBMS constraints permit it.

### Q10. What is a Composite Key?

A Composite Key consists of two or more attributes that together identify a row uniquely.

### Q11. What is the difference between Super Key and Candidate Key?

A Super Key may contain extra attributes, while a Candidate Key is a minimal Super Key.

### Q12. What is the difference between Primary Key and UNIQUE?

Primary Key is the main identifier and cannot contain NULL. UNIQUE enforces uniqueness, with NULL behavior depending on the DBMS.

### Q13. What is a Natural Key?

A Natural Key is based on meaningful real-world data, such as an email address or registration number.

### Q14. What is a Surrogate Key?

A Surrogate Key is an artificial identifier generated by the system, such as an auto-increment ID or UUID.

### Q15. Does MongoDB support Primary Keys?

MongoDB uses the `_id` field as the unique identifier for each document in a collection.

---

## 22. Practical Tasks

### Task 1: Create a Students Table

Requirements:

- Student_ID as Primary Key.
- Email as UNIQUE.
- Name as NOT NULL.
- Age as another column.

### Task 2: Create Courses Table

Requirements:

- Course_ID as Primary Key.
- Course_Name as NOT NULL.

### Task 3: Create Enrollments Table

Requirements:

- Student_ID as Foreign Key.
- Course_ID as Foreign Key.
- Student_ID + Course_ID as Composite Primary Key.
- Enrollment_Date column.

### Task 4: Test Constraints

Try:

- Inserting duplicate Primary Key.
- Inserting duplicate Email.
- Inserting NULL into Primary Key.
- Inserting an invalid Foreign Key.
- Inserting multiple orders for one customer.

Observe which operations succeed and which fail.

### Task 5: Explain in Your Own Words

Without looking at notes, explain:

1. Super Key.
2. Candidate Key.
3. Primary Key.
4. Foreign Key.
5. Composite Key.
6. Natural Key vs Surrogate Key.

---

## 23. Quick Revision

| Key           | One-Line Meaning                                         |
| ------------- | -------------------------------------------------------- |
| Super Key     | Any attribute combination that uniquely identifies a row |
| Candidate Key | Minimal Super Key                                        |
| Primary Key   | Selected Candidate Key                                   |
| Alternate Key | Candidate Key not selected as Primary Key                |
| Foreign Key   | References an eligible key in another or same table      |
| Composite Key | Two or more attributes together identify a row           |
| Simple Key    | Single-attribute key                                     |
| Natural Key   | Real-world meaningful identifier                         |
| Surrogate Key | Artificially generated identifier                        |
| Unique Key    | Enforces uniqueness                                      |
| Secondary Key | Often a non-unique search attribute; terminology varies  |
| Partial Key   | Identifies a weak entity within its owner context        |

### Remember These Rules

- Every Candidate Key is a Super Key.
- Every Primary Key is a Candidate Key.
- Every Alternate Key is a Candidate Key.
- Foreign Key values can repeat.
- Foreign Key can be NULL if permitted.
- Primary Key cannot be NULL.
- Composite Key uses multiple columns.
- MongoDB uses `_id` as document identifier.
- Key and Index are different concepts.

---

## 24. MCQ Quiz – Test Your Knowledge

**Q1. Which key uniquely identifies each row in a table?**

A. Foreign Key  
B. Primary Key  
C. Secondary Key  
D. Partial Key

**Q2. A minimal Super Key is called:**

A. Candidate Key  
B. Foreign Key  
C. Alternate Key  
D. Composite Key

**Q3. Which key can contain duplicate values?**

A. Primary Key  
B. Candidate Key  
C. Foreign Key  
D. Unique Key

**Q4. Which key is selected from Candidate Keys?**

A. Secondary Key  
B. Primary Key  
C. Foreign Key  
D. Partial Key

**Q5. A key consisting of two or more attributes is called:**

A. Simple Key  
B. Composite Key  
C. Natural Key  
D. Alternate Key

**Q6. Which is an example of a Surrogate Key?**

A. Email  
B. Passport Number  
C. Auto-generated User_ID  
D. Vehicle Registration Number

**Q7. Can a table have multiple Candidate Keys?**

A. Yes  
B. No  
C. Only two  
D. Only three

**Q8. Which field is the default unique identifier in MongoDB documents?**

A. userId  
B. primaryId  
C. _id  
D. ref

**Q9. Which key is based on real-world meaningful data?**

A. Surrogate Key  
B. Natural Key  
C. Foreign Key  
D. Secondary Key

**Q10. What is the main purpose of a Foreign Key?**

A. Store images  
B. Increase RAM  
C. Establish relationships between tables  
D. Delete all duplicate records

### Answer Key

1. B – Primary Key
2. A – Candidate Key
3. C – Foreign Key
4. B – Primary Key
5. B – Composite Key
6. C – Auto-generated User_ID
7. A – Yes
8. C – _id
9. B – Natural Key
10. C – Establish relationships between tables

---

**Topic 06 Completed – Keys in DBMS**

Next Topic: **07 – Relationships and Constraints in DBMS**

Is topic mein hum One-to-One, One-to-Many, Many-to-Many relationships, Entity Integrity, Referential Integrity, Domain Constraints, CHECK, NOT NULL, DEFAULT aur SQL constraints ko detail mein samjhenge.
