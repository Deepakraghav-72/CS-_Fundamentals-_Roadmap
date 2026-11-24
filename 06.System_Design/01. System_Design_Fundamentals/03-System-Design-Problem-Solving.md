# Topic 03: System Design Problem Solving Approach

## 1. System Design Problem Solving Approach Kya Hai?

System Design Problem Solving Approach ek step-by-step process hai jiske through hum kisi software system ko plan, design aur build karne ka solution nikalte hain.

Iska purpose hai:

- User ki requirements samajhna.
- System ke important components identify karna.
- Components ke beech communication decide karna.
- Database aur APIs ka basic plan banana.
- Performance, security aur scalability ko consider karna.
- System ke possible failures aur bottlenecks ko identify karna.

**Example:**

Agar interviewer kahe:

"Design a WhatsApp-like chat application."

To humein directly coding start nahi karni.

Pehle samajhna hoga:

- Users ek dusre ko message kaise bhejenge?
- Group chat support hogi?
- Online/offline messages kaise handle honge?
- Messages database mein kaise store honge?
- Bahut saare users ek saath message bhejein to system kaise handle karega?

In questions ke answers ke basis par hum system design karenge.

---

## 2. System Design Solve Karne Ka Complete Flow

System Design problem ko solve karne ke liye ek practical framework follow kar sakte hain.

### Step 1: Understand the Problem

Sabse pehle problem ko clearly samjho.

Identify karo:

- System kis purpose ke liye ban raha hai?
- Iska target user kaun hai?
- User system se kya expect karta hai?
- Main problem kya solve karni hai?

**Example:**

Question: Design an Instagram-like application.

Problem:
Users photos upload kar sakein, dusre users ki photos dekh sakein aur like/comment kar sakein.

### Step 2: Clarify Requirements

Requirements ko do categories mein divide karo:

**A. Functional Requirements**

System kya-kya karega?

Instagram example:

- User signup/login kar sake.
- User photo upload kar sake.
- User kisi ko follow kar sake.
- User posts dekh sake.
- User like aur comment kar sake.

**B. Non-Functional Requirements**

System kitni achhi quality se kaam karega?

Example:

- Fast response.
- High availability.
- Security.
- Scalability.
- Reliability.

**Important:** Har possible feature include karna zaroori nahi. Pehle core features decide karo.

### Step 3: Define Scope and Assumptions

System mein kya include hoga aur kya include nahi hoga, ye decide karo.

Example:

Instagram design ke liye initial scope:

- Signup/Login
- Photo upload
- Follow/Unfollow
- Feed
- Like/Comment

Out of scope:

- Video calling
- Live streaming
- Advanced AI recommendations

Assumptions bhi clearly mention karo.

Example:

- Initially mobile aur web clients honge.
- Users ke paas internet connection hoga.
- Images cloud storage mein store hongi.

Assumptions ko facts ki tarah present mat karo; ye design banane ke liye li gayi maan kar chalne wali conditions hain.

### Step 4: Identify Users and Main Components

System ke actors aur major components identify karo.

Instagram example:

Actors:

- User
- Admin

Main components:

- Client Application
- Backend Server
- Authentication Service
- Post Service
- Feed Service
- Database
- Image Storage

### Step 5: Estimate Scale (When Required)

System kitne users aur requests handle karega, iska rough estimate lagao.

Example assumptions:

- 1 million registered users.
- 100,000 daily active users.
- Har active user average 10 requests per day.

Daily requests:

100,000 × 10 = 1,000,000 requests/day

Average requests per second:

1,000,000 ÷ 86,400 ≈ 11.6 requests/second

Ye sirf average estimate hai. Real traffic peak hours mein isse kaafi zyada ho sakta hai.

**Scale estimation ka purpose:** Database, servers, storage aur network requirements samajhna.

### Step 6: Design High-Level Architecture

Ab system ke major components aur unke connections ka diagram banao.

Example:

```text
        User
          |
          v
     Frontend App
          |
          v
      Backend API
          |
    +-----+------+
    |            |
    v            v
  Database    Image Storage
```

Is example mein:

