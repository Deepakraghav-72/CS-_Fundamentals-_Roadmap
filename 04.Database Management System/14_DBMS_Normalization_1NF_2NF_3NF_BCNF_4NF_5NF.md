# 14. DBMS Normalization – 1NF, 2NF, 3NF, BCNF, 4NF & 5NF

## 1. Normalization kya hoti hai?

**Normalization** ek database design technique hai jisme tables ko properly organize kiya jata hai, taaki:

- Duplicate data kam ho.
- Data consistency maintain rahe.
- Insert, Update aur Delete anomalies avoid hon.
- Data relationships properly manage hon.

Simple words mein: Database ko aise organize karna ki unnecessary data repetition na ho aur data easily maintain ho sake.

### Example – Unnormalized Table

| Student_ID | Student_Name | Courses      |
| ---------- | ------------ | ------------ |
| 1          | Rahul        | Java, Python |
| 2          | Aman         | C++, Java    |

Yahan ek cell mein multiple course values hain. Ye design 1NF follow nahi karta.

Normalization ke baad:

**Students**

| Student_ID | Student_Name |
| ---------- | ------------ |
| 1          | Rahul        |
| 2          | Aman         |

**Enrollments**

| Student_ID | Course |
| ---------- | ------ |
| 1          | Java   |
| 1          | Python |
| 2          | C++    |
| 2          | Java   |

Ab data better organized hai.

---

## 2. Normalization ki Need

Normalization ke bina database mein ye problems aa sakti hain:

1. Data duplication.
2. Inconsistent data.
3. Storage wastage.
4. Difficult updates.
5. Data insertion problems.
6. Accidental data loss during deletion.

---

## 3. Database Anomalies

Anomaly ka matlab database operation ke time unwanted problem.

### A. Insertion Anomaly

Jab kisi information ko insert karne ke liye unnecessary extra information deni pade.

Example:

| Student_ID | Student_Name | Course |
| ---------- | ------------ | ------ |
| 1          | Rahul        | Java   |

Agar humein ek new course Python add karna hai, lekin abhi koi student enrolled nahi hai, to is combined table mein course information independently insert karna difficult ho sakta hai.

### B. Update Anomaly

Same information multiple rows mein stored ho aur update karte time kuch rows update karna bhool jayein.

Example:

| Student_ID | Student_Name | Course | Instructor |
| ---------- | ------------ | ------ | ---------- |
| 1          | Rahul        | Java   | Amit       |
| 2          | Aman         | Java   | Amit       |

Agar instructor ka naam change ho, to dono rows update karni hongi. Ek row update na hui to inconsistent data ho jayega.

### C. Deletion Anomaly

Ek record delete karne se kisi doosri important information ka bhi loss ho jana.

Example:

| Student_ID | Student_Name | Course |
| ---------- | ------------ | ------ |
| 1          | Rahul        | Java   |
| 2          | Aman         | Python |

Agar Aman ka last enrollment delete kar diya, aur course information sirf isi table mein stored thi, to Python course ki information bhi lost ho sakti hai.

---

## 4. Functional Dependency (FD)

Functional Dependency normalization ka important concept hai.

Agar ek attribute ki value se doosre attribute ki value uniquely determine hoti hai, to ise Functional Dependency kehte hain.

Notation:

```text
A → B
```

Meaning: A determines B.

### Example

| Student_ID | Student_Name |
| ---------- | ------------ |
| 1          | Rahul        |
| 2          | Aman         |

Yahan:

```text
Student_ID → Student_Name
```

Student_ID se Student_Name determine ho sakta hai.

### Types of Functional Dependency

| Type                       | Meaning                                                    |
| -------------------------- | ---------------------------------------------------------- |
| Trivial FD                 | RHS attributes, LHS ka subset hote hain                    |
| Non-trivial FD             | RHS, LHS ka subset nahi hota                               |
| Full Functional Dependency | Complete composite determinant required hota hai           |
| Partial Dependency         | Composite key ke kisi proper subset par dependency         |
| Transitive Dependency      | A → B aur B → C, isliye A indirectly C determine karta hai |

### Examples

**Trivial:**

```text
(Student_ID, Name) → Name
```

