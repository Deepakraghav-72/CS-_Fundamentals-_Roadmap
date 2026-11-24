# 18. Views and Stored Procedures in DBMS

## 1. What is a View?

**View** SQL database mein ek virtual table hoti hai jo ek SQL query ke result par based hoti hai.

View generally actual data ko separately store nahi karti; ye underlying table se data show karti hai.

Example: `Students` table:

| id  | name  | age | city  |
| --- | ----- | --- | ----- |
| 1   | Rahul | 22  | Delhi |
| 2   | Aman  | 24  | Noida |
| 3   | Ravi  | 21  | Delhi |

Hume sirf Delhi ke students show karne hain.

```sql
CREATE VIEW Delhi_Students AS
SELECT id, name, age
FROM Students
WHERE city = 'Delhi';
```

View ko access karna:

```sql
SELECT * FROM Delhi_Students;
```

Output:

| id  | name  | age |
| --- | ----- | --- |
| 1   | Rahul | 22  |
| 3   | Ravi  | 21  |

**Important:** View ek saved query ki tarah hoti hai. Normal view ka result usually query execute hone par underlying tables se retrieve hota hai.

## 2. Why Do We Use Views?

Views ke main benefits:

1. **Security:** Users ko sirf required columns ya rows dikhana.
2. **Simplicity:** Complex queries ko simple name se access karna.
3. **Reusability:** Same query baar-baar likhne ki zarurat kam.
4. **Abstraction:** Users ko underlying table structure ki details se bachana.
5. **Consistency:** Common query logic ko reuse karna.

Example:

```sql
CREATE VIEW Public_Users AS
SELECT id, name
FROM Users;
```

Is view mein password ya sensitive columns expose nahi hote.

Note: View khud complete security solution nahi hai. Proper permissions aur access controls bhi zaroori hain.

## 3. Types of Views

### A. Simple View

Usually ek table par based view, jisme simple columns aur expressions hote hain.

```sql
CREATE VIEW Student_View AS
SELECT id, name
FROM Students;
```

### B. Complex View

Multiple tables, joins, aggregate functions ya grouping par based view.

```sql
CREATE VIEW Student_Courses AS
SELECT
    s.name,
    c.course_name
FROM Students s
JOIN Courses c
ON s.id = c.student_id;
```

### C. Materialized View

Materialized view query ka result physically store karti hai.

- Read performance improve ho sakti hai.
- Stored result ko refresh karna pad sakta hai.
- Data underlying tables se temporarily out-of-date ho sakta hai.

Example syntax (PostgreSQL):

```sql
CREATE MATERIALIZED VIEW Student_Count AS
SELECT COUNT(*) AS total_students
FROM Students;
```

Refresh:

```sql
REFRESH MATERIALIZED VIEW Student_Count;
```

**Difference:**

| Normal View                                      | Materialized View                         |
| ------------------------------------------------ | ----------------------------------------- |
| Query definition store hoti hai                  | Query result physically store hota hai    |
| Generally latest underlying data query karti hai | Refresh ki zarurat ho sakti hai           |
| Extra result storage usually nahi                | Extra storage required                    |
| Read performance query par depend                | Repeated complex reads fast ho sakte hain |

Materialized views ka support aur refresh behavior DBMS-specific hota hai.

## 4. Creating, Updating and Deleting Views

### Create View

```sql
CREATE VIEW Active_Students AS
SELECT id, name
FROM Students
WHERE status = 'active';
```

### Replace View

Kuch DBMS `CREATE OR REPLACE VIEW` support karte hain:

```sql
CREATE OR REPLACE VIEW Active_Students AS
SELECT id, name, email
FROM Students
WHERE status = 'active';
```

Syntax DBMS ke according vary kar sakti hai.

### Drop View

```sql
DROP VIEW Active_Students;
```

Isse view definition delete hoti hai; underlying table ka data normally delete nahi hota.

## 5. Can We Update Data Through a View?

Kuch simple views ke through INSERT, UPDATE aur DELETE possible hote hain.

Example:

```sql
CREATE VIEW Student_Basic AS
SELECT id, name
FROM Students;
```

Update:

```sql
UPDATE Student_Basic
SET name = 'Aman'
WHERE id = 1;
```

Agar DBMS aur view definition allow kare, to underlying `Students` table update ho sakti hai.

**Views generally non-updatable ho sakti hain agar unmein:**

- Aggregate functions hon.
- GROUP BY ho.
- DISTINCT ho.
- UNION ho.
- Complex joins ya calculated columns hon.

Exact rules DBMS-specific hain.

## 6. What is a Stored Procedure?

**Stored Procedure** SQL statements ka ek named group hota hai jo database server par store hota hai aur zarurat padne par execute kiya ja sakta hai.

Example use cases:

- User registration logic.
- Salary calculation.
- Reports generate karna.
- Multiple database operations perform karna.
- Repeated database tasks automate karna.

Stored procedures ka syntax DBMS ke according different hota hai.

### Example – MySQL Stored Procedure

```sql
DELIMITER //

CREATE PROCEDURE GetStudents()
BEGIN
    SELECT * FROM Students;
END //

DELIMITER ;
```

