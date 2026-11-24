# Topic 11 – SQL Operators and Functions

## 1. Introduction

SQL Operators ka use conditions, calculations aur data filtering ke liye hota hai.

SQL Functions ka use data par predefined operations perform karne ke liye hota hai.

Example:

```sql
SELECT * FROM students
WHERE marks > 80;
```

Yahan `>` comparison operator hai.

```sql
SELECT COUNT(*) FROM students;
```

Yahan `COUNT()` function hai.

---

## 2. Types of SQL Operators

SQL operators ki main categories:

1. Arithmetic Operators
2. Comparison Operators
3. Logical Operators
4. Special Operators
5. Set Operators
6. String Concatenation Operators

## 3. Arithmetic Operators

Mathematical calculations ke liye use hote hain.

| Operator | Meaning             | Example |
| -------- | ------------------- | ------- |
| +        | Addition            | 10 + 5  |
| -        | Subtraction         | 10 - 5  |
| \*       | Multiplication      | 10 \* 5 |
| /        | Division            | 10 / 5  |
| %        | Modulus / Remainder | 10 % 3  |

Example:

```sql
SELECT
    10 + 5 AS addition,
    10 - 5 AS subtraction,
    10 * 5 AS multiplication,
    10 / 5 AS division,
    10 % 3 AS remainder;
```

Table ke saath:

```sql
SELECT name, marks + 5 AS updated_marks
FROM students;
```

**Note:** Division aur modulus ka exact behavior data types aur DBMS ke according vary kar sakta hai.

## 4. Comparison Operators

Values compare karne ke liye use hote hain.

| Operator | Meaning                      |
| -------- | ---------------------------- |
| =        | Equal                        |
| <>       | Not equal                    |
| !=       | Not equal (widely supported) |
| >        | Greater than                 |
| <        | Less than                    |
| >=       | Greater than or equal        |
| <=       | Less than or equal           |

Examples:

```sql
SELECT * FROM students WHERE marks = 90;

SELECT * FROM students WHERE marks <> 90;

SELECT * FROM students WHERE marks > 80;

SELECT * FROM students WHERE marks < 50;

SELECT * FROM students WHERE marks >= 80;

SELECT * FROM students WHERE marks <= 90;
```

**Important:** NULL ko normal comparison operators se check nahi karte. Uske liye IS NULL / IS NOT NULL use karo.

## 5. Logical Operators

Multiple conditions combine karne ke liye use hote hain.

### A. AND

Saari conditions TRUE honi chahiye.

```sql
SELECT * FROM students
WHERE age > 18 AND marks > 80;
```

### B. OR

Kam se kam ek condition TRUE honi chahiye.

```sql
SELECT * FROM students
WHERE city = 'Delhi' OR city = 'Noida';
```

### C. NOT

Condition ko logically reverse karta hai.

```sql
SELECT * FROM students
WHERE NOT city = 'Delhi';
```

### Truth Table

| A     | B     | A AND B | A OR B |
| ----- | ----- | ------- | ------ |
| TRUE  | TRUE  | TRUE    | TRUE   |
| TRUE  | FALSE | FALSE   | TRUE   |
| FALSE | TRUE  | FALSE   | TRUE   |
| FALSE | FALSE | FALSE   | FALSE  |

SQL mein NULL ke kaaran TRUE, FALSE ke alawa UNKNOWN bhi ho sakta hai.

## 6. Special Operators

### A. BETWEEN

Range ke andar values check karta hai. Dono endpoints included hote hain.

```sql
SELECT * FROM students
WHERE marks BETWEEN 60 AND 90;
```

### B. IN

Multiple values mein match check karta hai.

```sql
SELECT * FROM students
WHERE city IN ('Delhi', 'Meerut', 'Noida');
```

### C. NOT IN

Specified values ko exclude karta hai.

```sql
SELECT * FROM students
WHERE city NOT IN ('Delhi', 'Noida');
```

**Warning:** NOT IN ke list/subquery mein NULL hone par result unexpected ho sakta hai. NULL handling carefully karo.

### D. LIKE