**Non-trivial:**

```text
Student_ID → Name
```

**Full Dependency:**

```text
(Student_ID, Course_ID) → Grade
```

Agar Grade determine karne ke liye dono attributes required hain.

**Partial Dependency:**

```text
(Student_ID, Course_ID) → Student_Name
Student_ID → Student_Name
```

Yahan Student_Name composite key ke sirf Student_ID part par depend karta hai.

**Transitive Dependency:**

```text
Student_ID → Department_ID
Department_ID → Department_Name
```

Isliye Student_ID indirectly Department_Name determine karta hai.

---

## 5. First Normal Form (1NF)

**1NF rule:** Table ke har cell mein atomic (single) value honi chahiye aur repeating groups nahi hone chahiye.

### Before 1NF

| Student_ID | Name  | Subjects     |
| ---------- | ----- | ------------ |
| 1          | Rahul | Java, Python |
| 2          | Aman  | C++, HTML    |

Problem: Subjects column mein multiple values hain.

### After 1NF

| Student_ID | Name  | Subject |
| ---------- | ----- | ------- |
| 1          | Rahul | Java    |
| 1          | Rahul | Python  |
| 2          | Aman  | C++     |
| 2          | Aman  | HTML    |

Ab har cell mein single value hai.

### 1NF Rules

- Each cell contains one value.
- No repeating groups.
- Each row should be uniquely identifiable.
- Column values should belong to a consistent domain.

**Important:** Atomicity context-dependent hoti hai. Database design ke use case ke according decide hota hai ki value ko further divide karna zaroori hai ya nahi.

---

## 6. Second Normal Form (2NF)

**2NF rule:**

1. Table 1NF mein honi chahiye.
2. Har non-prime attribute, candidate key par fully functionally dependent hona chahiye.

Simple words mein: Composite candidate key ke kisi ek part par non-key attribute depend nahi hona chahiye.

### Example – Before 2NF

| Student_ID | Course_ID | Student_Name | Course_Name |
| ---------- | --------- | ------------ | ----------- |
| 1          | C1        | Rahul        | Java        |
| 1          | C2        | Rahul        | Python      |
| 2          | C1        | Aman         | Java        |

Composite Primary Key:

```text
(Student_ID, Course_ID)
```

Dependencies:

```text
Student_ID → Student_Name
Course_ID → Course_Name
(Student_ID, Course_ID) → Enrollment
```

Problem:

- Student_Name sirf Student_ID par depend karta hai.
- Course_Name sirf Course_ID par depend karta hai.

Ye partial dependencies hain.

### After 2NF

**Students**

| Student_ID (PK) | Student_Name |
| --------------- | ------------ |
| 1               | Rahul        |
| 2               | Aman         |

**Courses**

| Course_ID (PK) | Course_Name |
| -------------- | ----------- |
| C1             | Java        |
| C2             | Python      |

**Enrollments**

| Student_ID (FK) | Course_ID (FK) |
| --------------- | -------------- |
| 1               | C1             |
| 1               | C2             |
| 2               | C1             |

Ab partial dependencies remove ho gayi hain.

**Important:** Agar table mein har candidate key single attribute ki hai, to partial dependency possible nahi hoti. Aisi table agar 1NF mein hai to 2NF bhi satisfy karti hai.

---

## 7. Third Normal Form (3NF)

**3NF rule:**

1. Table 2NF mein honi chahiye.
2. Non-prime attributes mein improper transitive dependency nahi honi chahiye.

Formal rule: Har non-trivial FD `X → A` ke liye, ya to X superkey ho ya A prime attribute ho.

### Example – Before 3NF

| Student_ID | Student_Name | Department_ID | Department_Name |
| ---------- | ------------ | ------------- | --------------- |
| 1          | Rahul        | D1            | Computer        |
| 2          | Aman         | D2            | IT              |

Dependencies:

```text
Student_ID → Student_Name
Student_ID → Department_ID
Department_ID → Department_Name
```

Yahan:

```text
Student_ID → Department_ID → Department_Name
```

Department_Name indirectly Student_ID par depend karta hai.

Ye transitive dependency hai.

### After 3NF

**Students**

