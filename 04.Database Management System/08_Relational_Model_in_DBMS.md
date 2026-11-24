# 08. Relational Model in DBMS

## 1. Introduction to Relational Model

**Definition:**

The Relational Model is a database model in which data is organized and stored in the form of relations (tables) consisting of rows and columns.

Simple words mein:

Relational Model mein data tables ke form mein store hota hai. Har table mein rows aur columns hote hain.

Relational Model ko **E. F. Codd** ne 1970 mein introduce kiya tha.

### Example

Consider a Students table:

| Student_ID | Name  | Age | Course |
| ---------- | ----- | --- | ------ |
| 101        | Aman  | 22  | BCA    |
| 102        | Rahul | 21  | BCA    |
| 103        | Ravi  | 23  | BBA    |

Yahan:

- Table = Relation
- Row = Tuple
- Column = Attribute
- Column ke allowed values = Domain

### Relational Model Uses

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite

---

## 2. Basic Terminology of Relational Model

Relational Model mein kuch important terms use hoti hain:

1. Relation
2. Tuple
3. Attribute
4. Domain
5. Relation Schema
6. Relation Instance
7. Degree
8. Cardinality

Inhe ek-ek karke samajhte hain.

---

## 3. Relation

**Definition:**

A Relation is a table consisting of rows and columns in the Relational Model.

Simple words mein:

Relational Model mein table ko Relation kaha jaata hai.

### Example

**Students Relation**

| Student_ID | Name  | Age |
| ---------- | ----- | --- |
| 101        | Aman  | 22  |
| 102        | Rahul | 21  |
| 103        | Ravi  | 23  |

Yahan Students ek Relation hai.

### Properties of a Relation

1. Relation ka unique name hota hai.
2. Har column ka unique name hota hai.
3. Har cell mein ek atomic value hoti hai (basic relational model mein).
4. Same relation mein duplicate tuples allowed nahi hote.
5. Rows ka order logically important nahi hota.
6. Columns ka order bhi logically important nahi hota.
7. Har attribute ka ek defined domain hota hai.

**Important:** Practical SQL tables mein duplicate rows possible hain agar uniqueness enforce nahi ki gayi ho. Isliye theoretical Relation aur SQL Table ko exactly identical samajhna sahi nahi hai.

---

## 4. Tuple

**Definition:**

A Tuple is a single row or record in a Relation.

Simple words mein:

Table ki ek complete row ko Tuple kehte hain.

### Example

| Student_ID | Name  | Age |
| ---------- | ----- | --- |
| 101        | Aman  | 22  |
| 102        | Rahul | 21  |
| 103        | Ravi  | 23  |

First tuple:

```text
(101, Aman, 22)
```

Second tuple:

```text
(102, Rahul, 21)
```

Third tuple:

```text
(103, Ravi, 23)
```

### Important Points

- Tuple ek record represent karta hai.
- Ek relation mein multiple tuples hote hain.
- Tuple ko row bhi kaha jaata hai.
- Theoretical relation mein duplicate tuples nahi hote.

---

## 5. Attribute

**Definition:**

An Attribute is a named column of a Relation that represents a property of an entity.

Simple words mein:

Table ke har column ko Attribute kehte hain.

### Example

| Student_ID | Name | Age | Course |
| ---------- | ---- | --- | ------ |

Attributes:

- Student_ID
- Name
- Age
- Course

### Important Points

- Attribute table ki property represent karta hai.
- Har attribute ka unique name hota hai within a relation.
- Har attribute ka ek domain hota hai.
- Attribute ko column bhi kaha jaata hai.

---

## 6. Domain

**Definition:**

A Domain is the set of valid atomic values that an attribute can contain.

Simple words mein:

Kisi column mein kaunsi type aur range ki values allowed hain, us set ko Domain kehte hain.

### Example

Students table:

| Attribute  | Domain                       |
| ---------- | ---------------------------- |
| Student_ID | Positive integers            |
| Name       | Valid text values            |
| Age        | Integers in an allowed range |
| Marks      | Numeric values from 0 to 100 |

For example:

```text
Age Domain = {18, 19, 20, 21, 22, ...}
```

Agar Age column ka rule hai ki age 18 se 60 ke beech honi chahiye, to us range ke bahar values invalid hongi.

