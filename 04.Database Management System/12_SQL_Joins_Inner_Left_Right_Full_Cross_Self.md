# Topic 12 – SQL Joins

## 1. What is SQL JOIN?

JOIN ka use two or more tables ke related records ko combine karke retrieve karne ke liye hota hai.

Example: `students` table mein student details hain aur `courses` table mein course details hain. JOIN ki help se dono ka related data ek result mein la sakte hain.

### Example Tables

**students**

| student_id | name  | course_id |
| ---------- | ----- | --------- |
| 1          | Rahul | 101       |
| 2          | Aman  | 102       |
| 3          | Priya | 103       |
| 4          | Neha  | NULL      |

**courses**

| course_id | course_name |
| --------- | ----------- |
| 101       | MERN        |
| 102       | Java        |
| 103       | Python      |
| 104       | C++         |

Common column: `course_id`

---

## 2. Types of SQL JOIN

Main JOIN types:

1. INNER JOIN
2. LEFT JOIN (LEFT OUTER JOIN)
3. RIGHT JOIN (RIGHT OUTER JOIN)
4. FULL OUTER JOIN
5. CROSS JOIN
6. SELF JOIN

## 3. INNER JOIN

INNER JOIN sirf matching records return karta hai.

```sql
SELECT students.name, courses.course_name
FROM students
INNER JOIN courses
ON students.course_id = courses.course_id;
```

**Result:**

| name  | course_name |
| ----- | ----------- |
| Rahul | MERN        |
| Aman  | Java        |
| Priya | Python      |

Neha ka record nahi aayega kyunki uska matching course nahi hai. C++ bhi nahi aayega kyunki us course ka matching student nahi hai.

**Remember:** INNER JOIN = Only matching rows.

## 4. LEFT JOIN

LEFT JOIN left table ke saare records aur right table ke matching records return karta hai.

```sql
SELECT students.name, courses.course_name
FROM students
LEFT JOIN courses
ON students.course_id = courses.course_id;
```

**Result:**

| name  | course_name |
| ----- | ----------- |
| Rahul | MERN        |
| Aman  | Java        |
| Priya | Python      |
| Neha  | NULL        |

Neha ka record aayega, lekin matching course nahi hone ke karan course_name NULL hoga.

**Remember:** LEFT JOIN = All left table rows + matching right rows.

## 5. RIGHT JOIN

RIGHT JOIN right table ke saare records aur left table ke matching records return karta hai.

```sql
SELECT students.name, courses.course_name
FROM students
RIGHT JOIN courses
ON students.course_id = courses.course_id;
```

**Result:**

| name  | course_name |
| ----- | ----------- |
| Rahul | MERN        |
| Aman  | Java        |
| Priya | Python      |
| NULL  | C++         |

C++ ka course aayega, chahe uska matching student na ho.

**Remember:** RIGHT JOIN = All right table rows + matching left rows.

## 6. FULL OUTER JOIN

FULL OUTER JOIN dono tables ke saare records return karta hai.

Matching records combine hote hain. Non-matching side ki values NULL hoti hain.

```sql
SELECT students.name, courses.course_name
FROM students
FULL OUTER JOIN courses
ON students.course_id = courses.course_id;
```

**Result:**

| name  | course_name |
| ----- | ----------- |
| Rahul | MERN        |
| Aman  | Java        |
| Priya | Python      |
| Neha  | NULL        |
| NULL  | C++         |

**Important:** MySQL mein native FULL OUTER JOIN syntax supported nahi hai. MySQL mein LEFT JOIN aur RIGHT JOIN ko UNION ke saath combine karke equivalent result banaya ja sakta hai.

MySQL example:

```sql
SELECT students.name, courses.course_name
FROM students
LEFT JOIN courses
ON students.course_id = courses.course_id

UNION

SELECT students.name, courses.course_name
FROM students
RIGHT JOIN courses
ON students.course_id = courses.course_id;
```

**Remember:** FULL OUTER JOIN = All rows from both tables.

## 7. CROSS JOIN

CROSS JOIN left table ki har row ko right table ki har row ke saath combine karta hai.

Isse Cartesian Product kehte hain.

```sql
SELECT students.name, courses.course_name
FROM students
CROSS JOIN courses;
```

Agar:

- Students mein 4 rows hain.
- Courses mein 4 rows hain.

Total result rows:

`4 × 4 = 16`

**Remember:** CROSS JOIN = Every possible combination.

## 8. SELF JOIN

Jab ek table ko usi table ke saath JOIN karte hain, use SELF JOIN kehte hain.

Example: Employees table mein employee aur manager dono ka data hai.

**employees**

| emp_id | emp_name | manager_id |
| ------ | -------- | ---------- |
| 1      | Amit     | NULL       |
| 2      | Rahul    | 1          |
| 3      | Neha     | 1          |
| 4      | Aman     | 2          |

Query:

```sql
SELECT
    e.emp_name AS employee,
    m.emp_name AS manager
FROM employees e
LEFT JOIN employees m
ON e.manager_id = m.emp_id;
```

