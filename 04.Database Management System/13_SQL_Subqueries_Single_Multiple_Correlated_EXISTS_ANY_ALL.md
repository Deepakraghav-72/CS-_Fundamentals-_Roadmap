# 13. SQL Subqueries – Single, Multiple & Correlated

## 1. Subquery kya hoti hai?

**Subquery** ek SQL query ke andar likhi hui doosri query hoti hai.

- Inner Query: andar wali query.
- Outer Query: bahar wali main query.

Subquery ka result outer query use karti hai.

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name = (
    SELECT column_name
    FROM another_table
);
```

### Example

Un students ko find karo jinke marks average marks se zyada hain.

```sql
SELECT name, marks
FROM students
WHERE marks > (
    SELECT AVG(marks)
    FROM students
);
```

Pehle inner query average marks calculate karegi, phir outer query students filter karegi.

---

## 2. Types of Subqueries

Result aur working ke basis par subqueries ke main types:

| Type            | Meaning                              |
| --------------- | ------------------------------------ |
| Single-row      | Maximum ek row return kare           |
| Multiple-row    | Multiple rows return kare            |
| Scalar          | Ek row aur ek column ka single value |
| Multiple-column | Ek se zyada columns return kare      |
| Non-correlated  | Outer query par dependent nahi       |
| Correlated      | Outer query par dependent            |

**Note:** Scalar subquery single-row aur single-column result deti hai.

---

## 3. Scalar Subquery

Scalar subquery exactly ek value return karti hai.

### Example

```sql
SELECT name,
       marks,
       (SELECT AVG(marks) FROM students) AS average_marks