### SQL Example

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT CHECK (Age BETWEEN 18 AND 60),
    Marks DECIMAL(5,2) CHECK (Marks BETWEEN 0 AND 100)
);
```

Yahan:

- INT, VARCHAR aur DECIMAL data types define karte hain.
- CHECK constraints allowed values ko further restrict karte hain.

### Why Domain is Important?

1. Invalid data prevent karna.
2. Data consistency maintain karna.
3. Column ke valid values define karna.
4. Data quality improve karna.

---

## 7. Relation Schema

**Definition:**

A Relation Schema defines the structure of a relation, including its name, attributes and their domains.

Simple words mein:

Table ka design ya structure Relation Schema kehlata hai.

### Example

```text
STUDENTS(Student_ID, Name, Age, Course)
```

Yahan:

- STUDENTS = Relation Name
- Student_ID = Attribute
- Name = Attribute
- Age = Attribute
- Course = Attribute

Isse Relation Schema kehte hain.

### SQL Example

```sql
CREATE TABLE Students (
    Student_ID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT,
    Course VARCHAR(50)
);
```

Ye SQL statement Students table ka structure define karti hai.

### Important Points

- Schema database ka structure define karta hai.
- Schema relatively stable hota hai.
- Schema mein changes karne ke liye table structure modify karna padta hai.

---

## 8. Relation Instance

**Definition:**

A Relation Instance is the actual set of tuples stored in a relation at a particular point in time.

Simple words mein:

Table mein currently jo actual records/data present hain, wo Relation Instance hai.

### Example

Relation Schema:

```text
STUDENTS(Student_ID, Name, Age)
```

Relation Instance:

| Student_ID | Name  | Age |
| ---------- | ----- | --- |
| 101        | Aman  | 22  |
| 102        | Rahul | 21  |

Agar baad mein ek new student insert hota hai:

| Student_ID | Name  | Age |
| ---------- | ----- | --- |
| 101        | Aman  | 22  |
| 102        | Rahul | 21  |
| 103        | Ravi  | 23  |

To Relation Instance change ho gaya, lekin Schema same reh sakta hai.

### Schema vs Instance

| Schema                      | Instance                            |
| --------------------------- | ----------------------------------- |
| Database structure          | Actual stored data                  |
| Design define karta hai     | Current records represent karta hai |
| Relatively stable           | Frequently change ho sakta hai      |
| Example: Column definitions | Example: Rows in a table            |

**Remember:**

Schema = Structure

Instance = Data

---

## 9. Degree of a Relation

**Definition:**

The Degree of a Relation is the total number of attributes (columns) in that relation.

Simple words mein:

Table mein jitne columns hain, uski Degree utni hoti hai.

### Example

| Student_ID | Name | Age | Course |
| ---------- | ---- | --- | ------ |

Total columns = 4

Therefore:

```text
Degree = 4
```

### More Examples

| Table     | Columns | Degree |
| --------- | ------: | -----: |
| Students  |       4 |      4 |
| Employees |       5 |      5 |
| Courses   |       3 |      3 |
| Products  |       6 |      6 |

**Remember:** Degree = Number of Columns.

---

## 10. Cardinality of a Relation

**Definition:**

The Cardinality of a Relation is the total number of tuples (rows) in that relation.

Simple words mein:

Table mein jitni rows hain, uski Cardinality utni hoti hai.

### Example

| Student_ID | Name  |
| ---------- | ----- |
| 101        | Aman  |
| 102        | Rahul |
| 103        | Ravi  |

Total rows = 3

Therefore:

```text
Cardinality = 3
```

### Degree vs Cardinality

| Degree               | Cardinality               |
| -------------------- | ------------------------- |
| Number of columns    | Number of rows            |
| Attributes count     | Tuples count              |
| Structure se related | Actual records se related |
| Example: 4 columns   | Example: 3 rows           |

### Easy Trick

- Degree = Columns
- Cardinality = Rows

---

## 11. NULL Values in Relational Model

**Definition:**

NULL represents a missing, unknown or not applicable value in a database.

Simple words mein:

Jab kisi field ki value available nahi hoti ya applicable nahi hoti, to NULL use ho sakta hai.

### Example

| Student_ID | Name  | Phone      |
| ---------- | ----- | ---------- |
| 101        | Aman  | 9876543210 |
| 102        | Rahul | NULL       |
| 103        | Ravi  | 9123456780 |

Rahul ka Phone number available nahi hai.

Isliye NULL store kiya gaya hai.

### NULL vs Zero vs Empty String

| Value | Meaning                  |
| ----- | ------------------------ |
| NULL  | Missing or unknown value |
| 0     | Numeric zero             |
| ''    | Empty string             |
| '0'   | Text containing zero     |

### SQL Example

```sql
SELECT *
FROM Students
WHERE Phone IS NULL;
```

NULL check karne ke liye `IS NULL` aur `IS NOT NULL` use karte hain.

**Important:**

- NULL zero nahi hota.
- NULL empty string nahi hota.
- NULL ke saath normal equality comparison use nahi karna chahiye.
- SQL mein NULL comparisons generally UNKNOWN result de sakte hain.

---

## 12. Properties of Relational Model

Relational Model ki important properties:

### 1. Atomic Values

Basic relational model mein har cell mein ek atomic value hoti hai.

Example:

Correct:

| Student_ID | Phone      |
| ---------- | ---------- |
| 101        | 9876543210 |

Poor design:

| Student_ID | Phone                  |
| ---------- | ---------------------- |
| 101        | 9876543210, 9123456780 |

Second example mein multiple phone numbers ek hi cell mein store hain. Ye First Normal Form ke against ho sakta hai.

### 2. Unique Attribute Names

Ek relation ke andar attributes ke names unique hone chahiye.

### 3. Unique Tuples

Theoretical relation mein duplicate tuples allowed nahi hote.

### 4. Same Domain

Ek attribute ki values uske defined domain se belong karni chahiye.

### 5. Order of Rows is Not Important

Relational Model mein rows ka fixed order nahi hota.

Agar order chahiye to SQL mein `ORDER BY` use karte hain.

```sql
SELECT *
FROM Students
ORDER BY Student_ID;
```

### 6. Order of Columns is Not Important

Logical level par attributes ka order relation ko define nahi karta.

---

# PART 2: RELATIONAL MODEL STRUCTURE

## 13. Relational Database

**Definition:**

A Relational Database is a collection of related tables that store data in a structured form and can be connected through keys.

### Example

College Database:

```text
COLLEGE DATABASE
       |
       |---- STUDENTS
       |
       |---- COURSES
       |
       |---- TEACHERS
       |
       |---- ENROLLMENTS