- Frontend user se input leta hai.
- Backend request process karta hai.
- Database structured information store karta hai.
- Image Storage photos store karta hai.

Ye ek basic architecture hai. Real system mein additional components ki zaroorat ho sakti hai.

### Step 7: Design APIs

Decide karo ki frontend aur backend kaise communicate karenge.

Example APIs:

| Method | Endpoint                 | Purpose         |
| ------ | ------------------------ | --------------- |
| POST   | /api/auth/signup         | Account create  |
| POST   | /api/auth/login          | Login           |
| POST   | /api/posts               | Post create     |
| GET    | /api/posts               | Posts fetch     |
| POST   | /api/posts/:id/like      | Like post       |
| GET    | /api/users/:id/followers | Followers fetch |

API design karte waqt request, response, authentication aur error handling bhi consider karo.

### Step 8: Design Database

Decide karo ki data kaise store hoga.

Example collections:

**Users**

- _id
- name
- email
- passwordHash

**Posts**

- _id
- userId
- imageUrl
- caption
- createdAt

**Comments**

- _id
- postId
- userId
- text
- createdAt

**Likes**

- _id
- postId
- userId

MERN connection: MongoDB mein in collections ko store kar sakte hain.

Database design mein relationships, indexes, data duplication aur query patterns ko bhi consider karna hota hai.

### Step 9: Identify Bottlenecks and Failure Points

Bottleneck ka matlab system ka woh part jo performance ko slow kar raha ho ya requests handle karne mein problem create kar raha ho.

Example:

- Bahut saari images load hone se response slow ho sakta hai.
- Database par excessive queries load badha sakti hain.
- Single server fail hone par application unavailable ho sakti hai.

Possible solutions:

- Caching
- CDN
- Database indexing
- Load balancing
- Replication

In concepts ko hum aage HLD topics mein detail se padhenge.

### Step 10: Consider Security and Reliability

System ko secure aur reliable banana bhi design ka part hai.

Consider:

- Password hashing
- Authentication and authorization
- Input validation
- Rate limiting
- HTTPS
- Data backup
- Error handling

Example: Password ko plain text mein database mein store nahi karna chahiye. Password hashing use karni chahiye.

### Step 11: Discuss Trade-offs

System Design mein har decision ke advantages aur disadvantages ho sakte hain.

Example:

SQL vs NoSQL:

- SQL structured data aur relationships ke liye useful ho sakta hai.
- NoSQL flexible document-based data ke liye useful ho sakta hai.

Decision system ki requirements aur access patterns ke according lena chahiye.

**Trade-off:** Ek benefit lene ke liye kisi doosre aspect mein compromise karna pad sakta hai.

### Step 12: Validate and Improve the Design

Final design ko dobara check karo:

- Kya saari core requirements cover ho rahi hain?
- Kya APIs expected functionality support karti hain?
- Kya database queries efficient hain?
- Kya system expected traffic handle kar sakta hai?
- Kya security consider ki gayi hai?
- Kya failure hone par recovery ka plan hai?

Agar problem mile to design improve karo.

---

## 3. Complete Problem-Solving Flow Diagram

```text
Understand Problem
       |
       v
Clarify Requirements
       |
       v
Define Scope & Assumptions
       |
       v
Identify Users & Components
       |
       v
Estimate Scale
       |
       v
Design Architecture
       |
       v
Design APIs & Database
       |
       v
Identify Bottlenecks
       |
       v
Security & Reliability
       |
       v
Discuss Trade-offs
       |
       v
Validate & Improve
```

**Note:** Ye practical framework hai, koi rigid universal rule nahi. Real projects mein kuch steps repeat ya parallel bhi ho sakte hain.

---

## 4. System Design Interview Mein Kaise Approach Karein?

Agar interviewer koi system design question de, to:

1. Problem ko apne words mein repeat karke confirm karo.
2. Requirements aur scope clarify karo.
3. Core use cases identify karo.
4. Important assumptions aur scale estimates batao.
5. High-level architecture draw karo.
6. APIs aur database ka basic design explain karo.
7. Bottlenecks, failures aur security discuss karo.
8. Trade-offs explain karo.
9. Interviewer ke feedback ke according design improve karo.