Result:

| employee | manager |
| -------- | ------- |
| Amit     | NULL    |
| Rahul    | Amit    |
| Neha     | Amit    |
| Aman     | Rahul   |

Yahan:

- `e` = Employee table ka alias.
- `m` = Manager ke liye same table ka second reference.

## 9. JOIN with WHERE

JOIN ke result ko filter karne ke liye WHERE use kar sakte hain.

```sql
SELECT students.name, courses.course_name
FROM students
INNER JOIN courses
ON students.course_id = courses.course_id
WHERE courses.course_name = 'MERN';
```

Sirf MERN course wale matching students return honge.

## 10. JOIN with Multiple Tables

Ek query mein multiple tables join kar sakte hain.

Example:

**students**

| id  | name  |
| --- | ----- |
| 1   | Rahul |
| 2   | Aman  |

**enrollments**

| student_id | course_id |
| ---------- | --------- |
| 1          | 101       |
| 2          | 102       |

**courses**

| course_id | course_name |
| --------- | ----------- |
| 101       | MERN        |
| 102       | Java        |

Query:

```sql
SELECT
    s.name,
    c.course_name
FROM students s
INNER JOIN enrollments e
ON s.id = e.student_id
INNER JOIN courses c
ON e.course_id = c.course_id;
```

Result:

| name  | course_name |
| ----- | ----------- |
| Rahul | MERN        |
| Aman  | Java        |

---

## 11. JOIN vs UNION

| JOIN                                                    | UNION                                                 |
| ------------------------------------------------------- | ----------------------------------------------------- |
| Tables ko columns ke basis par combine karta hai        | SELECT results ko rows ke form mein combine karta hai |
| Related columns par matching condition use ho sakti hai | Corresponding columns compatible hone chahiye         |
| Result mein columns combine hote hain                   | Result mein rows append hoti hain                     |
| INNER, LEFT, RIGHT etc.                                 | UNION, UNION ALL                                      |

## 12. ON vs USING

### ON

JOIN condition explicitly define karta hai.

```sql
SELECT *
FROM students s
JOIN courses c
ON s.course_id = c.course_id;
```

### USING

Jab dono tables mein matching column ka same naam ho:

```sql
SELECT *
FROM students
JOIN courses
USING (course_id);
```

**Note:** USING ka support aur behavior DBMS-specific ho sakta hai. ON zyada widely applicable hai.

## 13. ON vs WHERE

- ON JOIN ke matching condition ko define karta hai.
- WHERE final joined result ko filter karta hai.

Example:

```sql
SELECT s.name, c.course_name
FROM students s
LEFT JOIN courses c
ON s.course_id = c.course_id
AND c.course_name = 'MERN';
```

Ye saare students ko retain karega, lekin sirf MERN matching course details attach karega.

Ab WHERE ke saath:

```sql
SELECT s.name, c.course_name
FROM students s
LEFT JOIN courses c
ON s.course_id = c.course_id
WHERE c.course_name = 'MERN';
```

Ye sirf MERN matching rows return karega. Unmatched students remove ho jayenge.

**Important Interview Point:** LEFT JOIN ke baad right table par WHERE condition lagane se result kai cases mein INNER JOIN jaisa behave kar sakta hai.

## 14. JOIN Summary Table

| JOIN            | Result                        |
| --------------- | ----------------------------- |
| INNER JOIN      | Only matching records         |
| LEFT JOIN       | All left + matching right     |
| RIGHT JOIN      | All right + matching left     |
| FULL OUTER JOIN | All records from both         |
| CROSS JOIN      | Every possible combination    |
| SELF JOIN       | Same table joined with itself |

## 15. SQL JOIN Visual Memory

```text
INNER JOIN
Only common matching area

LEFT JOIN
Complete left table + matching right

RIGHT JOIN
Complete right table + matching left

FULL OUTER JOIN
Complete both tables

CROSS JOIN
Every possible combination

SELF JOIN
One table joined to itself
```

## 16. Common Mistakes

1. JOIN condition bhool jana.
2. Wrong columns par JOIN karna.
3. LEFT JOIN aur INNER JOIN confuse karna.
4. FULL OUTER JOIN ko MySQL mein directly supported samajhna.
5. Multiple tables join karte waqt ambiguous column names use karna.
6. ON aur WHERE ka difference ignore karna.
7. CROSS JOIN se bahut large result generate kar dena.
8. Duplicate rows ko hamesha JOIN error samajhna; one-to-many relationships mein multiple rows expected ho sakti hain.

## 17. Performance Tips

- JOIN columns par suitable indexes consider karo.
- Sirf required columns SELECT karo.
- Correct join condition use karo.
- Large tables par query execution plan check karo.
- Unnecessary CROSS JOIN avoid karo.
- Foreign key columns par indexing performance mein help kar sakti hai, lekin index automatically har DBMS mein create nahi hota.

## 18. MERN Stack Connection

MERN default MongoDB use karta hai, lekin MongoDB mein related collections combine karne ke liye `$lookup` aggregation stage available hai.