```

Tables ke beech relationships Foreign Keys ke through establish ki ja sakti hain.

### Example Structure

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

---

## 14. Relational Model vs Relational Database vs RDBMS

| Term                | Meaning                                    |
| ------------------- | ------------------------------------------ |
| Relational Model    | Data organize karne ka theoretical model   |
| Relational Database | Relational structure mein stored database  |
| RDBMS               | Software that manages relational databases |

Examples of RDBMS:

- MySQL
- PostgreSQL
- Oracle
- SQL Server
- SQLite

---

## 15. What is Relational Algebra?

**Definition:**

Relational Algebra is a procedural query language used to perform operations on relations (tables) and retrieve required data.

Simple words mein:

Relational Algebra ek mathematical language hai jiske through tables par operations perform kiye jaate hain.

Ismein input ek ya multiple relations hote hain aur output bhi ek relation hota hai.

### Main Operations of Relational Algebra

1. Selection (σ)
2. Projection (π)
3. Union (∪)
4. Set Difference (−)
5. Cartesian Product (×)
6. Rename (ρ)
7. Intersection (∩)
8. Join (⋈)
9. Division (÷)

---

## 16. Selection Operation (σ)

**Definition:**

Selection is used to select rows (tuples) from a relation that satisfy a given condition.

Simple words mein:

Selection ka use specific condition ke according rows select karne ke liye hota hai.

### Symbol

```text
σ
```

### Example

Students table:

| Student_ID | Name  | Age |
| ---------- | ----- | --- |
| 101        | Aman  | 22  |
| 102        | Rahul | 21  |
| 103        | Ravi  | 23  |

Age greater than 21 wale students:

```text
σ Age > 21 (Students)
```

Output:

| Student_ID | Name | Age |
| ---------- | ---- | --- |
| 101        | Aman | 22  |
| 103        | Ravi | 23  |

### SQL Equivalent

```sql
SELECT *
FROM Students
WHERE Age > 21;
```

**Remember:** Selection = Rows.

---

## 17. Projection Operation (π)

**Definition:**

Projection is used to select specific columns (attributes) from a relation.

Simple words mein:

Projection ka use table ke required columns select karne ke liye hota hai.

### Symbol

```text
π
```

### Example

Students table:

| Student_ID | Name  | Age |
| ---------- | ----- | --- |
| 101        | Aman  | 22  |
| 102        | Rahul | 21  |
| 103        | Ravi  | 23  |

Only Name column:

```text
π Name (Students)
```

Output:

| Name  |
| ----- |
| Aman  |
| Rahul |
| Ravi  |

### SQL Equivalent

```sql
SELECT Name
FROM Students;
```

**Important:** Classical relational algebra mein Projection duplicate tuples ko remove karta hai. SQL mein `SELECT` by default duplicates preserve karta hai. SQL mein duplicate remove karne ke liye `DISTINCT` use karte hain.

```sql
SELECT DISTINCT Name
FROM Students;
```

**Remember:** Projection = Columns.

---

## 18. Union Operation (∪)

**Definition:**

Union combines tuples from two compatible relations and returns tuples present in either relation.

Simple words mein:

Union ka use do compatible tables ke records ko combine karne ke liye hota hai.

### Symbol

```text
∪
```

### Example

Table A:

| Student_ID |
| ---------- |
| 101        |
| 102        |

Table B:

| Student_ID |
| ---------- |
| 102        |
| 103        |

Union:

```text
A ∪ B
```

Output:

| Student_ID |
| ---------- |
| 101        |
| 102        |
| 103        |

Duplicate 102 remove ho gaya.

### SQL Equivalent

```sql
SELECT Student_ID FROM Table_A

