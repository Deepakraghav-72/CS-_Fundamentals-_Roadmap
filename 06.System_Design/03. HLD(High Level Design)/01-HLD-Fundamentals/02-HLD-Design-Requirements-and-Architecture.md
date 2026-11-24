# 02. HLD Design Requirements & Architecture

## 1. Introduction

Kisi bhi software application ko develop karne se pehle hume ye samajhna hota hai ki application ko kya kaam karna hai aur uska overall structure kaisa hoga.

Is process mein do important cheezein hoti hain:

1. Design Requirements
2. System Architecture

**Design Requirements:** Application ko kya-kya kaam karna chahiye aur uski kya conditions honi chahiye.

**System Architecture:** Application ke different components kaise organize honge aur ek dusre ke saath communicate karenge.

Simple Example:

Maan lo tum Amazon jaisi E-commerce application bana rahe ho.

Requirements:

- User account create kar sake.
- Products search kar sake.
- Cart mein products add kar sake.
- Online payment kar sake.
- Order track kar sake.

Architecture:

- React frontend.
- Node.js backend.
- Express.js APIs.
- MongoDB database.
- Redis cache.
- Payment service.

Requirements batati hain application ko kya karna hai, aur Architecture batata hai application banegi kaise.

---

## 2. What Are Design Requirements?

Design Requirements wo conditions aur expectations hoti hain jo define karti hain ki software system ko kya features provide karne hain aur kis tarah perform karna hai.

Requirements ko samajhna HLD ka important starting point hai.

### Requirements ke main types

1. Functional Requirements
2. Non-Functional Requirements
3. Constraints
4. Assumptions

Inko aage ke topics mein detail mein padhenge.

---

## 3. Functional Requirements

Functional Requirements batati hain ki application kya-kya functionality provide karegi.

Example: E-commerce application

- User registration.
- User login.
- Product search.
- Add to cart.
- Place order.
- Make payment.
- View order history.

Ye sab functional requirements hain.

**Remember:** Functional Requirements = What the system should do.

---

## 4. Non-Functional Requirements

Non-Functional Requirements batati hain ki application apna kaam kitni achhi tarah karegi.

Example:

- Application fast honi chahiye.
- System secure hona chahiye.
- Millions of users handle kar sake.
- System reliable hona chahiye.
- Application highly available honi chahiye.

**Remember:** Non-Functional Requirements = How well the system should work.

---

## 5. What Are Constraints?

Constraints wo limitations ya restrictions hoti hain jinhe follow karke system design karna padta hai.

Examples:

1. Limited development budget.
2. Fixed project deadline.
3. Specific programming language use karna.
4. Existing database use karna.
5. Legal aur security requirements.

Example:

Agar company decide karti hai ki backend Node.js mein hi banana hai, toh ye technology constraint hai.

---

## 6. What Are Assumptions?

Assumptions wo conditions hoti hain jinhe hum design banate waqt temporarily true maan kar chalte hain.

Example:

Maan lo tum ek shopping application design kar rahe ho.

Tum assumptions le sakte ho:

- Most users mobile se application access karenge.
- Users internet connection ke through application use karenge.
- Traffic festival season mein increase hoga.
- Most users products browse karenge, lekin comparatively kam users purchase karenge.

Assumptions ko validate karna important hota hai. Galat assumptions architecture ko affect kar sakti hain.

---

## 7. What Is System Architecture?

System Architecture ek software system ka overall structure hota hai.

Ismein hum decide karte hain:

- Frontend kaise work karega?
- Backend kaise work karega?
- Database kaunsa hoga?
- APIs kaise communicate karengi?
- Traffic kaise handle hoga?
- Data kaise store aur retrieve hoga?

Example:

Ek MERN application ka basic architecture:

```text
          USER
            |
            |
       REACT FRONTEND
            |
            |
         API REQUEST
            |
            |
       EXPRESS SERVER
        (Node.js)
            |
       -------------
       |           |
       |           |
    MONGODB      REDIS
    DATABASE     CACHE
```

Ye ek simplified architecture hai.

---

## 8. Main Components of System Architecture

### 1. Client

Client wo application ya device hota hai jiske through user system access karta hai.

Examples:

- Web Browser
- Mobile Application
- Desktop Application

### 2. Backend Server

Backend server requests process karta hai aur business logic execute karta hai.

Example:
Node.js + Express.js.

### 3. Database

Database application ka data store karta hai.

Examples:

- MongoDB
- MySQL
- PostgreSQL

### 4. Cache

Cache frequently accessed data ko temporarily store karta hai taaki response fast mil sake.

Example:
Redis.

### 5. API

API different software components ke beech communication ka interface provide karti hai.

Example:
React frontend Express backend ki API call karta hai.

### 6. Load Balancer

Load Balancer incoming traffic ko multiple servers mein distribute karta hai.

Isse ek server par excessive load aane se bachaya ja sakta hai.

---

## 9. How to Design System Architecture?

System Architecture design karne ka basic process:

### Step 1: Understand Requirements

Sabse pehle application ke features aur expectations samjho.

Example:
E-commerce application mein registration, product search, cart aur payment features chahiye.

