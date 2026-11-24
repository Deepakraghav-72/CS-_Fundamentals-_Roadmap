# 07. Relationships and Constraints in DBMS

## 1. Introduction to Relationships in DBMS

DBMS mein Relationship ka matlab hai do ya do se zyada tables ke beech connection.

Jab database mein data multiple tables mein store hota hai, tab un tables ko connect karne ke liye relationships use ki jaati hain.

### Example

Ek college database mein:

**Students Table**

| Student_ID | Student_Name |
| ---------- | ------------ |
| 101        | Aman         |
| 102        | Rahul        |
| 103        | Ravi         |

**Courses Table**

| Course_ID | Course_Name |
| --------- | ----------- |
| C01       | MERN        |
| C02       | DSA         |

Ek student multiple courses join kar sakta hai aur ek course multiple students join kar sakte hain.

Is connection ko database relationship kehte hain.

### Why are Relationships Important?

1. Data duplication kam karna.
2. Tables ke beech connection establish karna.
3. Data consistency maintain karna.
4. Database ko organized rakhna.
5. Data ko efficiently retrieve karna.
6. Related information ko manage karna.

---

## 2. Types of Relationships in DBMS

DBMS mein cardinality ke basis par three main relationships hoti hain:

1. One-to-One (1:1)
2. One-to-Many (1:N)
3. Many-to-Many (M:N)

Ek additional concept hai Self-Referencing Relationship, jisme table khud ko reference karti hai.

---

## 3. One-to-One Relationship (1:1)

**Definition:**

A One-to-One relationship means one record in Table A is associated with at most one record in Table B, and vice versa.

Simple words mein:

Ek record ka connection doosri table ke maximum ek record ke saath hota hai.

### Real-Life Example

Person aur Passport:

- Ek person ka ek current passport record ho sakta hai.
- Ek passport record ek hi person se related hota hai.

### Diagram

```text
+-------------+          +-------------+
|   PERSON    |          |   PASSPORT  |
+-------------+          +-------------+
| Person_ID   | 1 ---- 1 | Passport_ID |
| Name        |          | Person_ID   |
+-------------+          +-------------+
```

### SQL Example

```sql
CREATE TABLE Persons (
    Person_ID INT PRIMARY KEY,
    Name VARCHAR(50)
);

CREATE TABLE Passports (
    Passport_ID INT PRIMARY KEY,
    Person_ID INT UNIQUE,
    Passport_Number VARCHAR(30) UNIQUE,

    FOREIGN KEY (Person_ID)
    REFERENCES Persons(Person_ID)
);
```

Yahan `Person_ID` in Passports table par UNIQUE constraint hai.

Isliye ek person ke liye maximum ek passport row ho sakti hai.

**Important:** UNIQUE foreign key one-to-one relationship enforce karne mein help karti hai. Lekin isse ye guarantee nahi hoti ki har person ke paas passport record zaroor hoga.

### One-to-One Relationship Uses

- Person and Passport
- User and Profile
- Employee and Employee_Details
- Country and Capital (depending on the business rules)

---

## 4. One-to-Many Relationship (1:N)

**Definition:**

A One-to-Many relationship means one record in Table A can be associated with multiple records in Table B, but each record in Table B is associated with at most one record in Table A.

Simple words mein:

Ek parent record ke multiple child records ho sakte hain.

### Real-Life Example

One Customer can place multiple Orders.

- Ek customer multiple orders place kar sakta hai.
- Ek order ek customer se related hota hai.

### Diagram

```text
+----------------+          +----------------+
|   CUSTOMERS    |          |     ORDERS     |
+----------------+          +----------------+
| Customer_ID PK | 1 ---- N | Order_ID PK    |
| Name           |          | Customer_ID FK |
+----------------+          | Order_Date     |
                             +----------------+
```

### SQL Example

```sql
CREATE TABLE Customers (
    Customer_ID INT PRIMARY KEY,
    Name VARCHAR(50)
);

CREATE TABLE Orders (
    Order_ID INT PRIMARY KEY,
    Order_Date DATE,
    Customer_ID INT,

    FOREIGN KEY (Customer_ID)
    REFERENCES Customers(Customer_ID)
);
```

### Example Data

**Customers**

| Customer_ID | Name  |
| ----------- | ----- |
| 1           | Aman  |
| 2           | Rahul |

