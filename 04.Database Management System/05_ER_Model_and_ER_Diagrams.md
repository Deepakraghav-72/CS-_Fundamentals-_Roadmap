# Topic 05 – ER Model and ER Diagrams in DBMS

## 1. ER Model Kya Hota Hai?

ER ka full form **Entity Relationship** hai.

ER Model ek conceptual data model hai jiska use database ka design banane ke liye kiya jata hai.

Ismein hum real-world objects, unki properties aur unke beech relationships ko represent karte hain.

Simple words mein:

ER Model batata hai ki database mein kaun-kaun si entities hongi, unke attributes kya honge aur entities ek doosre se kaise connected hongi.

### Example

Maan lo hume College Database design karna hai.

Ismein:

- Student
- Teacher
- Course
- Department

Ye sab entities ho sakti hain.

Student ke attributes:

- Student_ID
- Name
- Email
- Age

Student aur Course ke beech relationship:

- Student ENROLLS IN Course.

## 2. ER Diagram Kya Hota Hai?

ER Diagram ek graphical representation hai jo ER Model ko diagram ke form mein show karta hai.

Ismein different symbols ka use hota hai:

- Rectangle = Entity
- Oval = Attribute
- Diamond = Relationship
- Underlined Attribute = Key Attribute
- Double Oval = Multivalued Attribute
- Dashed Oval = Derived Attribute

### Basic ER Diagram

```text
       (Student_ID)
            |
         [STUDENT]
            |
          (Name)
```

Yahan:

- STUDENT = Entity
- Student_ID = Attribute
- Name = Attribute

Note: Diagram mein `[STUDENT]` ko rectangle aur `(Name)` ko oval represent karta hai. Ye ASCII representation hai.

## 3. Entity Kya Hoti Hai?

Entity koi real-world object, person, place ya concept hoti hai jiske baare mein database mein information store karni hoti hai.

### Examples

| Entity     | Meaning                |
| ---------- | ---------------------- |
| Student    | Student ki information |
| Teacher    | Teacher ki information |
| Employee   | Employee details       |
| Product    | Product details        |
| Customer   | Customer information   |
| Department | Department details     |

### Entity Ka Symbol

ER Diagram mein Entity ko Rectangle se represent kiya jata hai.

```text
+-------------+
|   STUDENT   |
+-------------+
```

## 4. Types of Entity

Entity ke two important types hote hain:

1. Strong Entity
2. Weak Entity

### A. Strong Entity

Strong Entity wo entity hoti hai jo apne attributes ke through independently identify ki ja sakti hai.

Iski apni primary key hoti hai.

Example:

```text
+------------------+
|     STUDENT      |
+------------------+
| Student_ID (PK)  |
| Name             |
| Email            |
+------------------+
```

Yahan Student_ID student ko uniquely identify karta hai.

**Symbol:** Single Rectangle.

### B. Weak Entity

Weak Entity wo entity hoti hai jise apne attributes ke through independently uniquely identify nahi kiya ja sakta.

Iski identification kisi owner/strong entity ki key aur apne partial key ke combination se hoti hai.

Example:

Ek Employee ke multiple Dependents ho sakte hain.

Dependent ko identify karne ke liye Employee_ID aur Dependent_Name ka combination use kiya ja sakta hai.

```text
+-------------+       +================+
|  EMPLOYEE   |-------||   DEPENDENT    ||
+-------------+       +================+
| Employee_ID |       | Dependent_Name |
| Name        |       | Age            |
+-------------+       +================+
```

**Symbol:**

- Weak Entity = Double Rectangle.
- Identifying Relationship = Double Diamond.
- Partial Key = Commonly dashed underline.

Important: Weak entity ki identification owner entity ki key aur partial key se hoti hai.

## 5. Attribute Kya Hota Hai?

Attribute kisi Entity ki property ya characteristic ko kehte hain.

Example:

Student Entity ke attributes:

- Student_ID
- Name
- Age
- Email
- Phone

### Symbol

Attribute ko Oval se represent kiya jata hai.

```text
       (Name)
          |
      [STUDENT]
          |
       (Email)
```

## 6. Types of Attributes

ER Model mein attributes ke different types hote hain.

### A. Simple Attribute

Simple Attribute wo hota hai jise further meaningful parts mein divide nahi kiya ja sakta.

Examples:

- Age
- Salary
- Gender

### B. Composite Attribute

Composite Attribute ko smaller meaningful attributes mein divide kiya ja sakta hai.