FROM students;
```

Yahan average marks har student ke saath show honge.

### Important Rules

- One column return hona chahiye.
- Maximum one row return honi chahiye.
- Agar multiple rows return hui to generally error aayega.
- Agar zero rows return hui, scalar context mein result `NULL` hota hai.

---

## 4. Single-Row Subquery

Single-row subquery maximum one row return karti hai.

Common operators:

`=`, `>`, `<`, `>=`, `<=`, `<>`

### Example

Average se zyada marks wale students:

```sql
SELECT name, marks
FROM students
WHERE marks > (
    SELECT AVG(marks)
    FROM students
);
```

Yahan `AVG()` ek single value return karta hai.

---

## 5. Multiple-Row Subquery

Multiple-row subquery ek se zyada rows return kar sakti hai.

Iske saath commonly use hone wale operators:

- IN
- NOT IN
- ANY / SOME
- ALL
- EXISTS
- NOT EXISTS

### Example – IN

Aise students find karo jo Delhi ya Noida mein rehte hain, aur cities ki list subquery se lao:

```sql
SELECT name, city
FROM students
WHERE city IN (
    SELECT city
    FROM allowed_cities
);
```

`IN` check karta hai ki value returned list mein present hai ya nahi.

### NOT IN

```sql
SELECT name
FROM students
WHERE city NOT IN (
    SELECT city
    FROM allowed_cities
);
```

Ye un students ko return karega jinki city allowed cities mein nahi hai.

**Important:** Agar subquery ke result mein `NULL` aa gaya, to `NOT IN` unexpected results de sakta hai. Is situation mein `NOT EXISTS` often safer hota hai.

---

## 6. ANY / SOME Operator

`ANY` ka meaning hai: comparison subquery ke **kam se kam ek** result ke saath true hona chahiye.

`SOME` aur `ANY` generally equivalent hain.

### Example

```sql
SELECT name, marks
FROM students
WHERE marks > ANY (
    SELECT marks
    FROM students
    WHERE city = 'Delhi'
);
```

Meaning: Student ke marks Delhi ke kam se kam ek student ke marks se zyada hone chahiye.

### Simple Understanding

Suppose subquery returns:

```text
40
60
80
```

Condition:

```sql
marks > ANY (40, 60, 80)
```

Agar marks 50 hain, condition TRUE hai kyunki 50 > 40.

---

## 7. ALL Operator

`ALL` ka meaning hai: comparison subquery ke **har result** ke saath true hona chahiye.

### Example

```sql
SELECT name, marks
FROM students
WHERE marks > ALL (
    SELECT marks
    FROM students
    WHERE city = 'Delhi'
);
```

Meaning: Student ke marks Delhi ke har student ke marks se zyada hone chahiye.

### ANY vs ALL

| ANY                                     | ALL                                  |
| --------------------------------------- | ------------------------------------ |
| At least one result                     | Every result                         |
| Ek result match hona enough             | Sabhi results match hone chahiye     |
| `> ANY` means greater than at least one | `> ALL` means greater than every one |

**Note:** Empty result set ke saath SQL ke three-valued logic rules apply hote hain; `ALL` generally TRUE aur `ANY` FALSE hota hai.

---

## 8. EXISTS Operator

`EXISTS` check karta hai ki subquery kam se kam ek row return karti hai ya nahi.

- Row present = TRUE
- Koi row nahi = FALSE

### Example

Aise students find karo jinhone kisi course mein enrollment kiya hai:

```sql
SELECT s.name
FROM students s
WHERE EXISTS (
    SELECT 1
    FROM enrollments e
    WHERE e.student_id = s.id
);
```

`SELECT 1` ka matlab hai ki humein actual column values nahi chahiye, sirf row existence check karni hai.

### NOT EXISTS

Aise students find karo jinhone abhi tak koi course join nahi kiya:

```sql
SELECT s.name
FROM students s
WHERE NOT EXISTS (
    SELECT 1
    FROM enrollments e
    WHERE e.student_id = s.id
);
```

---

## 9. Correlated Subquery

Correlated subquery outer query ke column par depend karti hai.

Isme inner query outer query ke current row ka data use karti hai.

### Example

Har student ko apne city ke average marks se compare karo:

```sql
SELECT s.name, s.city, s.marks
FROM students s
WHERE s.marks > (
    SELECT AVG(s2.marks)
    FROM students s2
    WHERE s2.city = s.city
);
```

Yahan:

- `s` = outer query ka alias.
- `s2` = inner query ka alias.
- `s.city` outer query se aata hai.
- `s2.city = s.city` dono queries ko connect karta hai.

### Working

1. Outer query ek student select karti hai.
2. Inner query us student ki city ka average calculate karti hai.
3. Student ke marks average se compare hote hain.
4. Ye process logically har outer row ke liye apply hota hai.

**Important:** Correlated subquery ko conceptually har outer row ke liye evaluate kiya ja sakta hai, lekin database optimizer ise rewrite ya optimize bhi kar sakta hai.

---

## 10. Non-Correlated vs Correlated Subquery

| Non-Correlated                  | Correlated                        |
| ------------------------------- | --------------------------------- |
| Outer query par depend nahi     | Outer query par depend            |
| Independent hoti hai            | Outer row ka reference leti hai   |
| Standalone execute ho sakti hai | Outer query ke context ki zarurat |
| Often simpler                   | Complex ho sakti hai              |

### Non-Correlated Example

```sql
SELECT name
FROM students
WHERE marks > (
    SELECT AVG(marks)
    FROM students
);
```

### Correlated Example

```sql
SELECT s.name
FROM students s
WHERE marks > (
    SELECT AVG(s2.marks)
    FROM students s2
    WHERE s2.city = s.city
);
```

---

## 11. Subquery in SELECT

Subquery ko SELECT statement ke andar bhi use kar sakte hain.

### Example

Har student ke saath total enrollment count show karo:

```sql
SELECT
    s.name,
    (
        SELECT COUNT(*)
        FROM enrollments e
        WHERE e.student_id = s.id
    ) AS total_courses