**Orders**

| Order_ID | Customer_ID |
| -------- | ----------- |
| 101      | 1           |
| 102      | 1           |
| 103      | 2           |
| 104      | 1           |

Customer 1 ke three orders hain.

Customer 2 ka one order hai.

### One-to-Many Relationship Uses

- Customer and Orders
- Department and Employees
- Author and Books
- Category and Products
- User and Blog Posts

**Important:** One-to-Many relationship mein Foreign Key generally Many side wali table mein hoti hai.

---

## 5. Many-to-Many Relationship (M:N)

**Definition:**

A Many-to-Many relationship means multiple records in Table A can be associated with multiple records in Table B.

Simple words mein:

Ek table ke multiple records doosri table ke multiple records se connected ho sakte hain.

### Real-Life Example

Students and Courses:

- Ek student multiple courses join kar sakta hai.
- Ek course multiple students join kar sakte hain.

### Diagram

```text
+-------------+       +-------------+
|  STUDENTS   |       |   COURSES   |
+-------------+       +-------------+
| Student_ID  | M---N | Course_ID   |
| Name        |       | Course_Name |
+-------------+       +-------------+
```

Lekin relational database mein direct M:N relationship ko generally junction table ke through implement karte hain.

### What is a Junction Table?

A Junction Table (also called Bridge Table or Associative Table) is used to convert a Many-to-Many relationship into two One-to-Many relationships.

### Diagram with Junction Table

```text
+-------------+       +------------------+       +-------------+
|  STUDENTS   |       |   ENROLLMENTS    |       |   COURSES   |
+-------------+       +------------------+       +-------------+
| Student_ID  | 1---N | Student_ID (FK)  | N---1 | Course_ID   |
| Name        |       | Course_ID (FK)   |       | Course_Name |
+-------------+       | Enroll_Date      |       +-------------+
                      +------------------+
```

### SQL Example

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50)
);

CREATE TABLE Courses (
    Course_ID INT PRIMARY KEY,
    Course_Name VARCHAR(50)
);