### Step 2: Identify System Components

Application ke major components identify karo.

Example:

- Frontend
- Backend
- Database
- Cache
- Payment Service

### Step 3: Select Architecture Style

Decide karo application ke liye kaunsa architecture suitable hoga.

Examples:

- Monolithic Architecture
- Microservices Architecture
- Client-Server Architecture

### Step 4: Select Technologies

Project ke according technologies choose karo.

Example:

- React
- Node.js
- Express.js
- MongoDB
- Redis

### Step 5: Design Communication

Decide karo components ek dusre ke saath kaise communicate karenge.

Example:
Frontend REST API ke through backend ko request bhejega.

### Step 6: Consider Scalability and Security

Future traffic, data growth aur security requirements ko consider karo.

### Step 7: Prepare Architecture Diagram

Finally system ka architecture diagram prepare karo.

---

## 10. Real-World Example: E-commerce Application

Maan lo hume ek E-commerce application banani hai.

### Requirements

Functional:

- User registration.
- Login.
- Product search.
- Shopping cart.
- Payment.
- Order tracking.

Non-Functional:

- Fast response.
- Secure payments.
- High availability.
- Scalability.

### Proposed Architecture

```text
                 USER
                   |
                   |
             REACT FRONTEND
                   |
                   |
                API REQUEST
                   |
                   |
              LOAD BALANCER
                   |
                   |
             NODE.JS BACKEND
                   |
          ---------------------
          |         |         |
          |         |         |
       MONGODB    REDIS    PAYMENT
       DATABASE   CACHE    SERVICE
          |
          |
       ORDER DATA
```

Note: Ye learning purpose ke liye simplified architecture hai. Real-world system mein additional services aur security mechanisms honge.

---

## 11. Important Design Considerations

Architecture decide karte waqt in points par dhyan dena chahiye:

| Consideration   | Meaning                               |
| --------------- | ------------------------------------- |
| Scalability     | Increasing traffic handle karna       |
| Performance     | Fast response provide karna           |
| Availability    | Service available rakhna              |
| Reliability     | Consistent working ensure karna       |
| Security        | Data protect karna                    |
| Maintainability | Changes aur updates easy banana       |
| Cost            | Infrastructure expenses control karna |

Ek architecture har situation ke liye perfect nahi hota. Requirements ke according trade-offs choose karne padte hain.

---

## 12. Common Mistakes

1. Requirements properly samjhe bina coding start karna.
2. Functional aur Non-Functional Requirements ko confuse karna.
3. Future scalability ignore karna.
4. Unnecessary complex architecture banana.
5. Security ko last mein consider karna.
6. Budget aur technology constraints ignore karna.
7. Architecture diagram properly document na karna.

---

## 13. Interview Questions

**Q1. What are Design Requirements?**

Answer: Design Requirements define the expected functionalities, performance expectations and constraints of a software system.

**Q2. What is System Architecture?**

Answer: System Architecture defines the overall structure of a software system and explains how its components interact.

**Q3. What is the difference between Requirements and Architecture?**

Answer: Requirements describe what the system should do, whereas Architecture describes how the system is structured to fulfill those requirements.

**Q4. What are Functional Requirements?**

Answer: Functional Requirements describe the features and operations that a system must perform.

**Q5. What are Non-Functional Requirements?**

Answer: Non-Functional Requirements describe quality attributes such as performance, scalability, security and availability.

**Q6. What are Constraints in System Design?**

Answer: Constraints are limitations or restrictions that influence system design, such as budget, technology and deadlines.

**Q7. What are Assumptions?**

Answer: Assumptions are conditions considered true during the design process until they are validated.

**Q8. What are the basic steps of System Architecture Design?**

Answer: Understand requirements, identify components, select architecture, choose technologies, design communication, consider scalability and security, and prepare architecture diagrams.

---

## 14. Practical Assignment

Ek simple Instagram-like application imagine karo.

In questions ke answers khud likhne ki koshish karo:

1. Application ke 5 Functional Requirements likho.
2. Application ke 5 Non-Functional Requirements likho.
3. Application ke 3 Constraints identify karo.
4. Application ke 3 Assumptions likho.
5. Frontend aur Backend ke liye technologies select karo.
6. Database select karo.
7. Ek basic architecture diagram banao.

---

## 15. Quick Revision

| Concept                     | Meaning                           |
| --------------------------- | --------------------------------- |
| Design Requirements         | System ki expectations            |
| Functional Requirements     | System kya karega                 |
| Non-Functional Requirements | System kitna achha perform karega |
| Constraints                 | Design ki limitations             |
| Assumptions                 | Temporarily accepted conditions   |
| System Architecture         | Overall system structure          |
| Client                      | User-facing application           |
| Backend                     | Server-side logic                 |
| Database                    | Data storage                      |
| API                         | Communication interface           |

### Final Revision

- Requirements = What to build?
- Architecture = How to structure the system?
- Functional Requirements = What features?
- Non-Functional Requirements = What quality?
- Constraints = What limitations?
- Assumptions = What are we temporarily accepting?

**Next Topic:** Functional Requirements

**Next File:** `03-Functional-Requirements.md`