SQL example:

```sql
SELECT s.name, c.course_name
FROM students s
JOIN courses c
ON s.course_id = c.course_id;
```

MongoDB conceptually similar operation:

```javascript
db.students.aggregate([
  {
    $lookup: {
      from: "courses",
      localField: "course_id",
      foreignField: "course_id",
      as: "course_details",
    },
  },
]);
```

**Remember:** SQL JOIN aur MongoDB `$lookup` related data combine karte hain, lekin unka data model aur execution behavior identical nahi hai.

---

## 19. Interview Questions

**Q1. What is JOIN?**

JOIN combines related records from two or more tables.

**Q2. INNER JOIN kya return karta hai?**

Sirf matching records.

**Q3. LEFT JOIN kya return karta hai?**

Left table ke saare records aur right table ke matching records.

**Q4. RIGHT JOIN kya return karta hai?**

Right table ke saare records aur left table ke matching records.

**Q5. FULL OUTER JOIN kya hai?**

Dono tables ke matching aur non-matching records return karta hai.

**Q6. CROSS JOIN kya hai?**

Cartesian product return karta hai.

**Q7. SELF JOIN kya hai?**

Ek table ko usi table ke saath join karna.

**Q8. Kya MySQL FULL OUTER JOIN support karta hai?**

MySQL native FULL OUTER JOIN syntax support nahi karta. LEFT JOIN aur RIGHT JOIN ko UNION ke saath use kar sakte hain.

**Q9. JOIN aur UNION mein difference?**

JOIN columns combine karta hai; UNION query results ki rows combine karta hai.

**Q10. ON ka use kya hai?**

JOIN ki matching condition define karta hai.

---

## 20. Practical Tasks

Assume these tables:

- students(id, name, course_id)
- courses(course_id, course_name)
- employees(emp_id, emp_name, manager_id)

Practice:

1. Students aur courses ko INNER JOIN karo.
2. Saare students aur unke course names LEFT JOIN se show karo.
3. Saare courses aur matching students RIGHT JOIN se show karo.
4. FULL OUTER JOIN ka equivalent MySQL query likho.
5. Students aur courses ka CROSS JOIN karo.
6. Employees aur managers ke names SELF JOIN se show karo.
7. Sirf MERN course wale students show karo.
8. Three tables students, enrollments aur courses join karo.

---

## 21. Quick Revision

- JOIN = Multiple tables ka related data combine.
- INNER = Matching rows only.
- LEFT = All left rows.
- RIGHT = All right rows.
- FULL = All rows from both.
- CROSS = Cartesian product.
- SELF = Same table joined with itself.
- ON = Join condition.
- WHERE = Filter result.
- UNION = Results ki rows combine.
- MySQL native FULL OUTER JOIN support nahi karta.
- MongoDB equivalent concept = `$lookup`.

---

## 22. MCQ Test

**Q1. Sirf matching records kaun return karta hai?**

A. LEFT JOIN  
B. INNER JOIN  
C. CROSS JOIN  
D. FULL JOIN

**Q2. Left table ke saare records kaun return karta hai?**

A. LEFT JOIN  
B. RIGHT JOIN  
C. INNER JOIN  
D. CROSS JOIN

**Q3. Cartesian Product kaun banata hai?**

A. INNER JOIN  
B. LEFT JOIN  
C. CROSS JOIN  
D. SELF JOIN

**Q4. Same table ko khud ke saath join karna kya kehlata hai?**

A. CROSS JOIN  
B. SELF JOIN  
C. FULL JOIN  
D. RIGHT JOIN

**Q5. MySQL mein native FULL OUTER JOIN supported hai?**

A. Yes  
B. No  
C. Only with WHERE  
D. Only with LIMIT

**Q6. JOIN ki matching condition ke liye kya use hota hai?**

A. ORDER BY  
B. ON  
C. LIMIT  
D. DISTINCT

**Q7. UNION kya combine karta hai?**

A. Columns only  
B. Query results ki rows  
C. Database schemas  
D. Indexes

**Q8. Right table ke saare records kaun return karta hai?**

A. LEFT JOIN  
B. INNER JOIN  
C. RIGHT JOIN  
D. SELF JOIN

**Q9. MongoDB mein related collections combine karne ke liye kaunsa stage use hota hai?**

A. $match  
B. $lookup  
C. $sort  
D. $limit

**Q10. FULL OUTER JOIN kya return karta hai?**

A. Only matching rows  
B. Only left rows  
C. Only right rows  
D. Both tables ke all rows

### Answer Key

| Question | Answer |
| -------- | ------ |
| Q1       | B      |
| Q2       | A      |
| Q3       | C      |
| Q4       | B      |
| Q5       | B      |
| Q6       | B      |
| Q7       | B      |
| Q8       | C      |
| Q9       | B      |
| Q10      | D      |

# Topic 12 Completed

**Next Topic 13:** SQL Subqueries – Single Row, Multiple Row, Nested Subqueries, Correlated Subqueries, EXISTS, ANY and ALL.