CREATE TABLE Enrollments (
    Student_ID INT,
    Course_ID INT,
    Enroll_Date DATE,

    PRIMARY KEY (Student_ID, Course_ID),

    FOREIGN KEY (Student_ID)
    REFERENCES Students(Student_ID),

    FOREIGN KEY (Course_ID)
    REFERENCES Courses(Course_ID)
);
```

### Example Data

**Students**

| Student_ID | Name  |
| ---------- | ----- |
| 101        | Aman  |
| 102        | Rahul |

**Courses**

| Course_ID | Course_Name |
| --------- | ----------- |
| C01       | MERN        |
| C02       | DSA         |

**Enrollments**

| Student_ID | Course_ID |
| ---------- | --------- |
| 101        | C01       |
| 101        | C02       |
| 102        | C01       |

Meaning:

- Aman is enrolled in MERN and DSA.
- Rahul is enrolled in MERN.

### Why Junction Table is Needed?

Relational databases mein M:N relationship ko junction table ke through implement karne se:

1. Data duplication kam hota hai.
2. Relationships properly maintain hoti hain.
3. Foreign Keys apply kar sakte hain.
4. Relationship ki additional information store kar sakte hain.

### Many-to-Many Uses

- Students and Courses
- Products and Orders
- Movies and Actors
- Users and Roles
- Doctors and Patients

---

## 6. Self-Referencing Relationship

**Definition:**

A Self-Referencing Relationship occurs when a table contains a Foreign Key that references its own Primary Key.

Simple words mein:

Jab ek table khud apne records ko reference karti hai, use Self-Referencing Relationship kehte hain.

### Example: Employees and Managers

Ek employee kisi doosre employee ka manager ho sakta hai.

**Employees Table**

| Employee_ID | Name  | Manager_ID |
| ----------- | ----- | ---------- |
| 1           | Rahul | NULL       |
| 2           | Aman  | 1          |
| 3           | Ravi  | 1          |
| 4           | Mohan | 2          |

Yahan:

- Rahul top-level manager hai.
- Aman aur Ravi, Rahul ke under work karte hain.
- Mohan, Aman ke under work karta hai.

### SQL Example

```sql
CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Manager_ID INT,

    FOREIGN KEY (Manager_ID)
    REFERENCES Employees(Employee_ID)
);
```

Yahan `Manager_ID` same table ke `Employee_ID` ko reference kar raha hai.

### Uses

- Employee and Manager
- Category and Parent Category
- Comments and Parent Comments
- Organizational Hierarchy

---

## 7. Relationship Cardinality

Cardinality batati hai ki ek entity ke kitne records doosri entity ke records ke saath associate ho sakte hain.

Common cardinalities:

| Cardinality | Meaning      |
| ----------- | ------------ |
| 1:1         | One-to-One   |
| 1:N         | One-to-Many  |
| N:1         | Many-to-One  |
| M:N         | Many-to-Many |

### Important Difference

One-to-Many aur Many-to-One ek hi relationship ko opposite direction se describe karte hain.

Example:

- One Customer → Many Orders = 1:N
- Many Orders → One Customer = N:1

---

## 8. Participation Constraints

Participation batati hai ki kisi relationship mein entity ke records ka participate karna compulsory hai ya optional.

Two types:

1. Total Participation
2. Partial Participation

### A. Total Participation

**Definition:**

Total Participation means every entity instance must participate in the relationship.

Simple words mein:

Entity ka har record relationship mein participate karna compulsory hai.

Example:

Suppose business rule hai ki har Order ka ek Customer hona compulsory hai.

To Orders entity ka Customer relationship mein Total Participation hoga.

ER Diagram mein Total Participation ko generally double line se represent karte hain.

```text
ORDERS == HAS == CUSTOMERS
```

### B. Partial Participation

**Definition:**

Partial Participation means participation in the relationship is optional for some entity instances.

Simple words mein:

Entity ke kuch records relationship mein participate kar sakte hain aur kuch nahi bhi.

Example:

Har Customer ne order place kiya ho, ye necessary nahi hai.

To Customers ka Orders relationship mein Partial Participation ho sakta hai.

ER Diagram mein Partial Participation ko generally single line se represent karte hain.

```text
CUSTOMERS ---- PLACES ---- ORDERS
```

### Total vs Partial Participation

| Total Participation                       | Partial Participation                  |
| ----------------------------------------- | -------------------------------------- |
| Participation compulsory                  | Participation optional                 |
| Every entity instance participates        | Some instances may not participate     |
| ER diagram: Double line                   | ER diagram: Single line                |
| Example: Every order must have a customer | Example: Customer may have zero orders |

**Note:** Exact business rule decide karta hai ki participation total hai ya partial.

---

# PART 2: CONSTRAINTS IN DBMS

## 9. What are Constraints in DBMS?

**Definition:**

Constraints are rules applied to database columns or tables to control the type and validity of data stored in them.

Simple words mein:

Constraints database mein incorrect, invalid ya unwanted data enter hone se prevent karti hain.

### Example

Suppose Students table mein:

- Student_ID duplicate nahi hona chahiye.
- Name empty nahi hona chahiye.
- Age negative nahi honi chahiye.
- Email unique honi chahiye.

In rules ko enforce karne ke liye Constraints use hoti hain.

### Why are Constraints Important?

1. Data accuracy maintain karna.
2. Duplicate data prevent karna.
3. Data integrity improve karna.
4. Invalid values ko reject karna.
5. Relationships maintain karna.
6. Database rules enforce karna.

---

## 10. Types of Constraints in DBMS

Important constraints:

1. NOT NULL
2. UNIQUE
3. PRIMARY KEY
4. FOREIGN KEY
5. CHECK
6. DEFAULT

Inke alawa conceptual level par:

- Domain Constraint
- Entity Integrity Constraint
- Referential Integrity Constraint
- Key Constraint

---

## 11. NOT NULL Constraint

**Definition:**

NOT NULL constraint ensures that a column cannot store NULL values.

Simple words mein:

Is column mein NULL value insert nahi kar sakte.

### SQL Example

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(100)
);
```

Yahan `Name` NULL nahi ho sakta.

Valid:

```sql
INSERT INTO Students
VALUES (101, 'Aman', 'aman@gmail.com');
```

Invalid:

```sql
INSERT INTO Students
VALUES (102, NULL, 'rahul@gmail.com');
```

Ye query fail hogi, kyunki Name NOT NULL hai.