Execute:

```sql
CALL GetStudents();
```

Yahan:

- `CREATE PROCEDURE` procedure create karta hai.
- `BEGIN` procedure body start karta hai.
- `END` procedure body finish karta hai.
- `CALL` procedure execute karta hai.
- `DELIMITER` MySQL client mein statement delimiter temporarily change karta hai.

## 7. Stored Procedure with Parameters

Parameters ki help se procedure ko input diya ja sakta hai.

### IN Parameter

Input value receive karta hai.

```sql
DELIMITER //

CREATE PROCEDURE GetStudentById(IN studentId INT)
BEGIN
    SELECT *
    FROM Students
    WHERE id = studentId;
END //

DELIMITER ;
```

Execute:

```sql
CALL GetStudentById(101);
```

### OUT Parameter

Procedure output value return karne ke liye OUT parameter use kar sakta hai.

```sql
DELIMITER //

CREATE PROCEDURE CountStudents(OUT total INT)
BEGIN
    SELECT COUNT(*)
    INTO total
    FROM Students;
END //

DELIMITER ;
```

Execute:

```sql
CALL CountStudents(@student_total);

SELECT @student_total;
```

### INOUT Parameter

INOUT parameter input bhi receive kar sakta hai aur updated output bhi return kar sakta hai.

Example:

```sql
DELIMITER //

CREATE PROCEDURE IncreaseValue(INOUT num INT)
BEGIN
    SET num = num + 10;
END //

DELIMITER ;
```

Execute:

```sql
SET @value = 20;

CALL IncreaseValue(@value);

SELECT @value;
```

Output:

```text
30
```

| Parameter | Purpose                                    |
| --------- | ------------------------------------------ |
| IN        | Input receive karta hai                    |
| OUT       | Output provide karta hai                   |
| INOUT     | Input receive aur output provide karta hai |

## 8. What is a Function in DBMS?

**Function** database ka reusable routine hota hai jo generally ek value return karta hai.

Example (MySQL):

```sql
DELIMITER //

CREATE FUNCTION SquareNumber(num INT)
RETURNS INT
DETERMINISTIC
BEGIN
    RETURN num * num;
END //

DELIMITER ;
```

Use:

```sql
SELECT SquareNumber(5);
```

Output:

```text
25
```

Functions ko SQL expressions ke andar use kiya ja sakta hai, subject to DBMS rules.

## 9. Stored Procedure vs Function

| Stored Procedure                                                  | Function                                             |
| ----------------------------------------------------------------- | ---------------------------------------------------- |
| Procedure execute karne ke liye CALL jaisa statement use hota hai | Function expression mein use ho sakta hai            |
| Parameters IN, OUT, INOUT ho sakte hain                           | Function generally value return karta hai            |
| Multiple result sets possible in some DBMS                        | Usually a defined return value                       |
| Database operations ke liye useful                                | Calculations aur reusable expressions ke liye useful |
| SELECT ke andar directly call karna generally allowed nahi        | SELECT mein use ho sakta hai, subject to rules       |

**Note:** Procedure aur function ke exact capabilities SQL dialect ke according differ karte hain.

## 10. Stored Procedure vs Normal SQL Query

| Normal SQL Query                              | Stored Procedure                        |
| --------------------------------------------- | --------------------------------------- |
| Direct SQL statement execute hota hai         | Stored routine execute hoti hai         |
| Repeated logic baar-baar likhna pad sakta hai | Logic database mein reusable hota hai   |
| Single statement bhi ho sakta hai             | Multiple statements ho sakte hain       |
| Query application se send ki ja sakti hai     | Procedure database mein stored hoti hai |

## 11. Advantages of Stored Procedures

1. Code reusability.
2. Repeated database logic ko centralize karna.
3. Network round trips reduce ho sakte hain.
4. Database permissions ke through controlled access.
5. Multi-step operations ko organize karna.
6. Maintenance easy ho sakti hai jab common logic ek jagah rakha ho.

## 12. Disadvantages of Stored Procedures

1. DBMS-specific syntax se portability difficult ho sakti hai.
2. Complex procedures maintain karna difficult.
3. Business logic database aur application mein split ho sakti hai.
4. Debugging aur version control workflow complicated ho sakta hai.
5. Poorly written procedure performance problems create kar sakti hai.

Stored procedures automatically faster nahi hoti; performance query design, execution plan aur database configuration par depend karti hai.

## 13. Stored Procedures in MERN Stack

MERN stack mein MongoDB use hota hai, SQL database nahi.

MongoDB relational databases jaise SQL stored procedures provide nahi karta.

MERN applications mein business logic generally:

- Node.js
- Express.js
- Service layer
- Mongoose models

mein implement ki jaati hai.

Example:

```javascript
async function getStudentById(id) {
  const student = await Student.findById(id);
  return student;
}
```

Ye JavaScript function hai, database stored procedure nahi.

**Remember:**

- SQL Stored Procedure = Database server par stored routine.
- JavaScript Function = Application code mein reusable function.

## 14. Views vs Stored Procedures

