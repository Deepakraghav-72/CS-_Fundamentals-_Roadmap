# Topic 04 – Data Models in DBMS

## 1. Data Model Kya Hota Hai?

Data Model rules aur concepts ka collection hota hai jo define karta hai ki database mein data ko kaise organize, store, represent aur relate kiya jayega.

Simple words mein:

Data Model database ka blueprint hota hai, jo batata hai ki data ka structure kaisa hoga aur data ke beech relationship kaise banega.

### Example

Maan lo hum ek College Database bana rahe hain.

Ismein hume store karna hai:

- Students
- Teachers
- Courses
- Departments
- Marks

Data Model decide karne mein help karega ki in sabhi information ko kaise organize karna hai.

## 2. Data Model Ki Need Kyon Hoti Hai?

Data Model ki help se:

1. Database ka structure plan kar sakte hain.
2. Data ke beech relationships define kar sakte hain.
3. Data duplication reduce karne mein help milti hai.
4. Data consistency maintain karne mein help milti hai.
5. Database design understandable banta hai.
6. Developers aur database designers ke beech communication easy hota hai.

## 3. Types of Data Models

DBMS mein commonly ye data models padhe jate hain:

1. Hierarchical Data Model
2. Network Data Model
3. Relational Data Model
4. Entity-Relationship (ER) Model
5. Object-Oriented Data Model
6. Object-Relational Data Model
7. Document Data Model
8. Key-Value Data Model
9. Graph Data Model

Inhe detail mein samajhte hain.

## 4. Hierarchical Data Model

Hierarchical Data Model mein data tree-like structure mein organize hota hai.

Ismein parent-child relationship hota hai.

Ek parent ke multiple children ho sakte hain, lekin traditional hierarchical model mein ek child ka generally ek hi parent hota hai.

### Diagram

```text
              College
                 |
        -------------------
        |                 |
     Students          Teachers
        |                 |
    ---------          Subjects
    |       |
  Rahul   Amit
```

### Characteristics

- Tree-like structure.
- Parent-child relationship.
- One-to-many relationship naturally represent karta hai.
- Navigation generally hierarchical paths ke through hoti hai.

### Advantages

- Simple tree structure.
- One-to-many data ke liye useful.
- Predictable navigation.

### Disadvantages

- Many-to-many relationships represent karna difficult.
- Structure changes complex ho sakte hain.
- Parent-dependent structure hota hai.

### Example

IBM IMS ek historical aur established hierarchical database system ka example hai.

## 5. Network Data Model

Network Data Model mein data graph-like structure mein organize hota hai.

Ismein ek record multiple records se connected ho sakta hai.

Ek child ke multiple parent records ho sakte hain.

### Diagram

```text
       Student A
        /     \
       /       \
   Course 1   Course 2
       \       /
        \     /
       Student B
```

Yahan students multiple courses se connected ho sakte hain.

### Characteristics

- Graph-like structure.
- Multiple relationships support karta hai.
- Many-to-many relationships represent kar sakta hai.
- Records ke beech links/pointers use ho sakte hain.

### Advantages

- Complex relationships represent kar sakta hai.
- Multiple connections support karta hai.
- Certain navigation operations efficient ho sakte hain.

### Disadvantages

- Design complex hota hai.
- Structure maintain karna difficult ho sakta hai.
- Changes ke liye careful management chahiye.

## 6. Relational Data Model

Relational Data Model mein data tables ke form mein organize hota hai.

Tables ko relations bhi kaha jata hai.

Har table mein:

- Rows hoti hain.
- Columns hote hain.
- Har column ek attribute represent karta hai.
- Har row ek record/tuple represent karti hai.

### Example

**Students Table**

| Student_ID | Name  | Course_ID |
| ---------- | ----- | --------- |
| 101        | Rahul | C01       |
| 102        | Amit  | C02       |
| 103        | Priya | C01       |

**Courses Table**

| Course_ID | Course_Name |
| --------- | ----------- |
| C01       | BCA         |
| C02       | BBA         |

Yahan `Course_ID` ke through tables ke beech relationship establish kiya ja sakta hai.