**Important:** NULL ka meaning zero ya empty string nahi hota. NULL ka matlab missing/unknown/not applicable value ho sakta hai.

---

## 12. UNIQUE Constraint

**Definition:**

UNIQUE constraint ensures that values in a column or a group of columns are unique.

### SQL Example

```sql
CREATE TABLE Users (
    User_ID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE,
    Username VARCHAR(50) UNIQUE
);
```

Yahan Email aur Username duplicate nahi ho sakte.

### Composite UNIQUE Constraint

```sql
CREATE TABLE Student_Courses (
    ID INT PRIMARY KEY,
    Student_ID INT,
    Course_ID INT,

    UNIQUE (Student_ID, Course_ID)
);
```

Yahan same Student ko same Course mein duplicate enroll nahi kar sakte.

Lekin same Student different Courses mein enroll ho sakta hai.

**Note:** UNIQUE constraints mein NULL handling DBMS-specific hoti hai.

---

## 13. PRIMARY KEY Constraint

**Definition:**

PRIMARY KEY constraint uniquely identifies every row in a table and does not allow NULL values.

### SQL Example

```sql
CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,
    Name VARCHAR(50)
);
```

Rules:

- Duplicate values not allowed.
- NULL not allowed.
- One Primary Key constraint per table.
- Primary Key single-column ya composite ho sakti hai.

---

## 14. FOREIGN KEY Constraint

**Definition:**

FOREIGN KEY constraint ensures that a value in one table refers to an eligible key value in another or the same table.

### SQL Example

```sql
CREATE TABLE Departments (
    Department_ID INT PRIMARY KEY,
    Department_Name VARCHAR(50)
);

CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Department_ID INT,

    FOREIGN KEY (Department_ID)
    REFERENCES Departments(Department_ID)
);
```

Yahan Employees table ka Department_ID, Departments table ko reference karta hai.

Agar referenced department exist nahi karta, to invalid Department_ID insert nahi kar sakte.

**Note:** Foreign Key NULL allow kar sakti hai, agar column par NOT NULL constraint nahi laga hai.

---

## 15. CHECK Constraint

**Definition:**

CHECK constraint ensures that values satisfy a specified condition.

Simple words mein:

Column ya row ke data par condition lagane ke liye CHECK use karte hain.

### Example 1: Age Validation

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT CHECK (Age >= 18)
);
```

Age 18 ya usse greater honi chahiye.

### Example 2: Salary Validation

```sql
CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Salary DECIMAL(10,2) CHECK (Salary > 0)
);
```

Salary zero se greater honi chahiye.

### Example 3: Multiple Conditions

```sql
CREATE TABLE Products (
    Product_ID INT PRIMARY KEY,
    Price DECIMAL(10,2),
    Quantity INT,

    CHECK (Price > 0 AND Quantity >= 0)
);
```

**Important:** CHECK constraint mein NULL ke behavior ko samajhna zaroori hai. SQL mein CHECK generally tab reject karta hai jab condition FALSE ho; UNKNOWN (for example, NULL comparison) automatically FALSE nahi hota. Required values ke liye NOT NULL bhi use karo.

---

## 16. DEFAULT Constraint

**Definition:**

DEFAULT constraint automatically assigns a predefined value when no value is supplied for a column during insertion.

Simple words mein:

Agar INSERT query mein kisi column ki value provide nahi karte, to database us column mein default value store kar sakta hai.

### SQL Example

```sql
CREATE TABLE Users (
    User_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    City VARCHAR(50) DEFAULT 'Delhi',
    Status VARCHAR(20) DEFAULT 'Active'
);
```

Insert:

```sql
INSERT INTO Users (User_ID, Name)
VALUES (101, 'Aman');
```

Result:

| User_ID | Name | City  | Status |
| ------- | ---- | ----- | ------ |
| 101     | Aman | Delhi | Active |

**Important:**

- DEFAULT generally tab apply hota hai jab column omit kiya jaata hai ya DEFAULT keyword use hota hai.
- Explicit NULL dene par normally default automatically apply nahi hota.
- Exact behavior DBMS-specific ho sakta hai.

---

## 17. Domain Constraint

**Definition:**

Domain Constraint defines the valid set of values that an attribute can accept.

Simple words mein:

Kisi column mein kis type ki aur kis range ki values allowed hain, ye Domain Constraint define karta hai.

### Example

Student table:

| Column | Allowed Values                                      |
| ------ | --------------------------------------------------- |
| Age    | Integer                                             |
| Gender | Allowed business-defined values                     |
| Email  | Valid email format (usually application validation) |
| Marks  | 0 to 100                                            |

SQL Example:

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Age INT CHECK (Age BETWEEN 18 AND 60),
    Marks DECIMAL(5,2) CHECK (Marks BETWEEN 0 AND 100)
);
```