UNION

SELECT Student_ID FROM Table_B;
```

### Union Compatibility

Union perform karne ke liye:

- Dono relations mein same number of attributes hone chahiye.
- Corresponding attributes compatible domains/types ke hone chahiye.

---

## 19. Set Difference Operation (−)

**Definition:**

Set Difference returns tuples that exist in the first relation but not in the second relation.

Simple words mein:

A − B ka matlab hai A mein jo records hain, lekin B mein nahi hain.

### Example

Table A:

| Student_ID |
| ---------- |
| 101        |
| 102        |
| 103        |

Table B:

| Student_ID |
| ---------- |
| 102        |
| 103        |

Difference:

```text
A − B
```

Output:

| Student_ID |
| ---------- |
| 101        |

### SQL Equivalent

PostgreSQL example:

```sql
SELECT Student_ID FROM Table_A

EXCEPT

SELECT Student_ID FROM Table_B;
```

**Note:** Set Difference ki SQL syntax DBMS ke according vary karti hai. Oracle commonly `MINUS` use karta hai.

---

## 20. Cartesian Product (×)

**Definition:**

Cartesian Product combines every tuple of the first relation with every tuple of the second relation.

Simple words mein:

Table A ki har row ko Table B ki har row ke saath combine karta hai.

### Example

Table A:

| A_ID |
| ---- |
| 1    |
| 2    |

Table B:

| B_Name |
| ------ |
| Aman   |
| Rahul  |

Cartesian Product:

```text
A × B
```

Output:

| A_ID | B_Name |
| ---- | ------ |
| 1    | Aman   |
| 1    | Rahul  |
| 2    | Aman   |
| 2    | Rahul  |

Total rows:

```text
2 × 2 = 4
```

### SQL Equivalent

```sql
SELECT *
FROM Table_A
CROSS JOIN Table_B;
```

### Formula

If:

- Table A has m rows.
- Table B has n rows.

Then:

```text
Total Rows = m × n
```

---

## 21. Rename Operation (ρ)

**Definition:**

Rename operation is used to rename a relation or its attributes.

Simple words mein:

Relation ya column ka temporary name change karne ke liye Rename operation use hota hai.

### Symbol

```text
ρ
```

### Example

```text
ρ Student_Info (Students)
```

Iska meaning Students relation ko temporarily Student_Info naam dena hai.

### SQL Equivalent

```sql
SELECT
    Student_ID AS ID,
    Name AS Student_Name
FROM Students;
```

Table alias:

```sql
SELECT *
FROM Students AS S;
```

---

## 22. Intersection Operation (∩)

**Definition:**

Intersection returns only those tuples that are common to both relations.

Simple words mein:

Do tables mein jo common records hain, unhe return karta hai.

### Symbol

```text
∩
```

### Example

Table A:

| Student_ID |
| ---------- |
| 101        |
| 102        |
| 103        |

Table B:

| Student_ID |
| ---------- |
| 102        |
| 103        |
| 104        |

Intersection:

```text
A ∩ B
```

Output:

| Student_ID |
| ---------- |
| 102        |
| 103        |

### SQL Equivalent

```sql
SELECT Student_ID FROM Table_A