### Characteristics

- Data tables mein organize hota hai.
- Rows aur columns use hote hain.
- Primary keys records identify karti hain.
- Foreign keys tables ke beech relationships establish kar sakti hain.
- SQL commonly use hoti hai.

### Examples

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server

### Advantages

- Easy to understand.
- SQL ke through data retrieve karna convenient.
- Data integrity constraints support karta hai.
- Relationships aur joins support karta hai.

### Disadvantages

- Complex joins performance impact kar sakte hain.
- Highly flexible/unstructured data ke liye additional design effort lag sakta hai.
- Large-scale workloads mein proper indexing aur optimization important hoti hai.

## 7. Entity-Relationship (ER) Model

ER Model database ko entities, attributes aur relationships ke form mein represent karta hai.

Iska use database design aur ER diagrams banane mein hota hai.

### Main Components

**1. Entity**

Real-world object ya concept jiske baare mein data store karna hai.

Examples:

- Student
- Teacher
- Course
- Employee

**2. Attribute**

Entity ki property ko attribute kehte hain.

Student ke attributes:

- Student_ID
- Name
- Age
- Email

**3. Relationship**

Do ya more entities ke beech association ko relationship kehte hain.

Example:

```text
STUDENT -------- ENROLLS IN -------- COURSE
```

### Characteristics

- Conceptual database design mein useful.
- Entities aur relationships ko visualize karta hai.
- Database structure samajhna easy banata hai.

### Example

```text
+-----------+        +-----------+
|  STUDENT  |        |  COURSE   |
+-----------+        +-----------+
| StudentID |        | CourseID  |
| Name      |        | CourseName|
| Email     |        | Duration  |
+-----------+        +-----------+
       \                  /
        \                /
         \--- ENROLLS ---/
```

ER Model ko next topic mein detail mein padhenge.

## 8. Object-Oriented Data Model

Object-Oriented Data Model mein data objects ke form mein represent hota hai.

Ismein object-oriented programming ke concepts use ho sakte hain:

- Objects
- Classes
- Attributes
- Methods
- Inheritance
- Encapsulation

### Example

```text
Class: Student

Attributes:
- studentId
- name
- course

Methods:
- getDetails()
- updateDetails()
```

### Characteristics

- Objects ke form mein data representation.
- Complex data types support.
- Object-oriented concepts ka use.
- Complex objects ko represent karne mein useful.

## 9. Object-Relational Data Model

Object-Relational Data Model relational database model ko object-oriented features ke saath combine karta hai.

Ismein relational tables ke saath additional complex data types aur object-related capabilities support ho sakti hain.

Example:

PostgreSQL object-relational features provide karta hai.

### Characteristics

- Relational model ka foundation.
- User-defined types support ho sakte hain.
- Complex data representation.
- SQL ke saath additional object-related features.

## 10. Document Data Model

Document Data Model mein data documents ke form mein store hota hai.

Documents commonly JSON-like structure mein represent hote hain.

MongoDB BSON documents use karta hai.

### Example

```javascript
{
  _id: 101,
  name: "Rahul",
  course: "BCA",
  marks: 85,
  address: {
    city: "Meerut",
    state: "UP"
  }
}
```

### Characteristics

- Data documents mein store hota hai.
- Flexible document structure.
- Nested objects aur arrays support.
- Related information ek document mein embed ki ja sakti hai.

### Example Database

MongoDB.

### Advantages

- Flexible structure.
- JSON-like data ke saath convenient.
- Nested data represent karna easy.
- Application objects ke saath mapping convenient ho sakti hai.

### Disadvantages

- Data duplication ho sakta hai.
- Complex relationships ke liye careful design chahiye.
- Schema flexibility ka matlab data validation ki zaroorat khatam hona nahi hai.

## 11. Key-Value Data Model

Key-Value Model mein data key aur value ke pair mein store hota hai.

Har key apni corresponding value identify karti hai.

### Example

```javascript
{
  "user:101": "Rahul",
  "user:102": "Amit",
  "user:103": "Priya"
}
```