Example:

Name:

- First_Name
- Middle_Name
- Last_Name

Address:

- House_Number
- City
- State
- PIN_Code

```text
              (Name)
             /  |  \
            /   |   \
       (First)(Middle)(Last)
```

### C. Single-Valued Attribute

Aisa attribute jiske liye ek entity ke paas normally ek hi value hoti hai.

Example:

- Date_of_Birth
- Roll_Number

### D. Multivalued Attribute

Aisa attribute jiske liye ek entity ke paas multiple values ho sakti hain.

Example:

Ek student ke multiple phone numbers ho sakte hain.

```text
       ((Phone_Number))
               |
          [STUDENT]
```

**Symbol:** Double Oval.

### E. Derived Attribute

Derived Attribute wo hota hai jiski value kisi doosre attribute se calculate ki ja sakti hai.

Example:

Date_of_Birth se Age calculate karna.

```text
        - - (Age) - -
               |
          [STUDENT]
               |
        (Date_of_Birth)
```

**Symbol:** Dashed Oval.

Note: Age time ke saath change hoti hai, isliye current age ko birth date se calculate karna generally better hota hai.

### F. Key Attribute

Key Attribute entity ke kisi record ko uniquely identify karne mein help karta hai.

Example:

Student_ID.

**Symbol:** Attribute ke naam ke neeche underline.

```text
      (Student_ID)
      ____________
            |
        [STUDENT]
```

### Attribute Types – Quick Table

| Attribute     | Meaning                        | Example    |
| ------------- | ------------------------------ | ---------- |
| Simple        | Further divide nahi hota       | Age        |
| Composite     | Parts mein divide ho sakta hai | Name       |
| Single-Valued | One value                      | DOB        |
| Multivalued   | Multiple values                | Phone      |
| Derived       | Calculate kiya ja sakta hai    | Age        |
| Key           | Unique identification          | Student_ID |

## 7. Relationship Kya Hota Hai?

Relationship do ya more entities ke beech association ko represent karta hai.

Example:

Student aur Course ke beech relationship:

Student ENROLLS IN Course.

```text
+-----------+       <ENROLLS>       +----------+
|  STUDENT  |-----------------------|  COURSE  |
+-----------+                       +----------+
```

Yahan:

- STUDENT = Entity
- COURSE = Entity
- ENROLLS = Relationship

**Symbol:** Diamond.

## 8. Degree of Relationship

Degree batati hai ki ek relationship mein kitni entity types participate kar rahi hain.

Common types:

1. Unary Relationship
2. Binary Relationship
3. Ternary Relationship

### A. Unary Relationship

Jab same entity type ke records ke beech relationship ho.

Isse Recursive Relationship bhi kehte hain.

Example:

Employee manages Employee.

```text
       +------------+
       |  EMPLOYEE  |
       +------------+
          ^     |
          |     |
          +-----+
          MANAGES
```

Example:

Ek employee doosre employee ko manage karta hai.

### B. Binary Relationship

Jab two entity types ke beech relationship ho.

Example:

Student enrolls in Course.

```text
+-----------+       <ENROLLS>       +----------+
|  STUDENT  |-----------------------|  COURSE  |
+-----------+                       +----------+
```

Ye commonly used relationship degree hai.

### C. Ternary Relationship

Jab three entity types ek hi relationship mein participate karti hain.

Example:

Supplier supplies Product to Project.

```text
              +-----------+
              | SUPPLIER  |
              +-----------+
                    |
                    |
              <SUPPLIES>
              /        \
             /          \
    +---------+        +---------+
    | PRODUCT |        | PROJECT |
    +---------+        +---------+
```

Yahan ek relationship mein three entity types participate karti hain.

## 9. Cardinality Ratio

Cardinality batati hai ki ek entity ke kitne records doosri entity ke records se associated ho sakte hain.

Four common cardinality types:

1. One-to-One (1:1)
2. One-to-Many (1:N)
3. Many-to-One (N:1)
4. Many-to-Many (M:N)

### A. One-to-One (1:1)

Ek entity ka ek record doosri entity ke maximum ek record se related hota hai, aur reverse direction mein bhi maximum one.

Example:

Person aur Passport.

```text
+--------+       1 : 1       +----------+
| PERSON |------------------| PASSPORT |
+--------+                  +----------+
```

### B. One-to-Many (1:N)

Ek entity ka ek record doosri entity ke multiple records se related ho sakta hai.