INTERSECT

SELECT Student_ID FROM Table_B;
```

**Note:** INTERSECT support aur syntax DBMS/version par depend kar sakti hai.

---

## 23. Join Operation (⋈)

**Definition:**

Join combines related tuples from two or more relations based on a matching condition.

Simple words mein:

Jab humein multiple tables ka related data ek saath chahiye, tab Join use karte hain.

### Example

Students table:

| Student_ID | Name  |
| ---------- | ----- |
| 101        | Aman  |
| 102        | Rahul |

Courses table:

| Course_ID | Student_ID | Course |
| --------- | ---------- | ------ |
| C01       | 101        | MERN   |
| C02       | 102        | DSA    |

Join:

```text
Students ⋈ Students.Student_ID = Courses.Student_ID Courses
```

Output:

| Student_ID | Name  | Course |
| ---------- | ----- | ------ |
| 101        | Aman  | MERN   |
| 102        | Rahul | DSA    |

### SQL Equivalent

```sql
SELECT
    Students.Name,
    Courses.Course
FROM Students
INNER JOIN Courses
ON Students.Student_ID = Courses.Student_ID;
```

### Common Join Types

- Inner Join
- Left Join
- Right Join
- Full Outer Join
- Cross Join
- Self Join

In joins ko hum DBMS ke Topic 12 mein detail mein padhenge.

---

## 24. Division Operation (÷)

**Definition:**

Division is used to find records in one relation that are associated with all values in another relation.

Simple words mein:

Jab humein aise records find karne ho jo doosri table ke sabhi required records ke saath related hon, tab Division use hota hai.

### Example

Student_Courses:

| Student_ID | Course_ID |
| ---------- | --------- |
| 101        | C01       |
| 101        | C02       |
| 102        | C01       |
| 103        | C01       |
| 103        | C02       |

Required_Courses:

| Course_ID |
| --------- |
| C01       |
| C02       |

Question:

Kaunse students ne dono required courses complete kiye hain?

Result:

| Student_ID |
| ---------- |
| 101        |
| 103        |

Because students 101 and 103 have both C01 and C02.

**Remember:** Division is useful for "all" type queries.

---

## 25. Relational Algebra Operations – Quick Table

| Operation         | Symbol | Purpose                                     |
| ----------------- | ------ | ------------------------------------------- |
| Selection         | σ      | Select rows                                 |
| Projection        | π      | Select columns                              |
| Union             | ∪      | Combine compatible relations                |
| Difference        | −      | Records in first but not second             |
| Cartesian Product | ×      | Every row combination                       |
| Rename            | ρ      | Rename relation/attributes                  |
| Intersection      | ∩      | Common records                              |
| Join              | ⋈      | Combine related records                     |
| Division          | ÷      | Find records related to all required values |

---

## 26. Relational Algebra vs Relational Calculus

Both are formal query languages used in relational database theory.

| Relational Algebra                | Relational Calculus                |
| --------------------------------- | ---------------------------------- |
| Procedural                        | Non-procedural / Declarative       |
| Specifies operations to perform   | Specifies what result is required  |
| Based on algebraic operations     | Based on predicate logic           |
| Example: Selection and Projection | Example: Tuple Relational Calculus |

### Types of Relational Calculus

1. Tuple Relational Calculus (TRC)
2. Domain Relational Calculus (DRC)

### Simple Example

Relational Algebra:

```text
σ Age > 21 (Students)
```

Meaning: Select students whose age is greater than 21.

Relational Calculus concept:

Find all student records where Age > 21.

**Important:** SQL is declarative in style, although DBMS internally query ko execute karne ke liye execution plan generate karta hai.

---

## 27. Advantages of Relational Model

1. Simple tabular structure.
2. Data ko easily understand kar sakte hain.
3. Tables ke beech relationships establish kar sakte hain.
4. SQL ke through data retrieve aur manipulate karna easy hai.
5. Keys aur constraints se integrity maintain hoti hai.
6. Normalization ke through redundancy reduce kar sakte hain.
7. Data independence support karta hai.
8. Mature tools aur standards available hain.

---

## 28. Disadvantages of Relational Model

1. Complex relationships mein multiple joins ki need ho sakti hai.
2. Highly connected data ke liye graph databases more suitable ho sakte hain.
3. Flexible/unstructured data ke liye document databases convenient ho sakte hain.
4. Large-scale distributed workloads mein relational architecture ko carefully design karna padta hai.
5. Schema changes kabhi-kabhi complex ho sakte hain.
6. Poor indexing aur query design se performance slow ho sakti hai.

---

## 29. Relational Model in MERN Stack

MERN Stack mein MongoDB relational database nahi hai. Ye document-oriented NoSQL database hai.

Lekin relational concepts samajhna MongoDB relationships aur data modeling samajhne mein help karta hai.

### SQL Example

```text
USERS
User_ID | Name

