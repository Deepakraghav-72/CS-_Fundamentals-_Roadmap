# 03. Functional Requirements

## 1. Introduction

Functional Requirements software system ki wo requirements hoti hain jo define karti hain ki application kya-kya kaam karegi.

Simple words mein:

Functional Requirements batati hain ki user application ke andar kaun-kaun se actions perform kar sakta hai aur system un actions par kaise respond karega.

**Example:**

Maan lo tum Amazon jaisi E-commerce application bana rahe ho.

User application mein:

- Account create kar sakta hai.
- Login kar sakta hai.
- Products search kar sakta hai.
- Products cart mein add kar sakta hai.
- Online payment kar sakta hai.
- Order place kar sakta hai.
- Order status check kar sakta hai.

Ye sab Functional Requirements hain.

### Technical Definition

Functional Requirements specify the features, operations, inputs, outputs and behaviors that a software system must provide to its users.

**Remember:**

Functional Requirements = What should the system do?

---

## 2. Why Are Functional Requirements Important?

Functional Requirements define karti hain ki application mein kaun-kaun se features develop karne hain.

Inki importance:

1. Feature Clarity: Developers ko clear hota hai ki kya banana hai.
2. User Satisfaction: Application user ki needs fulfill karti hai.
3. Development Planning: Development team features plan kar sakti hai.
4. Testing: Testers verify kar sakte hain ki features correctly work kar rahe hain.
5. Project Scope: Project mein kya included hai aur kya nahi, ye clear hota hai.
6. Communication: Developers, designers aur clients ke beech confusion kam hota hai.

---

## 3. Functional Requirements Ke Main Elements

Ek functional requirement ko samajhne ke liye kuch important elements hote hain:

### 1. Input

User ya kisi external system se aane wala data.

Example:
User login karne ke liye email aur password enter karta hai.

### 2. Processing

System input par operations perform karta hai.

Example:
Backend database mein user ko search karta hai aur password verify karta hai.

### 3. Output

Processing ke baad system jo result deta hai.

Example:
Login successful hone par user dashboard open hota hai.

### 4. System Behavior

Kisi particular action ya condition par system ka expected response.

Example:
Galat password enter karne par system error message display karta hai.

**Example Flow:**

```text
       USER
         |
         |
    ENTER EMAIL
    AND PASSWORD
         |
         |
      FRONTEND
         |
         |
      LOGIN API
         |
         |
    BACKEND SERVER
         |
         |
      DATABASE
         |
         |
   VERIFY CREDENTIALS
         |
      ----------
      |        |
    VALID    INVALID
      |        |
      |        |
   SUCCESS   ERROR
   RESPONSE  MESSAGE
```

---

## 4. Real-World Example: E-commerce Application

Maan lo tum ek online shopping application design kar rahe ho.

Iski Functional Requirements:

### A. User Management

- User account create kar sake.
- User login kar sake.
- User logout kar sake.
- User profile update kar sake.
- User password reset kar sake.

### B. Product Management

- User products dekh sake.
- User products search kar sake.
- User categories filter kar sake.
- User product details dekh sake.
- Admin products add, update aur delete kar sake.

### C. Shopping Cart

- User products cart mein add kar sake.
- User cart se products remove kar sake.
- User product quantity update kar sake.
- User cart ka total price dekh sake.

### D. Order Management

- User order place kar sake.
- User order history dekh sake.
- User order status track kar sake.
- User eligible order cancel kar sake.

### E. Payment Management

- User online payment kar sake.
- System payment status verify kar sake.
- System successful payment ke baad order confirm kar sake.
- System failed payment handle kar sake.

Ye sab application ki Functional Requirements hain.

---

## 5. Functional Requirements Kaise Identify Karein?

System Design mein Functional Requirements identify karne ke liye following steps follow kar sakte hain.

### Step 1: Users Identify Karo

Sabse pehle identify karo ki application ko kaun use karega.

Example: E-commerce

- Customer
- Admin
- Delivery Partner

### Step 2: User Actions Identify Karo

Har user application mein kya-kya actions perform karega?

Customer:

- Register
- Login
- Search Products
- Add to Cart
- Place Order

Admin:

- Add Product
- Update Product
- Manage Orders

### Step 3: System Responses Identify Karo

Har action par system ka response kya hoga?

Example:

User login karta hai:

- Valid credentials: Login successful.
- Invalid credentials: Error message.
- Account locked: Login deny hoga.

### Step 4: Requirements Document Karo

Har functionality ko clearly document karo.

Example:

FR-01: The system shall allow users to register using their email address.

FR-02: The system shall allow registered users to log in.

FR-03: The system shall allow users to search for products.

FR-04: The system shall allow users to add products to their shopping cart.

FR-05: The system shall allow users to place orders.

---

## 6. Functional Requirements vs User Stories

Dono software requirements describe karne ke methods hain, lekin presentation different hoti hai.

### Functional Requirement

Formal statement hota hai jo system ki required functionality define karta hai.

Example:

"The system shall allow users to add products to their shopping cart."

### User Story

User ke point of view se feature describe karti hai.

Common format:

"As a [user], I want [feature], so that [benefit]."

Example:

"As a customer, I want to add products to my cart so that I can purchase them later."

