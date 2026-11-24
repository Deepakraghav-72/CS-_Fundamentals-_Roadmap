# Topic 02: Functional & Non-Functional Requirements

## 1. What are Requirements?

Requirements ka matlab hota hai kisi software application ko banane ke liye uski zaruraton (needs) ko samajhna aur define karna.

Simple words mein:

**Requirements = What a software system needs to do and how well it should do it.**

Jab hum koi application banate hain, toh coding start karne se pehle humein samajhna hota hai:

- Application kya kaam karegi?
- User kaun-kaun se features use kar sakega?
- Application kitni fast honi chahiye?
- Application kitne users ko handle karegi?
- User ka data kitna secure hona chahiye?

In sabhi questions ke answers requirements kehlate hain.

### Example: Instagram

Maan lo humein Instagram jaisi application banani hai.

Humein decide karna hoga:

1. User account create kar sake.
2. User login kar sake.
3. User photos aur videos upload kar sake.
4. User doosron ki posts dekh sake.
5. User likes aur comments kar sake.
6. Application fast load honi chahiye.
7. User ka private data secure rehna chahiye.

Ye sab requirements hain.

---

## 2. Types of Requirements

Software Engineering aur System Design mein requirements ko broadly do major categories mein divide kiya jata hai:

1. Functional Requirements (FR)
2. Non-Functional Requirements (NFR)

### Diagram

```text
             REQUIREMENTS
                  |
          +-------+-------+
          |               |
          v               v
      FUNCTIONAL      NON-FUNCTIONAL
     REQUIREMENTS      REQUIREMENTS
          |               |
          v               v
     WHAT SYSTEM       HOW WELL SYSTEM
      SHOULD DO         SHOULD WORK
```

Ab dono ko detail mein samajhte hain.

---

## 3. Functional Requirements (FR)

### Definition

Functional Requirements define karti hain ki software system ko kya-kya functions ya operations perform karne chahiye.

Simple words mein:

**Functional Requirements = What the system should do.**

Ye application ke features aur functionality ko describe karti hain.

### Example: E-commerce Website

Maan lo hum Amazon jaisi shopping application bana rahe hain.

Uski functional requirements hongi:

1. User account create kar sake.
2. User login aur logout kar sake.
3. User products search kar sake.
4. User products ko cart mein add kar sake.
5. User orders place kar sake.
6. User online payment kar sake.
7. User order status track kar sake.
8. User order cancel kar sake.
9. Admin products add, update aur delete kar sake.

Ye sab functional requirements hain kyunki ye batati hain ki system ko kya karna hai.

### Important Characteristics of Functional Requirements

- Ye specific features define karti hain.
- Ye user actions ko describe karti hain.
- Ye system ke expected behavior ko define karti hain.
- Inhe test karke verify kiya ja sakta hai.

### More Examples

| Application       | Functional Requirement              |
| ----------------- | ----------------------------------- |
| WhatsApp          | User message send kar sake          |
| Instagram         | User photo upload kar sake          |
| YouTube           | User video play kar sake            |
| Banking App       | User money transfer kar sake        |
| Netflix           | User movie search aur play kar sake |
| Food Delivery App | User food order kar sake            |

---

## 4. Non-Functional Requirements (NFR)

### Definition

Non-Functional Requirements define karti hain ki software system ko kitni achhi tarah work karna chahiye.

Simple words mein:

**Non-Functional Requirements = How well the system should work.**

Ye application ki quality, performance, security aur reliability ko describe karti hain.

### Example: E-commerce Website

Maan lo hum Amazon jaisi application bana rahe hain.

Uski non-functional requirements hongi:

1. Website normal conditions mein 2 seconds ke andar page load kare.
2. System 10 lakh concurrent users ko handle karne ke liye design ho.
3. User ka sensitive data encrypted ho.
4. System highly available ho.
5. Payment processing reliable ho.
6. System future mein easily scale ho sake.
7. System ka data regular backup ho.

Ye non-functional requirements hain kyunki ye application ke features nahi, balki uski quality define karti hain.

**Note:** Performance requirements jaise response time aur capacity ko measurable targets ke saath define karna chahiye. Sirf "application fast honi chahiye" likhna sufficient nahi hai.

---

## 5. Important Types of Non-Functional Requirements

Non-Functional Requirements ke kai important types hote hain.

### 1. Performance

Performance batati hai ki system kitni speed se response deta hai.

Example:

- Website ka response time 200 milliseconds se kam hona chahiye for a specified API under defined load.
- Images jaldi load honi chahiye.

### 2. Scalability

Scalability ka matlab hai workload ya users badhne par system apni capacity increase kar sake.

Example:

Aaj application par 1,000 users hain aur future mein 10 lakh users aa sakte hain.

System ko is growth ke liye design karna scalability hai.

### 3. Availability

Availability batati hai ki system kitne samay tak users ke liye accessible hai.

Example:

Agar kisi system ki availability 99.9% hai, toh iska matlab system bahut high proportion of time available rehna chahiye.

### 4. Reliability

Reliability ka matlab hai system consistently aur correctly kaam kare.

Example:

Banking application mein money transfer ke time incorrect transaction nahi honi chahiye.

### 5. Security

Security ka matlab hai system aur user data ko unauthorized access aur attacks se protect karna.

Example:

- Password hashing
- Authentication
- Authorization
- Data encryption

### 6. Maintainability

Maintainability ka matlab hai application ko update, fix aur improve karna easy hona chahiye.

Example:

Developer easily payment feature mein changes kar sake bina poore application ko affect kiye.

### 7. Fault Tolerance

Fault Tolerance ka matlab hai system ke kisi component ke fail hone par bhi system required services provide karta rahe.

Example:

Agar ek server fail ho jaye toh doosra server requests handle kar sake.

### 8. Usability

Usability ka matlab hai application ko use karna easy hona chahiye.

Example:

User bina confusion ke shopping application par product search aur purchase kar sake.

### 9. Durability

Durability ka matlab hai successfully saved data ko unexpected failures ke baad bhi preserve karna.

Example:

Bank transaction successfully commit hone ke baad system crash ho jaye, tab bhi transaction ka committed data lost nahi hona chahiye.

### 10. Portability

Portability ka matlab hai software ko different environments ya platforms par run kar pana.

Example:

Application Windows, Linux aur cloud environments par run kar sake.

---

## 6. Functional vs Non-Functional Requirements

Ye dono ka difference bahut important hai.

| Functional Requirements                | Non-Functional Requirements                                   |
| -------------------------------------- | ------------------------------------------------------------- |
| What system should do                  | How well system should work                                   |
| Features define karti hain             | Quality define karti hain                                     |
| User actions describe karti hain       | System performance describe karti hain                        |
| Login, Signup, Payment                 | Security, Performance, Availability                           |
| Functional testing se verify hoti hain | Performance, security aur quality testing se verify hoti hain |

### Easy Example

Maan lo ek login system hai.

Functional Requirements:

- User login kar sake.
- User logout kar sake.
- Wrong password par error show ho.

Non-Functional Requirements:

- Login response 500 milliseconds ke andar aaye under specified load.
- Password securely hashed ho.
- System multiple users ko handle kar sake.

**Yaad rakhne ki trick:**

FR = WHAT?

NFR = HOW WELL?

---

## 7. Functional and Non-Functional Requirements in MERN

MERN Developer ke liye ye concept bahut important hai.

Maan lo hum MERN se ek E-commerce application bana rahe hain.

### Functional Requirements

React:

- Login page
- Signup page
- Product listing
- Shopping cart

Express + Node.js:

- Login API
- Signup API
- Product API
- Payment API

MongoDB:

- User data store karna
- Product data store karna
- Order data store karna

### Non-Functional Requirements

- React application fast load honi chahiye.
- Node.js backend heavy traffic handle kar sake.
- MongoDB mein data secure aur reliable rahe.
- Passwords securely hash hone chahiye.
- Application ko scale kar pana possible ho.
- Errors properly handle hone chahiye.

---

## 8. How to Identify Requirements Before System Design?

Kisi bhi system ka design banane se pehle requirements identify karni chahiye.

### Step 1: Understand the Problem

Sabse pehle samjho ki application kis problem ko solve karegi.

Example: Food delivery application users ko online food order karne ki facility degi.

### Step 2: Identify Users

Application ko kaun use karega?

Example:

- Customer
- Restaurant
- Delivery Partner
- Admin

### Step 3: Identify Functional Requirements

Har user kya-kya actions perform kar sakega?

Example:

- Customer food order kar sake.
- Restaurant orders accept kar sake.
- Delivery partner order deliver kar sake.

### Step 4: Identify Non-Functional Requirements

System ki quality aur constraints kya hongi?

Example:

- Fast response.
- Secure payments.
- High availability.
- Scalability.