Example:

One Department has many Employees.

```text
+------------+       1 : N       +----------+
| DEPARTMENT |-------------------| EMPLOYEE |
+------------+                   +----------+
```

Ek department mein multiple employees ho sakte hain.

### C. Many-to-One (N:1)

Multiple records ek single record se associated ho sakte hain.

Example:

Multiple employees belong to one department.

```text
+----------+       N : 1       +------------+
| EMPLOYEE |------------------| DEPARTMENT |
+----------+                  +------------+
```

Ye One-to-Many ka reverse perspective hai.

### D. Many-to-Many (M:N)

Ek entity ke multiple records doosri entity ke multiple records se associated ho sakte hain.

Example:

Students aur Courses.

```text
+-----------+       M : N       +----------+
|  STUDENT  |-------------------|  COURSE  |
+-----------+                   +----------+
```

- Ek student multiple courses mein enroll ho sakta hai.
- Ek course mein multiple students enroll ho sakte hain.

### Cardinality Comparison

| Cardinality | Meaning      | Example              |
| ----------- | ------------ | -------------------- |
| 1:1         | One to One   | Person–Passport      |
| 1:N         | One to Many  | Department–Employees |
| N:1         | Many to One  | Employees–Department |
| M:N         | Many to Many | Students–Courses     |

## 10. Participation Constraints

Participation batati hai ki kisi relationship mein entity ke records ka participate karna compulsory hai ya optional.

Iske two types hain:

### A. Total Participation

Jab entity set ke har entity instance ko relationship mein participate karna compulsory ho.

Example:

Agar rule hai ki har employee kisi department se belong karega, to Employee ki Department relationship mein total participation hogi.

**Symbol:** Double Line.

```text
+----------+  ═════  <WORKS IN>
| EMPLOYEE |
+----------+
```

### B. Partial Participation

Jab relationship mein participate karna optional ho.

Example:

Har employee ko project assign hona compulsory nahi hai.

**Symbol:** Single Line.

```text
+----------+  ─────  <WORKS ON>
| EMPLOYEE |
+----------+
```

### Total vs Partial Participation

| Total Participation                | Partial Participation                     |
| ---------------------------------- | ----------------------------------------- |
| Participation compulsory           | Participation optional                    |
| Double line                        | Single line                               |
| Every entity instance participates | Some entity instances may not participate |

Important: Participation constraint aur cardinality ratio alag concepts hain.

## 11. ER Diagram Ka Complete Example

Maan lo hume College Database design karna hai.

Entities:

- STUDENT
- COURSE

Attributes:

**STUDENT:**

- Student_ID
- Name
- Email

**COURSE:**

- Course_ID
- Course_Name

Relationship:

- ENROLLS

Cardinality:

- Many-to-Many.

### Conceptual Diagram

```text
   (Student_ID)              (Course_ID)
        |                         |
        |                         |
   +----------+               +----------+
   | STUDENT  |               |  COURSE  |
   +----------+               +----------+
        |                         |
        +-------< ENROLLS >-------+
                  M : N
```

## 12. ER Diagram Ko Relational Tables Mein Convert Karna

ER Model conceptual design ke liye hota hai. Relational database banate waqt ise tables mein convert kiya ja sakta hai.

Example:

STUDENT aur COURSE ke beech Many-to-Many relationship hai.

Isko represent karne ke liye junction table banate hain.

### Students Table

| Student_ID (PK) | Name  |
| --------------- | ----- |
| 101             | Rahul |
| 102             | Amit  |

### Courses Table

| Course_ID (PK) | Course_Name |
| -------------- | ----------- |
| C01            | BCA         |
| C02            | BBA         |

### Enrollments Table

| Student_ID (FK) | Course_ID (FK) |
| --------------- | -------------- |
| 101             | C01            |
| 101             | C02            |
| 102             | C01            |

Yahan:

- Students table mein Student_ID primary key hai.
- Courses table mein Course_ID primary key hai.
- Enrollments table dono tables ko connect karti hai.
- Enrollments mein dono columns foreign keys hain.
- In dono columns ka combination composite primary key ban sakta hai.

## 13. Extended ER Model (EER Model)

EER ka full form **Enhanced Entity Relationship Model** hai.

Ye traditional ER Model ka extended version hai.

Ismein additional concepts use hote hain:

- Specialization
- Generalization
- Inheritance
- Aggregation
- Categories

### A. Specialization

Specialization top-down approach hai.