| Functional Requirement  | User Story              |
| ----------------------- | ----------------------- |
| System-focused          | User-focused            |
| Formal statement        | Simple natural language |
| Defines system behavior | Explains user need      |
| Used for specifications | Commonly used in Agile  |

---

## 7. Functional Requirements vs Use Cases

Use Case batata hai ki koi particular user goal achieve karne ke liye system ke saath kaise interact karta hai.

Example: User Login

Actor: Customer

Main Flow:

1. User login page open karta hai.
2. Email enter karta hai.
3. Password enter karta hai.
4. Login button click karta hai.
5. System credentials verify karta hai.
6. System successful login response deta hai.

Alternative Flow:

1. User incorrect password enter karta hai.
2. System credentials reject karta hai.
3. Error message display hota hai.

| Functional Requirement                   | Use Case                                  |
| ---------------------------------------- | ----------------------------------------- |
| Required functionality define karta hai  | Interaction steps explain karta hai       |
| Short requirement statement ho sakta hai | Detailed flow ho sakta hai                |
| What system must do                      | User aur system kaise interact karte hain |

---

## 8. Functional Requirements In MERN Stack

Tum MERN Stack seekh rahe ho. Ek login feature ka example dekho.

### React.js – Frontend

- Email input provide karega.
- Password input provide karega.
- Login button provide karega.
- Error aur success messages display karega.

### Express.js – API

- Login endpoint create karega.
- Request validate karega.
- Appropriate response return karega.

### Node.js – Backend

- Login ki business logic execute karega.
- Password verification process handle karega.

### MongoDB – Database

- User information store karega.
- User record retrieve karne mein help karega.

Example API:

```http
POST /api/auth/login
```

Request Body:

```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

Possible Response:

```json
{
  "success": true,
  "message": "Login successful"
}
```

Note: Real applications mein passwords plaintext mein store nahi karne chahiye. Password hashing aur secure authentication use karna zaroori hai.

---

## 9. Functional Requirements Ko Test Kaise Karte Hain?

Har Functional Requirement ko test kiya ja sakta hai.

Example: Login Functionality

| Test Case                  | Expected Result      |
| -------------------------- | -------------------- |
| Correct email and password | Login successful     |
| Incorrect password         | Error message        |
| Invalid email format       | Validation error     |
| Empty email                | Required field error |
| Empty password             | Required field error |
| Unregistered email         | Login rejected       |

Testing se verify hota hai ki implemented functionality expected behavior ke according work kar rahi hai.

---

## 10. Common Mistakes

1. Requirements ko unclear language mein likhna.
2. User actions identify na karna.
3. Admin aur customer features ko mix karna.
4. Error conditions ignore karna.
5. Duplicate requirements likhna.
6. Requirements ko unnecessarily technical banana.
7. Important features miss karna.

**Good Practice:** Requirements clear, specific, testable aur understandable honi chahiye.

---

## 11. Interview Questions

**Q1. What are Functional Requirements?**

Answer: Functional Requirements define the features and operations that a software system must perform to satisfy user needs.

**Q2. Give examples of Functional Requirements.**

Answer: User registration, login, product search, payment processing, order placement and order tracking.

**Q3. How do you identify Functional Requirements?**

Answer: Identify users, understand their goals, list their actions, define system responses and document the required functionality.

**Q4. What is a User Story?**

Answer: A User Story describes a software feature from the user's perspective, commonly using the format: As a user, I want a feature, so that I get a benefit.

**Q5. What is a Use Case?**

Answer: A Use Case describes how an actor interacts with a system to achieve a particular goal.

**Q6. Can Functional Requirements be tested?**

Answer: Yes. Each Functional Requirement can be verified through test cases that check expected system behavior.

**Q7. What is the difference between Functional and Non-Functional Requirements?**

Answer: Functional Requirements define what the system does, whereas Non-Functional Requirements define how well the system performs.

---

## 12. Practical Assignment

Imagine tumhe Instagram jaisi social media application design karni hai.

Identify at least 15 Functional Requirements.

Include:

1. User Registration
2. User Login
3. User Logout
4. Profile Management
5. Upload Photo
6. Upload Video
7. Like Post
8. Comment on Post
9. Follow User
10. Unfollow User
11. Search Users
12. View Feed
13. Send Messages
14. Delete Post
15. View Notifications

Ab in requirements ko FR-01, FR-02, FR-03 format mein document karo.

Bonus Task:

Kisi ek feature, jaise Upload Photo, ka complete Use Case likho.

---

## 13. Quick Revision

| Term                   | Meaning                           |
| ---------------------- | --------------------------------- |
| Functional Requirement | System kya karega                 |
| Input                  | System ko milne wala data         |
| Processing             | Input par operation               |
| Output                 | Processing ka result              |
| System Behavior        | System ka expected response       |
| User Story             | User ke perspective se feature    |
| Use Case               | Actor aur system interaction      |
| FR                     | Functional Requirement identifier |

### Final Revision

Functional Requirements define karti hain ki application kya-kya functionality provide karegi.

Example:

- Login
- Registration
- Search
- Upload
- Payment
- Order Management

**Remember: Functional Requirements = WHAT the system does.**

---

### Next Topic

Topic 04: Non-Functional Requirements

Filename: `04-Non-Functional-Requirements.md`

Folder: `01-HLD-Fundamentals`