FROM students s;
```

Yahan subquery correlated hai kyunki `s.id` outer query se aa raha hai.

---

## 12. Subquery in FROM – Derived Table

Jab subquery ko FROM ke andar use karte hain, to uske result ko derived table kehte hain.

### Example

City-wise average marks calculate karo aur sirf un cities ko show karo jinka average 70 se zyada hai:

```sql
SELECT city, avg_marks
FROM (
    SELECT city, AVG(marks) AS avg_marks
    FROM students
    GROUP BY city
) AS city_result
WHERE avg_marks > 70;
```

**Important:** Derived table ko alias dena generally required hota hai.

---

## 13. Subquery in HAVING

HAVING ke andar bhi subquery use kar sakte hain.

### Example

Un cities ko find karo jinka average marks overall average se zyada hai:

```sql
SELECT city, AVG(marks) AS city_avg
FROM students
GROUP BY city
HAVING AVG(marks) > (
    SELECT AVG(marks)
    FROM students
);
```

Yahan:

- GROUP BY city-wise groups banata hai.
- HAVING groups ko filter karta hai.
- Subquery overall average calculate karti hai.

---

## 14. Subquery vs JOIN

Dono ka use related data retrieve karne ke liye ho sakta hai, lekin dono same nahi hain.

### Subquery Example

```sql
SELECT name
FROM students
WHERE id IN (
    SELECT student_id
    FROM enrollments
);
```

### JOIN Example

```sql
SELECT DISTINCT s.name
FROM students s
INNER JOIN enrollments e
ON s.id = e.student_id;
```

### Difference

| Subquery                  | JOIN                                                 |
| ------------------------- | ---------------------------------------------------- |
| Query ke andar query      | Tables ko combine karta hai                          |
| Filtering ke liye useful  | Multiple tables ka data combine karne ke liye useful |
| EXISTS se existence check | JOIN se matching rows                                |
| Nested structure          | Combined result set                                  |

**Kab kya use karein?**

- Sirf existence check karna ho → `EXISTS`
- Related table ke columns chahiye → `JOIN`
- Ek calculated value se comparison karna ho → Scalar subquery
- Complex query readable banani ho → CTE bhi option hai

**Performance:** Ye zaroori nahi ki JOIN hamesha subquery se faster ho. Performance query, indexes aur database optimizer par depend karti hai.

---

## 15. Subquery vs CTE (Basic Understanding)

CTE ka full form **Common Table Expression** hai.

CTE query ke andar temporary named result set define karta hai.

### Example

```sql
WITH average_marks AS (
    SELECT AVG(marks) AS avg_marks
    FROM students
)
SELECT s.name, s.marks
FROM students s
CROSS JOIN average_marks a
WHERE s.marks > a.avg_marks;
```

CTE complex queries ko readable aur manageable bana sakta hai.

---

## 16. Common Mistakes

1. Scalar subquery se multiple rows return karna.
2. `IN` subquery mein mismatched number of columns dena.
3. `NOT IN` ke saath NULL issue ignore karna.
4. Correlated subquery mein aliases galat use karna.
5. `EXISTS` ko value comparison samajhna.
6. `ANY` aur `ALL` ka difference bhoolna.
7. Har subquery ko slow samajhna.
8. Derived table ko alias na dena.
9. `ORDER BY` ko unnecessary subquery mein use karna. Subquery ke andar ORDER BY ka result outer query ki ordering guarantee nahi karta.

---

## 17. SQL Subqueries and MERN Stack

MERN mein MongoDB use hota hai, jisme SQL subqueries jaisa exact syntax nahi hota.

Kuch related concepts:

| SQL                        | MongoDB                                                             |
| -------------------------- | ------------------------------------------------------------------- |
| `IN`                       | `$in`                                                               |
| `EXISTS`-style check       | `$exists` (field existence; row existence ka exact equivalent nahi) |
| JOIN                       | `$lookup`                                                           |
| GROUP BY                   | `$group`                                                            |
| Nested query / aggregation | Aggregation pipeline                                                |

Example MongoDB `$in`:

```javascript
db.students.find({
  city: { $in: ["Delhi", "Noida"] },
});
```

Example `$lookup`:

```javascript
db.students.aggregate([
  {
    $lookup: {
      from: "enrollments",
      localField: "_id",
      foreignField: "student_id",
      as: "enrollments",
    },
  },
]);
```

**Remember:** SQL subqueries aur MongoDB aggregation operations conceptually kuch problems solve kar sakte hain, lekin unka syntax aur behavior same nahi hota.

---

## 18. Interview Questions and Answers

**Q1. What is a subquery?**

A query written inside another SQL query is called a subquery.

**Q2. What is a scalar subquery?**

A subquery that returns exactly one value (one row and one column).

**Q3. What is a correlated subquery?**

A subquery that references columns from its outer query.

**Q4. What is the difference between ANY and ALL?**

ANY requires at least one comparison to be true; ALL requires every comparison to be true.

**Q5. What does EXISTS do?**

It checks whether the subquery returns at least one row.

**Q6. What is a derived table?**

A subquery used in the FROM clause.

**Q7. What is the difference between IN and EXISTS?**

IN compares a value against a set of values. EXISTS checks whether matching rows exist.

**Q8. Why can NOT IN cause problems with NULL?**

Because comparisons involving NULL can evaluate to UNKNOWN, affecting the result.

**Q9. Can a subquery be used in SELECT?**

Yes, a scalar subquery can be used in the SELECT list.

**Q10. Are subqueries always slower than JOINs?**

No. Performance depends on the query, indexes, database and optimizer.

---

## 19. Practical Coding Tasks

1. Find students scoring above the overall average.
2. Find students living in cities listed in `allowed_cities` using IN.
3. Find students who have enrolled in at least one course using EXISTS.
4. Find students who have not enrolled in any course using NOT EXISTS.
5. Find students scoring above their city's average using a correlated subquery.
6. Find cities whose average marks are above the overall average using HAVING.
7. Display each student's name and enrollment count using a SELECT subquery.
8. Use a derived table to find cities with average marks above 70.

---

## 20. Quick Revision

- Subquery = Query inside another query.
- Inner query = Nested query.
- Outer query = Main query.
- Scalar = One value.
- Single-row = Maximum one row.
- Multiple-row = Multiple rows.
- IN = Value list mein present hai ya nahi.
- NOT IN = Value list mein present nahi.
- ANY = At least one comparison true.
- ALL = Every comparison true.
- EXISTS = At least one row exists.
- NOT EXISTS = No matching row exists.
- Correlated = Outer query par dependent.
- Non-correlated = Independent query.
- Derived table = Subquery in FROM.
- CTE = Named temporary result set for a statement.

---

## 21. MCQ Practice – 10 Questions

**Q1. Subquery kya hoti hai?**

A. Table  
B. Query inside another query  
C. Database  
D. Index

**Q2. Scalar subquery kitni values return karti hai?**

A. Multiple  
B. Zero columns  
C. Exactly one value  
D. Unlimited

**Q3. Multiple-row subquery ke saath kaunsa operator use hota hai?**

A. IN  
B. ANY  
C. ALL  
D. All of these

**Q4. EXISTS kya check karta hai?**

A. Table size  
B. Row existence  
C. Column type  
D. Database name

**Q5. Correlated subquery kis par dependent hoti hai?**

A. Index  
B. Outer query  
C. Database name  
D. Server port

**Q6. ANY ka meaning kya hai?**

A. All rows  
B. At least one comparison true  
C. No rows  
D. Exactly one row

**Q7. ALL ka meaning kya hai?**

A. Every comparison true  
B. One comparison true  
C. No comparison  
D. First row only

**Q8. FROM ke andar subquery ko kya kehte hain?**

A. Trigger  
B. Derived table  
C. Primary key  
D. View only

**Q9. NOT IN ke saath kaunsi value problem create kar sakti hai?**

A. 0  
B. 1  
C. NULL  
D. 100

**Q10. EXISTS ke andar commonly kya likha jata hai?**

A. SELECT 1  
B. CREATE TABLE  
C. DROP DATABASE  
D. ALTER TABLE

### Answer Key

1-B, 2-C, 3-D, 4-B, 5-B, 6-B, 7-A, 8-B, 9-C, 10-A

---

**Topic 13 Complete – SQL Subqueries.**