Ek general entity ko specific sub-entities mein divide kiya jata hai.

Example:

```text
          EMPLOYEE
              |
        -------------
        |           |
      MANAGER     DEVELOPER
```

Employee ek general entity hai.

Manager aur Developer uske specialized subtypes hain.

### B. Generalization

Generalization bottom-up approach hai.

Multiple similar entities ko combine karke ek common higher-level entity banayi jati hai.

Example:

```text
       CAR          BIKE
         \          /
          \        /
           VEHICLE
```

Car aur Bike ko combine karke Vehicle general entity banayi ja sakti hai.

### Specialization vs Generalization

| Specialization                      | Generalization                      |
| ----------------------------------- | ----------------------------------- |
| Top-down approach                   | Bottom-up approach                  |
| General entity se specific entities | Specific entities se general entity |
| Employee → Manager, Developer       | Car, Bike → Vehicle                 |

### C. Inheritance

Subtype apne supertype ke attributes aur relationships inherit kar sakta hai.

Example:

Employee ke attributes:

- Employee_ID
- Name

Manager subtype in attributes ke saath apne additional attributes bhi rakh sakta hai.

### D. Aggregation

Aggregation mein kisi relationship ko higher-level entity ki tarah treat karke uska doosri entity ke saath relationship represent kiya jata hai.

Ye complex relationships ko model karne mein useful hai.

## 14. ER Model Ke Advantages

1. Database design visually understandable hota hai.
2. Entities aur relationships clearly identify hote hain.
3. Database development se pehle structure plan kar sakte hain.
4. Developers aur designers ke beech communication easy hota hai.
5. Missing entities aur relationships identify karne mein help milti hai.
6. Relational schema banane ke liye useful starting point hai.

## 15. ER Model Ki Limitations

1. Large databases ke ER diagrams complex ho sakte hain.
2. Complex business rules ko simple ER diagram mein represent karna difficult ho sakta hai.
3. ER diagram actual physical storage details show nahi karta.
4. Diagram banane ke baad relational schema mein conversion aur constraints define karne padte hain.
5. Different diagramming notations ki wajah se symbols ka presentation vary kar sakta hai.

## 16. MERN Developer Ke Liye ER Model Kyon Important Hai?

MERN stack mein MongoDB use karte waqt bhi database design samajhna important hai.

Example: E-commerce application.

Entities:

- User
- Product
- Order
- Payment

Relationships:

- User places Order.
- Order contains Products.
- Order has Payment.

ER Model ki help se pehle data structure aur relationships plan kar sakte ho.

Uske baad decide kar sakte ho ki MongoDB mein:

- Embedded documents use karne hain.
- References use karne hain.
- Collections kaise organize karni hain.

Important: MongoDB document database hai, lekin ER modeling ke concepts database design samajhne mein phir bhi useful hain.

## 17. Important Interview Questions

**Q1. ER Model kya hai?**

ER Model ek conceptual data model hai jo entities, attributes aur relationships represent karta hai.

**Q2. ER Diagram kya hota hai?**

ER Diagram ER Model ka graphical representation hota hai.

**Q3. Entity kya hoti hai?**

Entity real-world object ya concept hoti hai jiske baare mein data store karte hain.

**Q4. Attribute kya hota hai?**

Attribute entity ki property hoti hai.

**Q5. Strong Entity kya hai?**

Aisi entity jiske paas apni primary key hoti hai aur jo independently identify ho sakti hai.

**Q6. Weak Entity kya hai?**

Aisi entity jise identify karne ke liye owner entity ki key aur partial key ki zaroorat hoti hai.

**Q7. Composite Attribute kya hai?**

Aisa attribute jise smaller meaningful attributes mein divide kiya ja sakta hai.

**Q8. Derived Attribute kya hai?**

Aisa attribute jiski value kisi doosre attribute se calculate ki ja sakti hai.

**Q9. Multivalued Attribute kya hai?**

Aisa attribute jiske liye ek entity ki multiple values ho sakti hain.

**Q10. Cardinality kya hai?**

Cardinality relationship mein entities ke beech possible record associations ki quantity batati hai.

**Q11. Total Participation kya hai?**

Jab entity set ke har instance ko relationship mein participate karna compulsory ho.

**Q12. Partial Participation kya hai?**

Jab relationship mein participation optional ho.

**Q13. Binary Relationship kya hai?**

Jab two entity types relationship mein participate karti hain.

**Q14. Ternary Relationship kya hai?**