Yahan data type aur CHECK constraints milkar domain rules enforce karne mein help karte hain.

**Note:** SQL data types basic domain define karte hain. More complex validation ke liye CHECK, foreign keys ya application-level validation use ho sakti hai.

---

## 18. Entity Integrity Constraint

**Definition:**

Entity Integrity ensures that every row in a relational table can be uniquely identified.

Main rule:

Primary Key cannot contain NULL values.

Example:

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50)
);
```

Student_ID NULL nahi ho sakta.

Reason:

Agar Primary Key NULL ho, to row ki identity properly establish nahi ho payegi.

---

## 19. Referential Integrity Constraint

**Definition:**

Referential Integrity ensures that a Foreign Key value refers to a valid referenced key value, or is NULL if allowed.

Example:

Customers table:

| Customer_ID |
| ----------- |
| 1           |
| 2           |
| 3           |

Orders table:

| Order_ID | Customer_ID |
| -------- | ----------- |
| 101      | 1           |
| 102      | 2           |

Customer_ID = 5 insert nahi kar sakte, jab tak Customers table mein valid Customer_ID = 5 available na ho.

### Entity Integrity vs Referential Integrity

| Entity Integrity       | Referential Integrity                                  |
| ---------------------- | ------------------------------------------------------ |
| Primary Key se related | Foreign Key se related                                 |
| PK NULL nahi ho sakti  | FK valid referenced value honi chahiye ya allowed NULL |
| Row identification     | Table relationships ki consistency                     |

---

## 20. Key Constraint

**Definition:**

Key Constraint ensures that a key attribute or attribute combination uniquely identifies a record.

Example:

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Email VARCHAR(100) UNIQUE
);
```

Yahan:

- Student_ID uniquely identifies a row.
- Email bhi duplicate nahi ho sakta.

---

## 21. SQL Example – Multiple Constraints Together

Ab ek practical table banate hain jisme multiple constraints use hongi.

```sql
CREATE TABLE Departments (
    Department_ID INT PRIMARY KEY,
    Department_Name VARCHAR(50) NOT NULL UNIQUE
);
```

```sql
CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,

    Name VARCHAR(50) NOT NULL,

    Email VARCHAR(100) UNIQUE,

    Age INT CHECK (Age >= 18),

    Salary DECIMAL(10,2) DEFAULT 15000
        CHECK (Salary > 0),

    Department_ID INT,

    FOREIGN KEY (Department_ID)
    REFERENCES Departments(Department_ID)
);
```

### Constraints Used

| Constraint  | Applied On    | Purpose                    |
| ----------- | ------------- | -------------------------- |
| PRIMARY KEY | Employee_ID   | Unique row identification  |
| NOT NULL    | Name          | Name required              |
| UNIQUE      | Email         | Duplicate email prevent    |
| CHECK       | Age           | Age must be at least 18    |
| DEFAULT     | Salary        | Default salary value       |
| CHECK       | Salary        | Salary must be positive    |
| FOREIGN KEY | Department_ID | Valid department reference |

---

## 22. Relationships and Constraints – Combined Example

Suppose ek college database mein three tables hain:

1. Students
2. Courses
3. Enrollments