**Important:** Interview mein sirf final diagram banana enough nahi hai. Apne decisions ka reason explain karna bhi zaroori hai.

---

## 5. MERN Stack Se Connection

MERN developer ke liye System Design approach samajhna useful hai.

| System Component  | MERN Technology |
| ----------------- | --------------- |
| Frontend          | React.js        |
| Backend           | Node.js         |
| Backend Framework | Express.js      |
| Database          | MongoDB         |
| API Communication | HTTP / REST API |
| Authentication    | JWT / Session   |
| Image Storage     | Cloud Storage   |
| Caching           | Redis           |

Example flow:

```text
React Frontend
      |
      v
Express API
      |
      v
Node.js Backend
      |
      v
MongoDB
```

React request bhejta hai, Express route request receive karta hai, Node.js business logic execute karta hai aur MongoDB se data read/write hota hai.

---

## 6. Common Mistakes

1. Requirements samjhe bina architecture banana.
2. Har system mein unnecessarily microservices use karna.
3. Non-functional requirements ignore karna.
4. Traffic aur scale ka estimate na lagana.
5. Security ko last mein yaad karna.
6. Database design ko ignore karna.
7. Har problem ka same solution use karna.
8. Trade-offs explain na karna.
9. Bina reason ke unnecessary technologies add karna.

---

## 7. Interview Questions and Answers

**Q1. What is the System Design Problem Solving Approach?**

Ans: It is a structured process used to understand requirements, define scope, estimate scale, design architecture and evaluate a software system.

**Q2. Why should we clarify requirements first?**

Ans: Taaki system ka actual purpose aur expected functionality clear ho aur unnecessary features design mein include na hon.

**Q3. What is scope in System Design?**

Ans: Scope define karta hai ki system mein kaun-se features include honge aur kaun-se features initial design ke bahar rahenge.

**Q4. Why is scale estimation important?**

Ans: Isse expected traffic, storage aur infrastructure requirements ka rough idea milta hai.

**Q5. What is a bottleneck?**

Ans: System ka woh component jo overall performance ko limit karta hai.

**Q6. What is a trade-off?**

Ans: Jab ek design decision ke benefit ke saath kuch limitations ya disadvantages bhi accept karne padte hain.

**Q7. Should we always use microservices?**

Ans: No. Architecture project ki complexity, scale aur requirements ke according choose karni chahiye. Small applications ke liye monolithic architecture bhi suitable ho sakti hai.

---

## 8. Practical Tasks

### Task 1: Food Delivery Application

Ek food delivery app ke liye identify karo:

- Functional requirements
- Non-functional requirements
- Users
- Main components

### Task 2: YouTube-like Application

Basic design approach likho:

- User video kaise upload karega?
- Video ka data kahan store hoga?
- User videos kaise watch karega?
- System slow hone ke possible reasons kya hain?

### Task 3: MERN Blog Application

Ek basic blog application ke liye:

- Requirements identify karo.
- APIs list karo.
- MongoDB collections identify karo.
- High-level architecture diagram banao.

---

## 9. Quick Revision

- System Design Problem Solving Approach = System ko systematically design karne ka process.
- First step = Problem understand karna.
- Requirements = Functional + Non-Functional.
- Scope = System mein kya include hoga.
- Scale estimation = Expected load ka rough calculation.
- Architecture = Components aur unke connections.
- API = Frontend aur backend communication.
- Database design = Data storage structure.
- Bottleneck = Performance limit karne wala component.
- Trade-off = Benefits aur limitations ke beech decision.
- Validation = Design ko check aur improve karna.

---

## 10. Topic Completion Checklist

- [ ] Problem understanding
- [ ] Requirements clarification
- [ ] Scope and assumptions
- [ ] Users and components
- [ ] Scale estimation
- [ ] High-level architecture
- [ ] API and database design
- [ ] Bottleneck identification
- [ ] Security and reliability
- [ ] Trade-offs and validation

**Topic 03 complete hone ke baad:** Kisi ek application (Instagram, WhatsApp ya Food Delivery) ko lekar upar diye gaye steps khud apply karne ki practice karo.