Jab three entity types ek relationship mein participate karti hain.

**Q15. Specialization aur Generalization mein difference kya hai?**

Specialization top-down approach hai, jabki Generalization bottom-up approach hai.

**Q16. Many-to-Many relationship ko relational tables mein kaise implement karte hain?**

Generally junction table banakar, jisme related tables ki foreign keys hoti hain.

## 18. Common Mistakes

1. Entity aur Attribute ko same samajhna.
2. Relationship ko attribute samajhna.
3. Strong Entity aur Weak Entity confuse karna.
4. Composite aur Multivalued Attribute ko same samajhna.
5. Derived Attribute ko stored attribute samajhna.
6. Cardinality aur Participation ko same samajhna.
7. Binary aur Ternary relationship confuse karna.
8. Many-to-Many relationship ko relational database mein directly ek foreign key se represent karne ki koshish karna.
9. Specialization aur Generalization ka direction bhool jana.
10. Ye samajhna ki ER Diagram physical database storage show karta hai.

## 19. Quick Revision

- ER = Entity Relationship.
- ER Model = Conceptual database design.
- ER Diagram = Graphical representation.
- Entity = Real-world object.
- Attribute = Entity ki property.
- Relationship = Entities ke beech association.
- Strong Entity = Independent identification.
- Weak Entity = Owner key + Partial key.
- Simple Attribute = Further meaningful division nahi.
- Composite Attribute = Multiple meaningful parts.
- Single-Valued = One value.
- Multivalued = Multiple values.
- Derived = Calculated value.
- Key Attribute = Unique identification.
- Unary = One entity type.
- Binary = Two entity types.
- Ternary = Three entity types.
- 1:1 = One-to-One.
- 1:N = One-to-Many.
- M:N = Many-to-Many.
- Total Participation = Compulsory.
- Partial Participation = Optional.
- Specialization = Top-down.
- Generalization = Bottom-up.

## 20. Practical Tasks

1. Student Entity ke 5 attributes identify karo.
2. Strong Entity aur Weak Entity ka diagram banao.
3. Simple, Composite aur Multivalued attributes ke examples likho.
4. Student aur Course ke beech Many-to-Many ER Diagram banao.
5. Department aur Employee ke beech One-to-Many diagram banao.
6. Employee aur Manager ka Unary Relationship example banao.
7. Supplier, Product aur Project ka Ternary Relationship diagram banao.
8. Specialization aur Generalization ke diagrams banao.
9. Many-to-Many relationship ko Students, Courses aur Enrollments tables mein convert karo.
10. E-commerce application ke liye User, Product, Order aur Payment ka ER Model design karo.

## 21. Test Yourself – 10 MCQs

**Q1. ER ka full form kya hai?**

A. Entity Record  
B. Entity Relationship  
C. External Relation  
D. Entry Record

**Q2. ER Diagram mein Entity ko kaun sa symbol represent karta hai?**

A. Oval  
B. Diamond  
C. Rectangle  
D. Circle

**Q3. Attribute ko kaun sa symbol represent karta hai?**

A. Oval  
B. Rectangle  
C. Diamond  
D. Triangle

**Q4. Weak Entity ko kaise represent kiya jata hai?**

A. Single Rectangle  
B. Double Rectangle  
C. Single Oval  
D. Dashed Diamond

**Q5. Multivalued Attribute ka symbol kya hai?**

A. Double Oval  
B. Single Rectangle  
C. Diamond  
D. Dashed Line

**Q6. Student aur Course ke beech relationship generally kya ho sakta hai?**

A. One-to-One only  
B. Many-to-Many  
C. Unary only  
D. No relationship

**Q7. Jab three entity types ek relationship mein participate karti hain, use kya kehte hain?**

A. Unary  
B. Binary  
C. Ternary  
D. Simple

**Q8. Total Participation ko kaise show karte hain?**

A. Single Line  
B. Double Line  
C. Dashed Oval  
D. Double Rectangle

**Q9. Specialization ka approach kya hai?**

A. Bottom-up  
B. Top-down  
C. Random  
D. Physical

**Q10. Many-to-Many relationship ko relational database mein generally kaise implement karte hain?**

A. Junction Table  
B. Single Attribute  
C. Delete Table  
D. Index Only

### Answer Key

1. B
2. C
3. A
4. B
5. A
6. B
7. C
8. B
9. B
10. A

---

**Topic 05 Complete – ER Model and ER Diagrams**