ORDERS
Order_ID | User_ID | Product
```

Yahan `User_ID` Foreign Key hai.

### MongoDB Example

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
    userId: ObjectId("..."),
    product: "Laptop"
}
```

Yahan:

- `_id` document identifier hai.
- `userId` ek reference store karta hai.
- MongoDB traditional SQL Foreign Key constraint automatically enforce nahi karta.

### MERN Developer ke Liye Important

Relational Model samajhne se:

- SQL databases samajhne mein help milegi.
- MongoDB mein embedding vs referencing decisions better honge.
- Database schema design improve hoga.
- Joins, relationships aur data integrity clear honge.

---

## 30. Common Mistakes

1. Relation aur Relationship ko same samajhna.
   - Relation = Table.
   - Relationship = Tables/entities ke beech association.

2. Tuple aur Attribute ko confuse karna.
   - Tuple = Row.
   - Attribute = Column.

3. Degree aur Cardinality ko confuse karna.
   - Degree = Columns.
   - Cardinality = Rows.

4. Schema aur Instance ko same samajhna.
   - Schema = Structure.
   - Instance = Actual data.

5. Selection aur Projection ko confuse karna.
   - Selection = Rows.
   - Projection = Columns.

6. Theoretical Relation ko SQL Table ke exactly equal samajhna.
   - SQL tables duplicate rows allow kar sakti hain unless constrained.

7. NULL ko zero samajhna.
   - NULL means missing/unknown/not applicable.

8. Union compatibility ignore karna.
   - Same number of compatible attributes required.

9. Cartesian Product ka result size ignore karna.
   - m × n rows generate hote hain.

10. Relational Algebra ko SQL ke exactly same samajhna.
    - Relational Algebra formal mathematical model hai; SQL practical query language hai.

---

## 31. Interview Questions and Answers

### Q1. What is the Relational Model?

The Relational Model organizes data into relations (tables) containing rows and columns.

### Q2. Who introduced the Relational Model?

E. F. Codd introduced the Relational Model in 1970.

### Q3. What is a Relation?

A Relation is a table in the Relational Model.

### Q4. What is a Tuple?

A Tuple is a single row or record in a relation.

### Q5. What is an Attribute?

An Attribute is a column or property of a relation.

### Q6. What is a Domain?

A Domain is the set of valid atomic values allowed for an attribute.

### Q7. What is Relation Schema?

Relation Schema defines the structure of a relation, including its attributes.

### Q8. What is Relation Instance?

Relation Instance represents the actual set of tuples stored at a particular time.

### Q9. What is Degree?

Degree is the number of attributes (columns) in a relation.

### Q10. What is Cardinality?

Cardinality is the number of tuples (rows) in a relation.

### Q11. What is Relational Algebra?

Relational Algebra is a procedural mathematical query language used to perform operations on relations.

### Q12. What is Selection?

Selection retrieves rows that satisfy a specified condition.

### Q13. What is Projection?

Projection retrieves selected columns from a relation.

### Q14. What is Cartesian Product?

Cartesian Product combines every row of one relation with every row of another relation.

### Q15. What is Union Compatibility?

Two relations are union-compatible when they have the same number of corresponding attributes with compatible domains.

### Q16. What is the difference between Relational Algebra and Relational Calculus?

Relational Algebra specifies how to obtain the result, while Relational Calculus specifies what result is required.

### Q17. What is the difference between Schema and Instance?

Schema defines the structure, while Instance contains the actual data at a particular time.

### Q18. Is SQL a Relational Algebra language?