Pattern matching ke liye use hota hai.

| Wildcard | Meaning                 |
| -------- | ----------------------- |
| %        | Zero ya more characters |
| \_       | Exactly one character   |

Examples:

```sql
-- R se start hone wale names
SELECT * FROM students
WHERE name LIKE 'R%';

-- a par end hone wale names
SELECT * FROM students
WHERE name LIKE '%a';

-- Naam mein rah contain ho
SELECT * FROM students
WHERE name LIKE '%rah%';

-- Second character a ho
SELECT * FROM students
WHERE name LIKE '_a%';
```

### E. IS NULL

NULL values find karta hai.

```sql
SELECT * FROM students
WHERE city IS NULL;
```

### F. IS NOT NULL

Non-NULL values find karta hai.

```sql
SELECT * FROM students
WHERE city IS NOT NULL;
```

### G. EXISTS

Subquery mein at least one row exist karti hai ya nahi, check karta hai.

```sql
SELECT *
FROM students s
WHERE EXISTS (
    SELECT 1
    FROM enrollments e
    WHERE e.student_id = s.id
);
```

Ye un students ko return karega jinki at least one enrollment hai.

## 7. Set Operators

Multiple SELECT query results ko combine karne ke liye use hote hain.

| Operator  | Meaning                                    |
| --------- | ------------------------------------------ |
| UNION     | Results combine, duplicates remove         |
| UNION ALL | Results combine, duplicates retain         |
| INTERSECT | Common rows                                |
| EXCEPT    | First result mein rows jo second mein nahi |

Example:

```sql
SELECT city FROM students
UNION
SELECT city FROM teachers;
```

UNION ALL:

```sql
SELECT city FROM students
UNION ALL
SELECT city FROM teachers;
```

INTERSECT:

```sql
SELECT city FROM students
INTERSECT
SELECT city FROM teachers;
```

EXCEPT:

```sql
SELECT city FROM students
EXCEPT
SELECT city FROM teachers;
```

**Rules:**

- SELECT statements mein columns ki count same honi chahiye.
- Corresponding columns ke data types compatible hone chahiye.
- UNION duplicate rows remove karta hai.
- UNION ALL duplicates retain karta hai.
- INTERSECT aur EXCEPT ka support/syntax DBMS ke according vary kar sakta hai. Oracle mein EXCEPT ke badle MINUS commonly use hota hai.

## 8. SQL Functions

Functions predefined operations perform karte hain aur result return karte hain.

Main categories:

1. Aggregate Functions
2. String Functions
3. Numeric Functions
4. Date and Time Functions
5. NULL Handling Functions
6. Conversion Functions

## 9. Aggregate Functions

Multiple rows par calculation karke generally ek result return karte hain.

Assume `students` table:

| id  | name  | marks |
| --- | ----- | ----: |
| 1   | Rahul |    85 |
| 2   | Aman  |    90 |
| 3   | Priya |    95 |
| 4   | Neha  |    75 |

### A. COUNT()

Rows count karta hai.

```sql
SELECT COUNT(*) FROM students;
```

Result: 4

```sql
SELECT COUNT(marks) FROM students;
```

COUNT(column) NULL values ko count nahi karta.

### B. SUM()

Total calculate karta hai.

```sql
SELECT SUM(marks) FROM students;
```

### C. AVG()

Average calculate karta hai.

```sql
SELECT AVG(marks) FROM students;
```

### D. MAX()

Maximum value return karta hai.

```sql
SELECT MAX(marks) FROM students;
```

### E. MIN()

Minimum value return karta hai.

```sql
SELECT MIN(marks) FROM students;
```

### Quick Table

| Function | Purpose |
| -------- | ------- |
| COUNT()  | Count   |
| SUM()    | Total   |
| AVG()    | Average |
| MAX()    | Maximum |
| MIN()    | Minimum |

**Important:** Aggregate functions generally NULL values ignore karte hain, except COUNT(\*), jo rows count karta hai.

## 10. GROUP BY

Same values wale records ko groups mein divide karta hai.

Example:

```sql
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city;
```

Har city mein kitne students hain, result mein aayega.