### Students

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE
);
```

### Courses

```sql
CREATE TABLE Courses (
    Course_ID INT PRIMARY KEY,
    Course_Name VARCHAR(50) NOT NULL
);
```

### Enrollments

```sql
CREATE TABLE Enrollments (
    Student_ID INT,
    Course_ID INT,
    Enroll_Date DATE DEFAULT CURRENT_DATE,

    PRIMARY KEY (Student_ID, Course_ID),

    FOREIGN KEY (Student_ID)
    REFERENCES Students(Student_ID),

    FOREIGN KEY (Course_ID)
    REFERENCES Courses(Course_ID)
);
```

### Relationship

```text
STUDENTS 1 -------- N ENROLLMENTS N -------- 1 COURSES
```

Original relationship:

```text
STUDENTS M -------- N COURSES
```

Junction table `Enrollments` M:N relationship ko two 1:N relationships mein convert karti hai.

**Dialect Note:** `CURRENT_DATE` is widely supported, but default-expression rules can vary between DBMS products and versions.

---

## 23. SQL NULL vs Zero vs Empty String

Ye concepts interview aur practical SQL dono mein important hain.

| Value | Meaning                              |
| ----- | ------------------------------------ |
| NULL  | Missing, unknown or not applicable   |
| 0     | Numeric zero                         |
| ''    | Empty string                         |
| '0'   | String containing the character zero |

Example:

```sql
SELECT *
FROM Students
WHERE Email IS NULL;
```

NULL check karne ke liye:

- `IS NULL`
- `IS NOT NULL`

Use karo.

Wrong:

```sql
SELECT *
FROM Students
WHERE Email = NULL;
```

Correct:

```sql
SELECT *
FROM Students
WHERE Email IS NULL;
```

---

## 24. Important SQL Operations Related to Constraints

### A. Add a UNIQUE Constraint

```sql
ALTER TABLE Students
ADD CONSTRAINT unique_email UNIQUE (Email);
```

### B. Add a CHECK Constraint

```sql
ALTER TABLE Students
ADD CONSTRAINT check_age CHECK (Age >= 18);
```

### C. Add a Foreign Key

```sql
ALTER TABLE Employees
ADD CONSTRAINT fk_department
FOREIGN KEY (Department_ID)
REFERENCES Departments(Department_ID);
```

### D. Drop a Constraint

Syntax DBMS-specific ho sakti hai.

Example in PostgreSQL:

```sql
ALTER TABLE Students
DROP CONSTRAINT unique_email;
```

Example in MySQL:

```sql
ALTER TABLE Students
DROP INDEX unique_email;
```

**Important:** Constraint create karne se pehle existing data valid hona chahiye. Invalid existing rows hone par ALTER TABLE fail ho sakta hai.

---

## 25. Relationship vs Constraint

| Relationship                         | Constraint                             |
| ------------------------------------ | -------------------------------------- |
| Tables/entities ke beech association | Data par applied rule                  |
| Connection represent karti hai       | Data validity enforce karti hai        |
| Example: Customer–Orders             | Example: NOT NULL                      |
| ER modeling mein important           | Database implementation mein important |

Relationship ko implement karne ke liye Foreign Key jaise constraints use kiye ja sakte hain.

---

## 26. Relationships in MongoDB and MERN

MERN Stack mein MongoDB use hota hai. MongoDB document-oriented database hai.

MongoDB mein relationships represent karne ke two common approaches hain:

1. Embedding
2. Referencing

### A. Embedding

Related data ko same document ke andar store karna.

Example:

```javascript
{
    _id: 101,
    name: "Aman",
    address: {
        city: "Meerut",
        state: "Uttar Pradesh"
    }
}
```

Yahan address same document mein embedded hai.

**Advantages:**

- Related data ek read mein mil sakta hai.
- Simple data models ke liye useful.
- Atomic updates to a single document possible hain.

**Disadvantages:**

- Repeated data duplication ho sakti hai.
- Document size grow kar sakta hai.
- Frequently changing shared data ke liye less suitable ho sakta hai.

### B. Referencing

Ek document mein doosre document ki ID store karna.

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

Yahan `userId` Users collection ke `_id` ko reference karta hai.

### Mongoose Reference

```javascript
const orderSchema = new mongoose.Schema({
  product: {
    type: String,
    required: true,
  },

  userId: {
    type: mongoose.Schema.Types.ObjectId,
    ref: "User",
    required: true,
  },
});
```

Populate:

```javascript
const orders = await Order.find().populate("userId");
```

`populate()` referenced document ki information retrieve karne mein help karta hai.

### MongoDB Important Difference

| SQL Database                                 | MongoDB                                              |
| -------------------------------------------- | ---------------------------------------------------- |
| Tables                                       | Collections                                          |
| Rows                                         | Documents                                            |
| Foreign Key constraints                      | Traditional automatic FK constraints nahi            |
| JOIN                                         | `$lookup` aggregation / application-level population |
| Embedding through related tables not typical | Embedded documents supported                         |
| Constraints database enforce kar sakta hai   | Validation aur application logic use ho sakti hai    |

**Important:** MongoDB references aur Mongoose `ref` automatically SQL-style referential integrity guarantee nahi karte. Application ko orphan references aur deletion behavior handle karna pad sakta hai.

---

## 27. Common Mistakes

1. One-to-Many aur Many-to-Many ko same samajhna.
2. Many-to-Many mein junction table ka use bhool jaana.
3. Foreign Key ko always unique samajhna.
4. Foreign Key ko automatically NOT NULL samajhna.
5. UNIQUE aur PRIMARY KEY ko exactly same samajhna.
6. NULL ko zero samajhna.
7. CHECK constraint ko complete application validation samajhna.
8. DEFAULT ko explicit NULL par automatically apply hona samajhna.
9. One-to-One relationship mein Foreign Key par UNIQUE lagana bhool jaana.
10. CASCADE ka effect samjhe bina use karna.
11. MongoDB `ref` ko SQL Foreign Key constraint samajhna.
12. Total Participation aur One-to-Many cardinality ko same concept samajhna.

---

## 28. Interview Questions and Answers

### Q1. What is a Relationship in DBMS?

A Relationship represents an association between two or more entities or tables.

### Q2. What are the three main types of relationships?

- One-to-One
- One-to-Many
- Many-to-Many

### Q3. What is a One-to-One relationship?

One record in one table is associated with at most one record in another table, and vice versa.

### Q4. What is a One-to-Many relationship?

One record in a parent table can be associated with multiple records in a child table.

### Q5. What is a Many-to-Many relationship?

Multiple records in one table can be associated with multiple records in another table.

### Q6. What is a Junction Table?

A Junction Table is used to implement a Many-to-Many relationship using Foreign Keys.

### Q7. What is a Self-Referencing Relationship?

A relationship in which a table's Foreign Key references its own Primary Key.

### Q8. What are Constraints in DBMS?

Constraints are rules applied to database columns or tables to maintain data accuracy and integrity.

### Q9. What is NOT NULL?

NOT NULL ensures that a column cannot contain NULL values.

### Q10. What is UNIQUE?

UNIQUE prevents duplicate values according to the DBMS's NULL handling rules.

### Q11. What is CHECK?

CHECK validates data against a specified condition.

### Q12. What is DEFAULT?

DEFAULT provides a predefined value when an insert operation omits a column or explicitly uses DEFAULT.

### Q13. What is Entity Integrity?

Entity Integrity ensures that a table's Primary Key is not NULL.

### Q14. What is Referential Integrity?

Referential Integrity ensures that Foreign Key values refer to valid referenced key values or allowed NULL values.

### Q15. What is the difference between Total and Partial Participation?

Total Participation is compulsory for every entity instance; Partial Participation is optional for some instances.

### Q16. Can a One-to-One relationship have NULL Foreign Key?

Yes, if the Foreign Key column allows NULL. This means participation may be optional.

### Q17. How do you implement Many-to-Many in SQL?

By creating a Junction Table containing Foreign Keys referencing both related tables.

### Q18. What is the difference between Embedding and Referencing in MongoDB?

Embedding stores related data in the same document, while Referencing stores another document's identifier.

---

## 29. Practical Tasks

### Task 1: Create a College Database

Create three tables:

- Students
- Courses
- Enrollments

Apply:

- Primary Key
- Foreign Key
- Composite Primary Key
- NOT NULL
- UNIQUE

### Task 2: Implement One-to-One

Create:

- Users
- User_Profiles

Ensure each profile belongs to at most one user and each user has at most one profile.

Hint: Use a UNIQUE Foreign Key.

### Task 3: Implement One-to-Many

Create:

- Departments
- Employees

One department can have multiple employees.

### Task 4: Implement Many-to-Many

Create:

- Students
- Courses
- Enrollments

Allow multiple students in multiple courses.

### Task 5: Implement CHECK and DEFAULT

Create an Employees table:

- Age must be at least 18.
- Salary must be greater than zero.
- Status default should be Active.
- Name cannot be NULL.

### Task 6: Practice Invalid Data

Try:

- Duplicate Primary Key.
- Duplicate UNIQUE value.
- Invalid Foreign Key.
- NULL in NOT NULL column.
- Age below allowed limit.
- Negative Salary.

Observe the errors returned by your DBMS.

### Task 7: Explain Without Notes

Explain:

1. 1:1 relationship.
2. 1:N relationship.
3. M:N relationship.
4. Junction Table.
5. Total Participation.
6. Partial Participation.
7. Referential Integrity.
8. CHECK constraint.

---

## 30. Quick Revision

### Relationships

| Type             | Meaning                              | Example          |
| ---------------- | ------------------------------------ | ---------------- |
| 1:1              | One record to at most one record     | Person–Passport  |
| 1:N              | One record to multiple records       | Customer–Orders  |
| M:N              | Multiple records to multiple records | Students–Courses |
| Self-Referencing | Table references itself              | Employee–Manager |

### Participation

| Type    | Meaning                  |
| ------- | ------------------------ |
| Total   | Participation compulsory |
| Partial | Participation optional   |

### Constraints

| Constraint  | Purpose                   |
| ----------- | ------------------------- |
| NOT NULL    | Prevent NULL              |
| UNIQUE      | Prevent duplicate values  |
| PRIMARY KEY | Unique row identification |
| FOREIGN KEY | Maintain valid references |
| CHECK       | Validate a condition      |
| DEFAULT     | Provide default value     |

### Integrity Rules

- Entity Integrity → Primary Key cannot be NULL.
- Referential Integrity → Foreign Key must refer to a valid key or be NULL if allowed.
- Domain Constraint → Column values must follow valid data rules.
- Key Constraint → Key must uniquely identify records.

### Important Points

- Many-to-Many is generally implemented using a Junction Table.
- One-to-Many mein Foreign Key usually Many side par hoti hai.
- One-to-One enforce karne ke liye Foreign Key par UNIQUE constraint useful hai.
- CHECK condition invalid values ko reject karne mein help karti hai.
- DEFAULT omitted values ke liye predefined value provide karta hai.
- MongoDB mein Embedding aur Referencing dono approaches available hain.

---

## 31. MCQ Quiz – Test Your Knowledge

**Q1. Which relationship allows one record to be associated with multiple records in another table?**

A. One-to-One  
B. One-to-Many  
C. Many-to-One only  
D. None

**Q2. Which relationship is generally implemented using a Junction Table?**

A. One-to-One  
B. One-to-Many  
C. Many-to-Many  
D. Self-Referencing

**Q3. Which constraint prevents NULL values?**

A. UNIQUE  
B. DEFAULT  
C. NOT NULL  
D. CHECK

**Q4. Which constraint validates a specified condition?**

A. CHECK  
B. PRIMARY KEY  
C. FOREIGN KEY  
D. DEFAULT

**Q5. Which constraint provides a predefined value when a column is omitted?**

A. UNIQUE  
B. DEFAULT  
C. CHECK  
D. FOREIGN KEY

**Q6. Which integrity rule ensures that Primary Key cannot be NULL?**

A. Referential Integrity  
B. Entity Integrity  
C. Domain Integrity  
D. Network Integrity

**Q7. Which relationship is used when a table references itself?**

A. One-to-One  
B. Many-to-Many  
C. Self-Referencing  
D. Partial

**Q8. What is Total Participation?**

A. Optional participation  
B. Every entity instance must participate  
C. Only one table participates  
D. Duplicate participation

**Q9. In a One-to-Many relationship, the Foreign Key is generally placed in:**

A. One side  
B. Many side  
C. Both sides always  
D. Neither side

**Q10. Which are the two common ways to represent related data in MongoDB?**

A. Paging and Segmentation  
B. Embedding and Referencing  
C. Primary and Alternate  
D. TCP and UDP

### Answer Key

1. B – One-to-Many
2. C – Many-to-Many
3. C – NOT NULL
4. A – CHECK
5. B – DEFAULT
6. B – Entity Integrity
7. C – Self-Referencing
8. B – Every entity instance must participate
9. B – Many side
10. B – Embedding and Referencing

---

**Topic 07 Completed – Relationships and Constraints in DBMS**

Next Topic: **08 – Relational Model in DBMS**

Ismein hum Relation, Tuple, Attribute, Domain, Schema, Instance, Degree, Cardinality, Relational Algebra aur relational database ke important concepts padhenge.