| Student_ID (PK) | Student_Name | Department_ID (FK) |
| --------------- | ------------ | ------------------ |
| 1               | Rahul        | D1                 |
| 2               | Aman         | D2                 |

**Departments**

| Department_ID (PK) | Department_Name |
| ------------------ | --------------- |
| D1                 | Computer        |
| D2                 | IT              |

Ab Department_Name separately store hota hai.

---

## 8. BCNF (Boyce-Codd Normal Form)

BCNF, 3NF se stronger normal form hai.

**BCNF rule:** Har non-trivial functional dependency `X → Y` mein X ek superkey hona chahiye.

### 3NF vs BCNF

| 3NF                                             | BCNF                                  |
| ----------------------------------------------- | ------------------------------------- |
| Less strict                                     | More strict                           |
| RHS prime attribute hone par exception possible | Har determinant superkey hona chahiye |
| Some anomalies remain possible                  | Stronger redundancy control           |

### Example

Relation:

```text
Student, Course, Instructor
```

Assume:

- Ek student ek course mein ek instructor se padhta hai.
- Har instructor sirf ek course teach karta hai.
- Ek course ko multiple instructors padha sakte hain.

Functional dependencies:

```text
(Student, Course) → Instructor
Instructor → Course
```

Candidate keys:

```text
(Student, Course)
(Student, Instructor)
```

`Instructor → Course` mein Instructor superkey nahi hai, lekin Course prime attribute hai (candidate keys ka part).

Isliye relation 3NF satisfy kar sakta hai, lekin BCNF violate karta hai.

### BCNF Decomposition

**Instructor_Course**

| Instructor (PK) | Course |
| --------------- | ------ |

**Student_Instructor**

| Student | Instructor |
| ------- | ---------- |

Decomposition ka purpose non-superkey determinant wali dependency ko alag relation mein organize karna hai.

---

## 9. Fourth Normal Form (4NF)

4NF multivalued dependencies ko handle karti hai.

**4NF rule:** Relation BCNF mein honi chahiye aur har non-trivial multivalued dependency ka determinant superkey hona chahiye.

### Example

Ek student ke multiple hobbies aur multiple languages hain. Dono independent hain.

| Student | Hobby   | Language |
| ------- | ------- | -------- |
| Rahul   | Cricket | Hindi    |
| Rahul   | Cricket | English  |
| Rahul   | Music   | Hindi    |
| Rahul   | Music   | English  |

Yahan unnecessary combinations store ho rahe hain.

### 4NF Decomposition

**Student_Hobby**

| Student | Hobby   |
| ------- | ------- |
| Rahul   | Cricket |
| Rahul   | Music   |

**Student_Language**

| Student | Language |
| ------- | -------- |
| Rahul   | Hindi    |
| Rahul   | English  |

Ab independent multivalued facts alag store hain.

---

## 10. Fifth Normal Form (5NF)

5NF ko Project-Join Normal Form (PJNF) bhi kehte hain.

**5NF rule:** Relation mein non-trivial join dependencies candidate keys se implied honi chahiye.

Simple words mein: Table ko smaller tables mein tab decompose kiya jata hai jab decomposition ke baad JOIN karke original information accurately recover ho sake aur unnecessary redundancy remove ho.

### Example Concept

Suppose ek business record karta hai:

- Supplier
- Part
- Project

Agar valid supplier-part, supplier-project aur part-project combinations independent constraints se represent ho sakte hain, to three-way relation ko smaller relations mein decompose kiya ja sakta hai.

**Important:** Sirf tables ko chhota kar dena 5NF nahi hota. Decomposition lossless honi chahiye aur original valid tuples extra incorrect combinations ke bina reconstruct hone chahiye.

---

## 11. Normal Forms Comparison

| Normal Form | Main Rule                                                             |
| ----------- | --------------------------------------------------------------------- |
| 1NF         | Atomic values, no repeating groups                                    |
| 2NF         | 1NF + no partial dependency of non-prime attributes                   |
| 3NF         | 2NF + formal 3NF FD condition; commonly removes transitive dependency |
| BCNF        | Every determinant of non-trivial FD is a superkey                     |
| 4NF         | BCNF + no non-trivial MVD unless determinant is superkey              |
| 5NF         | Non-trivial join dependencies are implied by candidate keys           |