### GROUP BY with SUM

```sql
SELECT city, SUM(marks) AS total_marks
FROM students
GROUP BY city;
```

## 11. HAVING

GROUP BY ke baad groups ko filter karne ke liye HAVING use hota hai.

```sql
SELECT city, COUNT(*) AS total_students
FROM students
GROUP BY city
HAVING COUNT(*) > 2;
```

### WHERE vs HAVING

| WHERE                                               | HAVING                                    |
| --------------------------------------------------- | ----------------------------------------- |
| Individual rows filter karta hai                    | Groups filter karta hai                   |
| GROUP BY se pehle logically apply hota hai          | Grouping ke baad logically apply hota hai |
| Aggregate condition ke liye generally use nahi hota | Aggregate conditions ke liye use hota hai |

Example:

```sql
SELECT city, AVG(marks)
FROM students
WHERE marks >= 40
GROUP BY city
HAVING AVG(marks) > 70;
```

Pehle 40 se kam marks wale records exclude honge, phir city-wise grouping hogi, aur 70 se zyada average wale groups return honge.

## 12. String Functions

Text values par operations perform karte hain.

| Function    | Purpose                                               |
| ----------- | ----------------------------------------------------- |
| UPPER()     | Uppercase                                             |
| LOWER()     | Lowercase                                             |
| LENGTH()    | String length (DBMS-specific byte/character behavior) |
| TRIM()      | Extra surrounding spaces remove                       |
| CONCAT()    | Strings join                                          |
| SUBSTRING() | Part of string                                        |
| REPLACE()   | Text replace                                          |

Examples:

```sql
SELECT UPPER(name) FROM students;

SELECT LOWER(name) FROM students;

SELECT LENGTH(name) FROM students;

SELECT TRIM('  Rahul  ');

SELECT CONCAT(name, ' - Student')
FROM students;

SELECT SUBSTRING(name, 1, 3)
FROM students;

SELECT REPLACE(name, 'Rahul', 'Rohan')
FROM students;
```

**Note:** String function names aur exact syntax DBMS ke according vary kar sakte hain.

## 13. Numeric Functions

Numbers par calculations perform karte hain.

| Function           | Purpose            |
| ------------------ | ------------------ |
| ABS()              | Absolute value     |
| ROUND()            | Round off          |
| CEIL() / CEILING() | Next upper integer |
| FLOOR()            | Lower integer      |
| MOD()              | Remainder          |
| POWER()            | Power              |

Examples:

```sql
SELECT ABS(-10);

SELECT ROUND(12.567, 2);

SELECT CEIL(12.3);

SELECT FLOOR(12.9);

SELECT MOD(10, 3);

SELECT POWER(2, 3);
```

Possible results:

- ABS(-10) = 10
- ROUND(12.567, 2) = 12.57
- CEIL(12.3) = 13
- FLOOR(12.9) = 12
- MOD(10, 3) = 1
- POWER(2, 3) = 8

## 14. Date and Time Functions

Date aur time values handle karne ke liye.

| Function          | Purpose               |
| ----------------- | --------------------- |
| CURRENT_DATE      | Current date          |
| CURRENT_TIME      | Current time          |
| CURRENT_TIMESTAMP | Current date and time |
| EXTRACT           | Date ka specific part |

Examples:

```sql
SELECT CURRENT_DATE;

SELECT CURRENT_TIME;

SELECT CURRENT_TIMESTAMP;
```

Date ka year extract karna:

```sql
SELECT EXTRACT(YEAR FROM CURRENT_DATE);
```

**Note:** Date functions ki syntax MySQL, PostgreSQL, Oracle aur SQL Server mein different ho sakti hai.

## 15. NULL Handling Functions

NULL values ko handle karne ke liye.

### A. COALESCE()

First non-NULL value return karta hai.

```sql
SELECT COALESCE(city, 'Unknown')
FROM students;
```

Agar city NULL hai to Unknown show hoga.

### B. NULLIF()

Dono values equal hon to NULL return karta hai, otherwise first value.

```sql
SELECT NULLIF(10, 10);
```