| Views                                       | Stored Procedures                             |
| ------------------------------------------- | --------------------------------------------- |
| Virtual table/query result                  | Stored executable routine                     |
| Mainly data present karne ke liye           | Operations aur business logic ke liye         |
| SELECT se access                            | CALL/EXEC type statement se execute           |
| Parameters generally normal views mein nahi | Parameters support ho sakte hain              |
| Underlying data show karti hai              | Multiple SQL operations perform kar sakti hai |

## 15. Common Mistakes

1. View ko actual physical table samajhna.
2. Normal view aur materialized view ko same samajhna.
3. Har view ko automatically updatable samajhna.
4. Stored procedure ko JavaScript function samajhna.
5. IN, OUT aur INOUT parameters confuse karna.
6. Har DBMS mein same stored procedure syntax expect karna.
7. Stored procedure ko automatically faster samajhna.
8. View ko complete security mechanism samajhna.

## 16. Interview Questions and Answers

**Q1. What is a View in DBMS?**

View ek virtual table hoti hai jo SQL query ke result par based hoti hai.

**Q2. Why do we use Views?**

Data abstraction, security, simplicity aur query reusability ke liye.

**Q3. What is a Materialized View?**

Aisi view jiska query result physically store hota hai aur refresh karna pad sakta hai.

**Q4. What is a Stored Procedure?**

Database server par stored SQL statements ka named group jo execute kiya ja sakta hai.

**Q5. How do you execute a stored procedure in MySQL?**

`CALL procedure_name();`

**Q6. What are IN, OUT and INOUT parameters?**

IN input, OUT output aur INOUT input-output dono ke liye use hota hai.

**Q7. What is a Function in DBMS?**

Reusable database routine jo generally ek value return karti hai.

**Q8. Difference between View and Stored Procedure?**

View query result ko virtual table ke form mein present karti hai, jabki stored procedure executable SQL logic hoti hai.

**Q9. Can we update a View?**

Kuch simple views updatable hoti hain. Complex views generally restricted hoti hain.

**Q10. Does MongoDB support SQL Stored Procedures?**

MongoDB SQL stored procedures provide nahi karta. Application logic generally Node.js/Express mein likhi jaati hai.

## 17. Practical Tasks

1. Students table se `Student_View` create karo.
2. View mein sirf `id` aur `name` show karo.
3. Active students ke liye separate view banao.
4. Ek simple stored procedure create karo jo all students return kare.
5. IN parameter se student ID search karo.
6. OUT parameter se total students count return karo.
7. Ek function create karo jo number ka square return kare.
8. View aur stored procedure ke beech difference practice karo.

## 18. Quick Revision

| Concept           | Meaning                             |
| ----------------- | ----------------------------------- |
| View              | Query-based virtual table           |
| Simple View       | Generally single-table simple query |
| Complex View      | Joins/aggregates etc. par based     |
| Materialized View | Stored query result                 |
| CREATE VIEW       | View create karta hai               |
| DROP VIEW         | View definition delete karta hai    |
| Stored Procedure  | Stored executable SQL routine       |
| CALL              | MySQL procedure execute karta hai   |
| Function          | Value return karne wali routine     |
| IN                | Input parameter                     |
| OUT               | Output parameter                    |
| INOUT             | Input + Output parameter            |

**Remember:** View data ko present karne ka reusable way hai, jabki stored procedure database operations aur logic ko reusable banati hai.

## 19. MCQ Practice – 10 Questions

**Q1. View kya hoti hai?**

A. Hardware device  
B. Virtual table  
C. Programming language  
D. Operating system

**Q2. Materialized View kya store karti hai?**

A. Only database password  
B. Query result physically  
C. Only SQL comments  
D. Table name only

**Q3. View create karne ke liye kaunsa command use hota hai?**

A. CREATE VIEW  
B. INSERT VIEW  
C. ADD DATABASE  
D. SELECT VIEW

**Q4. Stored Procedure kahan store hoti hai?**

A. Browser  
B. Database server  
C. Keyboard  
D. HTML file

**Q5. MySQL mein procedure execute karne ke liye kya use hota hai?**

A. RUN  
B. CALL  
C. START HTML  
D. OPEN

**Q6. IN parameter ka purpose kya hai?**

A. Input receive karna  
B. Database delete karna  
C. Table rename karna  
D. Output only

**Q7. OUT parameter ka purpose kya hai?**

A. Input receive only  
B. Output provide karna  
C. Index create karna  
D. View delete karna

**Q8. Kaunsa routine generally value return karta hai?**

A. Function  
B. Table  
C. Index  
D. View

**Q9. MongoDB mein business logic generally kahan likhte hain?**

A. Node.js / Express.js  
B. SQL Stored Procedure  
C. HTML only  
D. CSS

**Q10. Kya har SQL View automatically updatable hoti hai?**

A. Yes  
B. No  
C. Only MongoDB  
D. Only HTML

### Answer Key

1-B, 2-B, 3-A, 4-B, 5-B, 6-A, 7-B, 8-A, 9-A, 10-B

---

**Topic 18 Complete – Views and Stored Procedures.**
