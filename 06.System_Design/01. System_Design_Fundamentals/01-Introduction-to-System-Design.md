# Topic 01: Introduction to System Design

## 1. What is System Design?

System Design ka matlab hota hai kisi software application ya system ko banane se pehle uska proper structure aur working plan taiyar karna.

Simple words mein:

**System Design = Planning how a software application will work.**

Jab hum koi application banate hain, toh humein pehle decide karna hota hai:

- Application kaise work karegi?
- Frontend aur Backend kaise connect honge?
- Data kahan store hoga?
- Users login kaise karenge?
- Application kitne users ko handle kar payegi?
- Agar server fail ho jaye toh kya hoga?
- Application ko fast aur secure kaise rakhenge?

In sabhi questions ke answers plan karna System Design kehlata hai.

### Real-Life Example: WhatsApp

Maan lo humein WhatsApp jaisi application banani hai.

Humein decide karna padega:

1. User account kaise create karega?
2. User kisi doosre user ko message kaise bhejega?
3. Messages database mein kaise save honge?
4. User offline hai toh message kaise deliver hoga?
5. Images aur videos kaise share hongi?
6. Ek saath millions of users message bhejein toh application kaise work karegi?

In sabhi problems ka solution design karna System Design hai.

---

## 2. Why Do We Need System Design?

System Design ki zarurat isliye hoti hai kyunki bina proper planning ke large applications banana aur maintain karna difficult ho sakta hai.

### Main Reasons:

**1. Scalability**

Application ko future mein badhne wale users handle karne layak banana.

Example: Aaj application par 1,000 users hain, kal 10 lakh ho sakte hain.

**2. Performance**

Application ko fast banana taaki user ko response jaldi mile.

Example: Instagram par photos aur posts jaldi load hon.

**3. Reliability**

Application ko consistently aur correctly work karna chahiye.

Example: Banking application transaction ke time fail na ho.

**4. Availability**

Application users ke liye available rahe, chahe kuch components fail ho jayein.

**5. Maintainability**

Application ke code aur architecture ko update karna easy hona chahiye.

**6. Security**

Users ka personal data, passwords aur transactions secure hone chahiye.

---

## 3. Main Components of a Software System

Ek normal web application ke kuch important components hote hain.

### 1. Client (Frontend)

Client wo part hota hai jiske through user application ke saath interact karta hai.

Examples:

- Website
- Mobile Application
- Desktop Application

MERN mein React frontend ka kaam karta hai.

### 2. Server (Backend)

Server client ki requests receive karta hai, business logic execute karta hai aur response send karta hai.

MERN mein:

- Node.js server-side JavaScript runtime hai.
- Express.js backend APIs banane mein help karta hai.

### 3. Database

Database application ka data store karta hai.

Examples:

- MongoDB
- MySQL
- PostgreSQL

MERN stack mein MongoDB use hota hai.

### 4. API

API client aur backend ke beech communication ka medium hoti hai.

Example:

React frontend login request bhejta hai aur Express backend us request ko process karta hai.

---

## 4. How Does a Basic System Work?

Maan lo user kisi website par login karta hai.

Working process:

1. User React website open karta hai.
2. User email aur password enter karta hai.
3. React backend ko API request bhejta hai.
4. Express server request receive karta hai.
5. Backend database mein user ko check karta hai.
6. Database result return karta hai.
7. Backend response frontend ko bhejta hai.
8. User ko login success ya error message dikhai deta hai.

### Basic Architecture Diagram

```text
       USER
         |
         v
   REACT FRONTEND
         |
         | API Request
         v
   EXPRESS SERVER
         |
         | Database Query
         v
      MONGODB
         |
         | Database Response
         v
   EXPRESS SERVER
         |
         | API Response
         v
   REACT FRONTEND
         |
         v
   USER GETS RESULT
```

Is process ko basic Client-Server Communication bhi kaha jata hai.

---

## 5. Important Characteristics of a Good System

Ek achhe software system mein ye characteristics honi chahiye:

| Characteristic  | Meaning                                           |
| --------------- | ------------------------------------------------- |
| Scalability     | Users badhne par system handle kar sake           |
| Reliability     | System correctly work kare                        |
| Availability    | System available rahe                             |
| Performance     | System fast response de                           |
| Security        | Data protected rahe                               |
| Maintainability | Changes karna easy ho                             |
| Fault Tolerance | Components fail hone par bhi system kaam kar sake |

In concepts ko hum aage detail mein padhenge.

---

## 6. Types of System Design

System Design ke do major parts hote hain:

### 1. LLD (Low Level Design)

LLD application ke internal structure aur code-level design par focus karta hai.

Ismein hum seekhte hain:

- Classes and Objects
- OOP Concepts
- SOLID Principles
- Design Patterns
- UML Diagrams

Example: ATM application mein Account class aur Transaction class kaise design hongi?

### 2. HLD (High Level Design)

HLD complete application ki overall architecture par focus karta hai.

Ismein hum seekhte hain:

- Servers
- Databases
- Load Balancers
- Caching
- Microservices
- Scalability

Example: ATM ya banking application ke servers, database aur services kaise communicate karengi?

**Difference:**

| LLD                     | HLD                        |
| ----------------------- | -------------------------- |
| Internal code structure | Overall architecture       |
| Classes and Objects     | Servers and Services       |
| OOP and Design Patterns | Scaling and Infrastructure |
| Detailed design         | Overall system design      |

---

## 7. System Design and MERN Stack Connection

MERN Developer ke liye System Design bahut useful hai.

| MERN Technology | System Design Connection   |
| --------------- | -------------------------- |
| React           | Client-side architecture   |
| Node.js         | Server-side architecture   |
| Express.js      | API Design                 |
| MongoDB         | Database Design            |
| Socket.io       | Real-time communication    |
| Redis           | Caching                    |
| JWT             | Authentication             |
| Cloud Services  | Deployment and Scalability |

Example:

Jab hum MERN se e-commerce application banate hain, toh System Design help karta hai decide karne mein:

- Products ka data kaise store hoga?
- Users ki requests kaise handle hongi?
- Payment service kaise connect hogi?
- Heavy traffic ko kaise manage karenge?

---

## 8. Real-World Examples of System Design

System Design ka use almost har large software application mein hota hai.

1. WhatsApp – Messaging system.
2. Instagram – Social media system.
3. YouTube – Video streaming system.
4. Netflix – Video delivery system.
5. Amazon – E-commerce system.
6. Uber – Ride booking system.
7. Google Drive – Cloud storage system.

Har application ki requirements aur architecture alag ho sakti hai.

---

## 9. Common Mistakes Beginners Make

1. Sirf coding par focus karna aur architecture ignore karna.
2. Database design ko properly na samajhna.
3. Application ki requirements clear kiye bina coding start karna.
4. Scalability aur security ko ignore karna.
5. Har application ke liye unnecessary microservices use karna.
6. System Design ko sirf diagrams banana samajhna.

**Remember:** Good System Design ka matlab unnecessarily complex architecture banana nahi hai. Requirements ke according simple aur effective solution choose karna hai.

---

## 10. Important Interview Questions

### Q1. What is System Design?

System Design is the process of planning the architecture, components, databases and communication of a software system.

### Q2. Why is System Design important?

It helps build scalable, reliable, secure, maintainable and high-performance applications.

### Q3. What are the two major types of System Design?

1. Low Level Design (LLD)
2. High Level Design (HLD)

### Q4. What is scalability?

Scalability is the ability of a system to handle increasing workload or users by adding resources.

### Q5. What is the difference between Client and Server?

Client sends requests to the server, and the server processes those requests and returns responses.

### Q6. What is the role of a database?

A database stores and manages application data.

### Q7. What is an API?

API is an interface that allows different software components to communicate with each other.

### Q8. Can we build a system without System Design?

Yes, small applications can be built with minimal planning, but proper design becomes increasingly important as complexity and scale grow.

---

## 11. Practical Tasks

### Task 1: Understand a Website

Kisi e-commerce website ko open karo aur identify karo:

- Frontend kya hai?
- Backend kya karta hoga?
- Database mein kya store hota hoga?
- API ka use kahan hota hoga?

### Task 2: Design a Basic Login System

Ek basic login system ka flow paper par banao:

User → Frontend → Backend → Database → Response

### Task 3: Think Like a Software Engineer

Socho agar tumhari application par ek din mein 10 lakh users aa jayein toh kya problems aa sakti hain?

Kam se kam 5 problems likho.

---

## 12. Quick Revision

- System Design = Software application ki planning aur architecture.
- Client = User-facing application.
- Server = Requests process karne wala system.
- Database = Data store karne ki jagah.
- API = Communication interface.
- LLD = Internal code-level design.
- HLD = Overall architecture design.
- Scalability = Increasing workload handle karne ki ability.
- Reliability = System ka consistently correct work karna.
- Availability = System ka accessible rehna.

---

## 13. Final Learning Check

Is topic ko complete karne ke baad tumhe ye samajh aana chahiye:

- System Design kya hai?
- Iski zarurat kyun padti hai?
- Client, Server, API aur Database kya hain?
- Basic application kaise work karti hai?
- LLD aur HLD mein kya difference hai?
- MERN aur System Design ka kya connection hai?

**Topic 01 Complete – Introduction to System Design**

Next Topic: Functional & Non-Functional Requirements.