Result: NULL

```sql
SELECT NULLIF(10, 5);
```

Result: 10

### C. IFNULL()

MySQL mein NULL value ka alternative return karta hai.

```sql
SELECT IFNULL(city, 'Unknown')
FROM students;
```

### D. ISNULL()

SQL Server mein NULL check/handling ke liye use hota hai, lekin syntax context-specific hai.

**Remember:** COALESCE standard SQL function hai; IFNULL aur ISNULL ka behavior database-specific ho sakta hai.

## 16. Type Conversion Functions

Ek data type ko doosre data type mein convert karne ke liye.

### CAST()

```sql
SELECT CAST('123' AS INTEGER);
```

String number ko integer mein convert karta hai, agar valid ho.

### CONVERT()

SQL Server example:

```sql
SELECT CONVERT(INT, '123');
```

Exact conversion syntax DBMS-specific hota hai.

## 17. Operator Precedence

Jab ek query mein multiple operators hote hain, to precedence decide karti hai ki operation kis order mein evaluate hoga.

Common order (simplified):

1. Parentheses `()`
2. Arithmetic operators
3. Comparison operators
4. NOT
5. AND
6. OR

Example:

```sql
SELECT *
FROM students
WHERE age > 18 AND (city = 'Delhi' OR city = 'Noida');
```

Parentheses ki wajah se pehle city conditions evaluate hongi, phir age condition ke saath AND apply hoga.

**Best Practice:** Complex conditions mein parentheses use karo.

## 18. SQL Query Execution Order (Logical)

Query likhne ka order aur logical processing order different ho sakta hai.

Query:

```sql
SELECT city, COUNT(*)
FROM students
WHERE marks > 50
GROUP BY city
HAVING COUNT(*) > 2
ORDER BY city;
```

Simplified logical order:

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY

Ye logical explanation hai; actual database execution optimizer ke according different ho sakta hai.

## 19. Common Mistakes

1. `= NULL` use karna; correct `IS NULL` hai.
2. COUNT(\*) aur COUNT(column) ko same samajhna.
3. WHERE aur HAVING confuse karna.
4. UNION aur UNION ALL ko same samajhna.
5. NOT IN ke andar NULL ka effect ignore karna.
6. Aggregate functions ko bina grouping samjhe use karna.
7. Complex conditions mein parentheses na lagana.
8. Har DBMS mein same function syntax assume karna.
9. ORDER BY ke bina result order fixed samajhna.

## 20. Interview Questions

**Q1. SQL operator kya hai?**

Operator ek symbol ya keyword hai jo values par operation perform karta hai.

**Q2. SQL functions kya hain?**

Predefined operations jo input lekar result return karte hain.

**Q3. Aggregate functions ke examples?**

COUNT, SUM, AVG, MAX, MIN.

**Q4. COUNT(\*) aur COUNT(column) mein difference?**

COUNT(\*) rows count karta hai; COUNT(column) non-NULL values count karta hai.

**Q5. WHERE aur HAVING mein difference?**

WHERE rows filter karta hai; HAVING groups filter karta hai.

**Q6. UNION aur UNION ALL mein difference?**

UNION duplicates remove karta hai; UNION ALL duplicates retain karta hai.

**Q7. BETWEEN inclusive hota hai ya exclusive?**

Inclusive; starting aur ending values dono include hoti hain.

**Q8. LIKE mein % ka meaning?**

Zero ya more characters.

**Q9. COALESCE kya karta hai?**

First non-NULL expression return karta hai.

**Q10. GROUP BY ka purpose?**

Rows ko common column values ke basis par groups mein divide karna.

**Q11. EXISTS kya karta hai?**

Check karta hai ki subquery at least one row return karti hai ya nahi.

**Q12. SQL execution ka simplified logical order kya hai?**

FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY.

## 21. Practical Tasks

Assume table: `students(id, name, age, city, marks)`.