Yahan:

- Key = `user:101`
- Value = `Rahul`

### Characteristics

- Simple key-value pairs.
- Key ke through value access.
- Fast lookups ke liye useful.
- Caching aur session storage mein common.

### Examples

- Redis
- Amazon DynamoDB (key-value/document capabilities)

## 12. Graph Data Model

Graph Data Model mein data nodes aur edges ke form mein represent hota hai.

- Node = Entity
- Edge = Relationship

### Example: Social Media

```text
       Rahul
       /   \
      /     \
   FRIEND  FRIEND
    /         \
  Amit ------ Priya
       FRIEND
```

Yahan:

- Rahul, Amit aur Priya nodes hain.
- Friendship connections edges hain.

### Characteristics

- Highly connected data ke liye useful.
- Relationships directly represent karta hai.
- Complex relationship queries support karta hai.

### Examples

- Neo4j
- Amazon Neptune

## 13. Data Models Comparison

| Data Model        | Structure                    | Example / Use    |
| ----------------- | ---------------------------- | ---------------- |
| Hierarchical      | Tree                         | IBM IMS          |
| Network           | Graph-like linked records    | CODASYL systems  |
| Relational        | Tables                       | MySQL            |
| ER Model          | Entities and relationships   | Database design  |
| Object-Oriented   | Objects                      | Object databases |
| Object-Relational | Relational + object features | PostgreSQL       |
| Document          | Documents                    | MongoDB          |
| Key-Value         | Key-value pairs              | Redis            |
| Graph             | Nodes and edges              | Neo4j            |

Note: ER Model mainly conceptual design model hai. Document, key-value aur graph models commonly NoSQL database systems mein use hote hain.

## 14. Schema Aur Instance Kya Hote Hain?

Data Model samajhne ke baad Schema aur Instance samajhna bhi important hai.

### Schema

Schema database ka structure ya blueprint hota hai.

Example:

```sql
CREATE TABLE Students (
    id INT,
    name VARCHAR(50),
    marks INT
);
```

Ye table ka structure define karta hai.

### Instance

Instance kisi particular time par database mein stored actual data ko represent karta hai.

Example:

|  id | name  | marks |
| --: | ----- | ----: |
| 101 | Rahul |    85 |
| 102 | Amit  |    78 |

Ye table ka current data hai.

### Schema vs Instance

| Schema                    | Instance                       |
| ------------------------- | ------------------------------ |
| Database structure        | Actual stored data             |
| Comparatively stable      | Frequently change ho sakta hai |
| Blueprint                 | Current records                |
| Example: Table definition | Example: Table rows            |

## 15. Data Model vs Database Schema

| Data Model                            | Database Schema                          |
| ------------------------------------- | ---------------------------------------- |
| Data organize karne ke concepts/rules | Particular database ka defined structure |
| General design approach               | Specific database blueprint              |
| Example: Relational Model             | Example: Students and Courses tables     |

## 16. MERN Developer Ke Liye Data Models

MERN stack mein MongoDB document model use hota hai.

Example:

```javascript
const student = {
  name: "Rahul",
  email: "rahul@example.com",
  skills: ["HTML", "CSS", "JavaScript"],
  address: {
    city: "Meerut",
    state: "UP",
  },
};
```

MongoDB mein is type ka object BSON document ke form mein store kiya ja sakta hai.

Backend mein Mongoose use karte waqt schema define kar sakte hain:

```javascript
const studentSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
  },
  skills: [String],
});
```

Important:

- MongoDB ka document model aur Mongoose schema same cheez nahi hain.
- MongoDB documents store karta hai.
- Mongoose schema application-side structure aur validation define karne mein help karta hai.

## 17. Important Interview Questions

**Q1. Data Model kya hota hai?**

Data Model rules aur concepts ka collection hai jo database mein data ka structure aur relationships define karta hai.

**Q2. Data Model ki need kyon hoti hai?**

Database structure plan karne, relationships define karne aur data organization improve karne ke liye.

**Q3. Hierarchical Data Model kya hai?**