### Easy Memory Trick

- 1NF → Atomic values
- 2NF → Full dependency
- 3NF → No improper transitive dependency
- BCNF → Every determinant is a superkey
- 4NF → Multivalued dependency
- 5NF → Join dependency

---

## 12. Lossless and Lossy Decomposition

Normalization mein table ko multiple tables mein divide kiya jata hai. Is process ko decomposition kehte hain.

### A. Lossless Decomposition

Agar decomposed tables ko JOIN karne par exactly original relation recover ho jaye, without extra incorrect rows, to decomposition lossless hai.

### B. Lossy Decomposition

Agar JOIN karne par extra incorrect combinations (spurious tuples) aa jayein ya original relation accurately recover na ho, to decomposition lossy hai.

**Remember:** Good normalization decomposition lossless honi chahiye.

---

## 13. Dependency Preservation

Agar decomposition ke baad original functional dependencies ko individual tables par constraints laga kar enforce kiya ja sake, without needing to JOIN tables, to decomposition dependency-preserving kehlati hai.

### Important

- Lossless decomposition: Original information safely recover ho.
- Dependency preservation: Dependencies efficiently enforce ho sakein.

Dono alag properties hain. Har lossless decomposition dependency-preserving ho, ye guaranteed nahi hai.

---

## 14. Normalization vs Denormalization

| Normalization               | Denormalization                                   |
| --------------------------- | ------------------------------------------------- |
| Data organize karna         | Selected data duplicate/store karna               |
| Redundancy reduce           | Read performance improve karne ke liye redundancy |
| Update consistency improve  | Updates complex ho sakte hain                     |
| More tables possible        | Fewer joins possible                              |
| Write consistency important | Read-heavy systems mein useful                    |

### Denormalization kab use hoti hai?

- Read-heavy applications.
- Reporting systems.
- Analytics.
- Jab JOIN performance measured bottleneck ho.
- Jab carefully controlled duplicate data useful ho.

**Important:** Denormalization bina reason ke nahi karni chahiye. Duplicate data ko consistent rakhne ka plan hona chahiye.

---

## 15. Normalization in MERN / MongoDB

MongoDB document database hai. Isme relational normalization ka exact same table-based process apply nahi hota, lekin data modeling ke principles similar hain.

### Embedding

Related data ko same document mein store karna.

```javascript
{
    _id: 1,
    name: "Rahul",
    address: {
        city: "Delhi",
        pincode: 110001
    }
}
```

Useful jab:

- Data frequently together read hota ho.
- Relationship one-to-one ya bounded one-to-few ho.
- Related data ka size manageable ho.

### Referencing

Related data ko separate collections mein store karke IDs se connect karna.

**Students**

```javascript
{
    _id: 1,
    name: "Rahul",
    departmentId: 10
}
```

**Departments**

```javascript
{
    _id: 10,
    name: "Computer Science"
}
```

Useful jab:

- Data shared ho.
- Relationship many-to-many ho.
- Related data independently update hota ho.
- Embedded data bahut large ya unbounded ho.

**Interview Point:** MongoDB mein embedding aur referencing ka decision access patterns, data size, update frequency aur consistency requirements ke basis par hota hai.

---

## 16. Common Mistakes

1. 1NF ko sirf primary key hona samajhna.
2. 2NF mein partial dependency ka concept ignore karna.
3. 3NF aur BCNF ko same samajhna.
4. Har transitive dependency ko bina formal FD rules dekhe 3NF violation declare karna.
5. BCNF mein determinant superkey rule bhoolna.
6. 4NF ko multivalued dependency se connect na karna.
7. 5NF ko sirf table splitting samajhna.
8. Lossless aur dependency-preserving decomposition ko same samajhna.
9. Ye assume karna ki har database ko maximum normalization chahiye.
10. MongoDB mein relational rules ko exactly same tarah apply karna.

---

## 17. Interview Questions and Answers

**Q1. What is normalization?**

Normalization is a database design process that organizes data to reduce redundancy and prevent anomalies.

**Q2. What are database anomalies?**