1. Total students count karo.
2. Maximum marks find karo.
3. Minimum marks find karo.
4. Average marks calculate karo.
5. Total marks calculate karo.
6. City-wise students count karo.
7. Sirf un cities ko show karo jahan 2 se zyada students hain.
8. Names uppercase mein show karo.
9. Marks ko 5 se increase karke display karo.
10. NULL city ko Unknown se replace karke show karo.
11. Marks 60 se 90 ke beech wale students find karo.
12. Delhi aur Meerut ke students find karo.
13. Students ko marks ke descending order mein show karo.
14. Students ke naam R se start hone chahiye.
15. Students table mein city-wise average marks find karo.

### Practice Solutions

```sql
-- 1
SELECT COUNT(*) FROM students;

-- 2
SELECT MAX(marks) FROM students;

-- 3
SELECT MIN(marks) FROM students;

-- 4
SELECT AVG(marks) FROM students;

-- 5
SELECT SUM(marks) FROM students;

-- 6
SELECT city, COUNT(*)
FROM students
GROUP BY city;

-- 7
SELECT city, COUNT(*)
FROM students
GROUP BY city
HAVING COUNT(*) > 2;

-- 8
SELECT UPPER(name) FROM students;

-- 9
SELECT name, marks + 5 AS new_marks
FROM students;

-- 10
SELECT COALESCE(city, 'Unknown')
FROM students;

-- 11
SELECT * FROM students
WHERE marks BETWEEN 60 AND 90;

-- 12
SELECT * FROM students
WHERE city IN ('Delhi', 'Meerut');

-- 13
SELECT * FROM students
ORDER BY marks DESC;

-- 14
SELECT * FROM students
WHERE name LIKE 'R%';

-- 15
SELECT city, AVG(marks)
FROM students
GROUP BY city;
```

---

## 22. Quick Revision

- Arithmetic: +, -, \*, /, %
- Comparison: =, <>, !=, >, <, >=, <=
- Logical: AND, OR, NOT
- Special: BETWEEN, IN, LIKE, IS NULL, EXISTS
- Set: UNION, UNION ALL, INTERSECT, EXCEPT
- Aggregate: COUNT, SUM, AVG, MAX, MIN
- String: UPPER, LOWER, TRIM, CONCAT, SUBSTRING
- Numeric: ABS, ROUND, CEIL, FLOOR, MOD, POWER
- Date: CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP
- NULL handling: COALESCE, NULLIF
- Conversion: CAST, CONVERT
- GROUP BY = Groups create.
- HAVING = Groups filter.
- WHERE = Rows filter.

---

## 23. MCQ Test

**Q1. Greater than operator kaunsa hai?**

A. <
B. >
C. =
D. !=

**Q2. Multiple conditions mein sab TRUE honi chahiye to kya use hoga?**

A. OR
B. NOT
C. AND
D. LIKE

**Q3. Aggregate function kaunsa hai?**

A. UPPER
B. COUNT
C. TRIM
D. ROUND

**Q4. Groups filter karne ke liye kya use hota hai?**

A. WHERE
B. ORDER BY
C. HAVING
D. DISTINCT

**Q5. UNION ALL kya karta hai?**

A. Duplicates remove
B. Duplicates retain
C. Rows delete
D. Table create

**Q6. First non-NULL value return karne wala function?**

A. NULLIF
B. COALESCE
C. COUNT
D. MAX

**Q7. LIKE mein multiple characters ke liye wildcard?**

A. \_
B. %
C. \*
D. #

**Q8. Average calculate karne wala function?**

A. SUM
B. COUNT
C. AVG
D. MIN

**Q9. Range check karne wala operator?**

A. BETWEEN
B. EXISTS
C. NOT
D. CONCAT

**Q10. Rows ko groups mein divide karne ke liye kya use hota hai?**

A. DISTINCT
B. GROUP BY
C. LIMIT
D. UPDATE

### Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | C      |
| Q3       | B      |
| Q4       | C      |
| Q5       | B      |
| Q6       | B      |
| Q7       | B      |
| Q8       | C      |
| Q9       | A      |
| Q10      | B      |

# Topic 11 Completed

**Next Topic 12:** SQL Joins – INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN, CROSS JOIN, SELF JOIN aur practical examples.