SQL is a declarative query language based on relational concepts. It is not simply identical to classical Relational Algebra.

---

## 32. Practical Tasks

### Task 1: Create a Students Table

Create a table with:

- Student_ID
- Name
- Age
- Course
- Email

Insert at least five records.

### Task 2: Identify Terminology

For your Students table, identify:

- Relation
- Tuple
- Attribute
- Domain
- Schema
- Instance
- Degree
- Cardinality

### Task 3: Practice Selection

Find students whose age is greater than 21.

Relational Algebra:

```text
σ Age > 21 (Students)
```

SQL:

```sql
SELECT *
FROM Students
WHERE Age > 21;
```

### Task 4: Practice Projection

Display only Name and Course.

```sql
SELECT Name, Course
FROM Students;
```

### Task 5: Practice Union

Create two tables containing Student_ID values and practice UNION.

### Task 6: Practice Cartesian Product

Create two small tables and perform CROSS JOIN.

Observe the total number of rows.

### Task 7: Practice Joins

Create Students and Courses tables and connect them using a common key.

### Task 8: Explain Without Notes

Explain:

1. Relation vs Relationship.
2. Tuple vs Attribute.
3. Degree vs Cardinality.
4. Schema vs Instance.
5. Selection vs Projection.
6. Relational Algebra vs Relational Calculus.

---

## 33. Quick Revision

| Term              | Meaning                      |
| ----------------- | ---------------------------- |
| Relation          | Table                        |
| Tuple             | Row                          |
| Attribute         | Column                       |
| Domain            | Valid set of values          |
| Schema            | Table structure              |
| Instance          | Actual stored data           |
| Degree            | Number of columns            |
| Cardinality       | Number of rows               |
| Selection         | Select rows                  |
| Projection        | Select columns               |
| Union             | Combine compatible relations |
| Difference        | First relation minus second  |
| Cartesian Product | All row combinations         |
| Rename            | Rename relation/attributes   |
| Intersection      | Common tuples                |
| Join              | Combine related tuples       |
| Division          | Match all required values    |

### Important Symbols

```text
σ  = Selection
π  = Projection
∪  = Union
−  = Difference
×  = Cartesian Product
ρ  = Rename
∩  = Intersection
⋈  = Join
÷  = Division
```

### Remember

- Relation = Table.
- Tuple = Row.
- Attribute = Column.
- Degree = Columns.
- Cardinality = Rows.
- Schema = Structure.
- Instance = Data.
- Selection = Rows.
- Projection = Columns.
- E. F. Codd introduced the Relational Model in 1970.

---

## 34. MCQ Quiz – Test Your Knowledge

**Q1. Who introduced the Relational Model?**

A. Charles Babbage  
B. E. F. Codd  
C. Dennis Ritchie  
D. James Gosling

**Q2. A row in a Relation is called:**

A. Attribute  
B. Domain  
C. Tuple  
D. Schema

**Q3. A column in a Relation is called:**

A. Tuple  
B. Attribute  
C. Cardinality  
D. Instance

**Q4. Degree of a Relation represents:**

A. Number of rows  
B. Number of columns  
C. Number of tables  
D. Number of databases

**Q5. Cardinality of a Relation represents:**

A. Number of columns  
B. Number of attributes  
C. Number of rows  
D. Number of constraints

**Q6. Which operation selects rows?**

A. Projection  
B. Selection  
C. Union  
D. Rename

**Q7. Which operation selects columns?**

A. Projection  
B. Selection  
C. Difference  
D. Division

**Q8. Which symbol represents Union?**

A. σ  
B. π  
C. ∪  
D. ×

**Q9. Which operation creates every possible combination of rows from two relations?**

A. Intersection  
B. Cartesian Product  
C. Difference  
D. Projection

**Q10. Schema represents:**

A. Actual records  
B. Database structure  
C. Number of rows  
D. Query output only

### Answer Key

1. B – E. F. Codd
2. C – Tuple
3. B – Attribute
4. B – Number of columns
5. C – Number of rows
6. B – Selection
7. A – Projection
8. C – Union
9. B – Cartesian Product
10. B – Database structure

---

**Topic 08 Completed – Relational Model in DBMS**

Next Topic: **09 – Introduction to SQL (Structured Query Language)**

Ismein hum SQL kya hai, SQL kaise work karti hai, SQL commands ka basic structure, database create/use karna, tables aur basic SELECT queries seekhenge.