Insertion, Update and Deletion anomalies.

**Q3. What is 1NF?**

Every cell should contain an atomic value and repeating groups should be removed.

**Q4. What is 2NF?**

A relation must be in 1NF and every non-prime attribute must be fully functionally dependent on every candidate key.

**Q5. What is partial dependency?**

When a non-prime attribute depends on a proper subset of a composite candidate key.

**Q6. What is transitive dependency?**

An indirect dependency, such as A → B and B → C, where A determines C through B.

**Q7. What is 3NF?**

For every non-trivial FD X → A, X must be a superkey or A must be a prime attribute.

**Q8. What is BCNF?**

Every determinant in a non-trivial functional dependency must be a superkey.

**Q9. Which normal form handles multivalued dependency?**

4NF.

**Q10. What is 5NF?**

It handles non-trivial join dependencies that are not implied by candidate keys.

**Q11. What is lossless decomposition?**

Decomposition in which joining the resulting relations reconstructs exactly the original relation.

**Q12. What is denormalization?**

Intentionally introducing controlled redundancy to improve selected read performance or simplify queries.

---

## 18. Practical Tasks

1. Ek unnormalized student-course table banao aur use 1NF mein convert karo.
2. Composite key wali table mein partial dependency identify karke 2NF apply karo.
3. Student aur department data se transitive dependency identify karke 3NF apply karo.
4. Given functional dependencies se candidate keys find karo.
5. Kisi relation ke liye check karo ki woh BCNF satisfy karta hai ya nahi.
6. Lossless aur lossy decomposition ke examples samjho.
7. MongoDB mein embedding aur referencing ke examples banao.

---

## 19. Quick Revision

- Normalization = Better database organization.
- Main goal = Redundancy aur anomalies reduce karna.
- Anomalies = Insertion, Update, Deletion.
- FD = Functional Dependency.
- 1NF = Atomic values.
- 2NF = No partial dependency of non-prime attributes.
- 3NF = No violation of formal 3NF condition.
- BCNF = Every determinant must be a superkey.
- 4NF = Multivalued dependency.
- 5NF = Join dependency.
- Lossless = Exact original relation recover.
- Dependency preservation = Dependencies separately enforce ho sakein.
- Denormalization = Controlled redundancy for specific performance needs.

---

## 20. MCQ Practice – 10 Questions

**Q1. Normalization ka main purpose kya hai?**

A. Data duplication badhana  
B. Data redundancy reduce karna  
C. Database delete karna  
D. CPU speed badhana

**Q2. 1NF mein kya required hai?**

A. Atomic values  
B. Multivalued cells  
C. Duplicate tables  
D. No primary key

**Q3. Partial dependency kis normal form mein remove ki jati hai?**

A. 1NF  
B. 2NF  
C. 4NF  
D. 5NF

**Q4. Transitive dependency commonly kis normal form se remove hoti hai?**

A. 1NF  
B. 2NF  
C. 3NF  
D. 4NF

**Q5. BCNF mein determinant kya hona chahiye?**

A. Foreign key only  
B. Superkey  
C. NULL  
D. Duplicate value

**Q6. Multivalued dependency kis normal form se related hai?**

A. 1NF  
B. 2NF  
C. 4NF  
D. 5NF

**Q7. 5NF ko aur kis naam se jana jata hai?**

A. First Normal Form  
B. Project-Join Normal Form  
C. Boyce-Codd Form  
D. Atomic Form

**Q8. Insertion, Update aur Deletion kya hain?**

A. SQL commands  
B. Database anomalies  
C. Keys  
D. Data types

**Q9. Lossless decomposition ka meaning kya hai?**

A. Data permanently delete hona  
B. Original relation accurately recover hona  
C. Data duplicate hona  
D. Database lock hona

**Q10. Denormalization ka purpose kya ho sakta hai?**

A. Controlled redundancy se read performance improve karna  
B. Har table delete karna  
C. Primary key remove karna  
D. Database ko corrupt karna

### Answer Key

1-B, 2-A, 3-B, 4-C, 5-B, 6-C, 7-B, 8-B, 9-B, 10-A

---

**Topic 14 Complete – DBMS Normalization.**