### Step 5: Prioritize Requirements

Important requirements ko pehle priority do.

Example:

Payment security aur order placement basic critical requirements hain, jabki optional themes ya animations baad mein implement ki ja sakti hain.

---

## 9. Real-World Example: WhatsApp

Maan lo hum WhatsApp jaisa messaging system design kar rahe hain.

### Functional Requirements

1. User signup aur login kar sake.
2. User messages send aur receive kar sake.
3. User images aur videos share kar sake.
4. User group create kar sake.
5. User online status dekh sake.
6. User messages delete kar sake.

### Non-Functional Requirements

1. Messages quickly deliver hone chahiye.
2. User data secure hona chahiye.
3. System millions of users ko handle kar sake.
4. Messages reliably store aur deliver hone chahiye.
5. System highly available hona chahiye.
6. Message delivery mein duplicate processing avoid honi chahiye.

Is example se samajh sakte hain ki ek hi application mein FR aur NFR dono ki zarurat hoti hai.

---

## 10. Common Mistakes

1. Functional aur Non-Functional Requirements ko same samajhna.
2. Requirements clear kiye bina coding start karna.
3. Performance ko sirf "fast hona chahiye" likhna, measurable target na dena.
4. Security ko ignore karna.
5. Sirf features par focus karna aur system quality ignore karna.
6. Requirements ke beech conflicts ko identify na karna.

Example: Maximum security aur minimum response time dono important ho sakte hain, lekin kabhi-kabhi additional security checks performance ko affect kar sakte hain. Design mein dono ka balance karna padta hai.

---

## 11. Important Interview Questions

### Q1. What are Software Requirements?

Software Requirements define the features, behavior and quality expectations of a software system.

### Q2. What are Functional Requirements?

Functional Requirements define what operations or features a system must provide.

### Q3. What are Non-Functional Requirements?

Non-Functional Requirements define the quality attributes and constraints of a system.

### Q4. Give an example of FR and NFR.

FR: User should be able to log in.

NFR: Login API should respond within 500 milliseconds under a specified workload.

### Q5. Is Security a Functional or Non-Functional Requirement?

Security is generally treated as a Non-Functional Requirement or quality attribute. However, specific security features, such as login and role-based access control, can also be expressed as Functional Requirements.

### Q6. Is Scalability a Functional Requirement?

No. Scalability is generally a Non-Functional Requirement.

### Q7. Why should requirements be defined before System Design?

Because requirements help developers choose the correct architecture, technologies and design decisions.

### Q8. What is the difference between Reliability and Availability?

Reliability is about consistently performing correctly. Availability is about being accessible when required.

---

## 12. Practical Tasks

### Task 1: YouTube Application

YouTube ke liye 5 Functional Requirements aur 5 Non-Functional Requirements likho.

### Task 2: Banking Application

Identify karo:

- Login kaunsi requirement hai?
- Money transfer kaunsi requirement hai?
- Password encryption kaunsi requirement hai?
- Application availability kaunsi requirement hai?

### Task 3: E-commerce Application

Ek e-commerce website ke liye:

- 8 Functional Requirements.
- 8 Non-Functional Requirements.

Khud likhne ki practice karo.

---

## 13. Quick Revision

| Concept         | Meaning                                     |
| --------------- | ------------------------------------------- |
| Requirements    | Software ki needs                           |
| FR              | What system should do                       |
| NFR             | How well system should work                 |
| Performance     | Speed and response time                     |
| Scalability     | Increasing workload handle karna            |
| Availability    | System accessible rehna                     |
| Reliability     | Consistent correct working                  |
| Security        | Data aur system protection                  |
| Maintainability | Changes karna easy hona                     |
| Fault Tolerance | Failures ke bawajood service continue karna |
| Usability       | Application use karna easy hona             |
| Durability      | Saved data ko preserve karna                |

### Remember:

**Functional Requirements = Features**

**Non-Functional Requirements = Quality Attributes**

---

## 14. Topic Completion Checklist

- [ ] Requirements ka meaning samajhna.
- [ ] Functional Requirements samajhna.
- [ ] Non-Functional Requirements samajhna.
- [ ] Dono ke beech difference samajhna.
- [ ] NFR ke important types yaad karna.
- [ ] Real-world examples samajhna.
- [ ] Practical tasks solve karna.
- [ ] Interview questions revise karna.

**Topic 02 Complete – Functional & Non-Functional Requirements**

Next Topic: System Design Problem Solving Approach.