Tree-like structure jisme parent-child relationship hota hai.

**Q4. Network Data Model kya hai?**

Graph-like linked structure jisme records multiple records se connected ho sakte hain.

**Q5. Relational Data Model kya hai?**

Data ko tables, rows aur columns mein organize karne wala model.

**Q6. ER Model kya hai?**

Entities, attributes aur relationships ke through database design represent karne wala model.

**Q7. Document Data Model kya hai?**

Data ko documents ke form mein store karne wala model.

**Q8. MongoDB kaunsa data model use karta hai?**

Document Data Model.

**Q9. Redis kaunsa data model use karta hai?**

Primarily Key-Value Data Model.

**Q10. Graph Data Model mein Node aur Edge kya hain?**

Node entity ko aur Edge entities ke beech relationship ko represent karta hai.

**Q11. Schema kya hota hai?**

Database ka structure ya blueprint.

**Q12. Instance kya hota hai?**

Kisi particular time par database mein stored actual data.

## 18. Common Mistakes

1. Data Model aur Database Schema ko same samajhna.
2. ER Model ko actual database storage model samajhna.
3. MongoDB ko relational model kehna.
4. Hierarchical aur Network models ko same samajhna.
5. Node aur Edge ka meaning confuse karna.
6. Document aur Key-Value model ko same samajhna.
7. Schema ko actual records samajhna.
8. Schema flexibility ka matlab validation ki zaroorat nahi, aisa samajhna.

## 19. Quick Revision

- Data Model = Database ka design approach.
- Hierarchical = Tree structure.
- Network = Linked graph-like structure.
- Relational = Tables.
- ER = Entities + Attributes + Relationships.
- Object-Oriented = Objects and Classes.
- Object-Relational = Relational + Object features.
- Document = Documents.
- Key-Value = Key and Value pairs.
- Graph = Nodes and Edges.
- MongoDB = Document Model.
- Redis = Key-Value Model.
- Neo4j = Graph Model.
- Schema = Structure.
- Instance = Actual current data.

## 20. Practical Tasks

1. Hierarchical Data Model ka diagram banao.
2. Network Data Model ka diagram banao.
3. Student aur Course ke liye relational tables design karo.
4. Ek Student ka JSON-like document create karo.
5. Key-Value model ka example likho.
6. Social media ke liye Graph Model draw karo.
7. Schema aur Instance ka difference likho.
8. MongoDB aur MySQL ke data models compare karo.

## 21. Test Yourself – 10 MCQs

**Q1. Data Model kya define karta hai?**

A. Computer speed  
B. Data ka structure aur relationships  
C. Internet speed  
D. Operating System

**Q2. Hierarchical Model ka structure kaisa hota hai?**

A. Tree  
B. Table only  
C. Key-Value  
D. Flat file only

**Q3. Relational Model mein data kis form mein hota hai?**

A. Tables  
B. Images  
C. Audio  
D. Videos

**Q4. ER Model ke main components kaun se hain?**

A. HTML, CSS, JS  
B. Entity, Attribute, Relationship  
C. Node, CPU, RAM  
D. Key, Value only

**Q5. MongoDB ka primary data model kya hai?**

A. Hierarchical  
B. Document  
C. Network  
D. Relational

**Q6. Redis primarily kis model ka example hai?**

A. Key-Value  
B. Relational  
C. Hierarchical  
D. Object-Oriented

**Q7. Graph Model mein relationship ko kya represent karta hai?**

A. Node  
B. Edge  
C. Table  
D. Column

**Q8. Database Schema kya hota hai?**

A. Actual current records  
B. Database structure  
C. User password  
D. Network address

**Q9. Instance kya represent karta hai?**

A. Database ka blueprint  
B. Actual stored data at a particular time  
C. Programming language  
D. Database software only

**Q10. Neo4j kis model ka example hai?**

A. Graph  
B. Relational  
C. Hierarchical  
D. Key-Value

### Answer Key

1. B
2. A
3. A
4. B
5. B
6. A
7. B
8. B
9. B
10. A

---

**Topic 04 Complete – Data Models in DBMS**
