# 04. Non-Functional Requirements (NFR)

## 1. Introduction

Non-Functional Requirements software system ki wo requirements hoti hain jo define karti hain ki application kitni achhi tarah perform karegi.

Simple words mein:

NFR batati hain ki application fast, secure, reliable, scalable aur available kitni honi chahiye.

Example:

Maan lo tum Amazon jaisi E-commerce application bana rahe ho.

Application mein:

- 10 lakh users ko handle karne ki capability honi chahiye.
- Search results 2 seconds ke andar aane chahiye.
- User ka payment data secure hona chahiye.
- Application 24/7 available rehni chahiye.
- Server failure hone par bhi service continue rehni chahiye.

Ye sab Non-Functional Requirements hain.

### Technical Definition

Non-Functional Requirements define the quality attributes, performance expectations, constraints and operational characteristics of a software system.

**Remember:**

NFR = How well the system should work?

---

## 2. Why Are Non-Functional Requirements Important?

NFR important hain kyunki sirf features banana sufficient nahi hota. Application ko efficiently aur reliably work bhi karna chahiye.

Importance:

1. Performance: Application fast response provide kare.
2. Scalability: Increasing users aur traffic handle kare.
3. Availability: Application users ke liye available rahe.
4. Reliability: System consistently correct work kare.
5. Security: User data protect rahe.
6. Maintainability: Application ko update aur maintain karna easy ho.
7. Cost Efficiency: Infrastructure cost controlled rahe.

Example:

Agar shopping application mein product search feature hai, toh functional requirement batati hai ki user product search kar sake.

NFR batati hai ki search result 2 seconds ke andar aana chahiye, even when traffic is high.

---

## 3. Main Types of Non-Functional Requirements

NFR ke important quality attributes:

1. Performance
2. Scalability
3. Availability
4. Reliability
5. Security
6. Maintainability
7. Usability
8. Fault Tolerance
9. Durability
10. Interoperability

Inhe detail mein samajhte hain.

---

## 4. Performance

Performance define karti hai ki application kitni fast aur efficiently requests process karti hai.

Example:

User Amazon par product search karta hai.

Agar result 1 second mein aa jata hai toh performance achhi ho sakti hai.

Agar result aane mein 20 seconds lagte hain toh performance poor ho sakti hai.

### Important Performance Metrics

**1. Latency**

Latency ka matlab hai request bhejne aur response milne ke beech ka time.

Example:

User ne request bheji aur response 200 milliseconds mein mila.

Latency = 200 ms.

**2. Throughput**

Throughput batata hai ki system ek given time mein kitni requests process kar sakta hai.

Example:

Server 1 second mein 5,000 requests process karta hai.

Throughput = 5,000 requests/second.

**3. Response Time**

Response Time wo total time hai jo user request initiate karne se lekar response receive karne tak experience karta hai.

### Latency vs Throughput

| Latency                    | Throughput                                    |
| -------------------------- | --------------------------------------------- |
| Request ka response time   | Requests process karne ki rate                |
| Time mein measure hoti hai | Requests per second mein measure ho sakta hai |
| Lower generally better     | Higher generally better                       |

---

## 5. Scalability

Scalability system ki ability hai jisse woh increasing users, requests aur workload ko handle kar sake.

Example:

Aaj tumhari application ko 1,000 users use kar rahe hain.

Kal 1 lakh users use karne lagte hain.

Agar application apne resources aur architecture ko adjust karke additional traffic handle kar sake, toh system scalable hai.

### Types of Scalability

**1. Vertical Scaling**

Vertical Scaling ka matlab existing server ki capacity increase karna.

Example:

- 8 GB RAM se 32 GB RAM.
- 4 CPU cores se 16 CPU cores.

**2. Horizontal Scaling**

Horizontal Scaling ka matlab additional servers add karna.

Example:

- 1 server se 3 servers.
- 3 servers se 10 servers.

```text
Vertical Scaling:

   SERVER
      |
   Upgrade
      |
  More RAM
  More CPU


Horizontal Scaling:

   SERVER 1
      |
   SERVER 2
      |
   SERVER 3
```

---

## 6. Availability

Availability batati hai ki system kitne time tak users ke liye accessible aur operational rehta hai.

Example:

Agar application 24 hours mein 23 hours 59 minutes available hai aur 1 minute down hai, toh uski availability approximately 99.93% hai.

### Availability Formula

Availability = (Uptime / Total Time) × 100

Where:

- Uptime = System working time.
- Downtime = System unavailable time.
- Total Time = Uptime + Downtime.

### Availability Percentage

| Availability | Approx. Downtime per Year |
| ------------ | ------------------------: |
| 99%          |                 3.65 days |
| 99.9%        |                8.76 hours |
| 99.99%       |             52.56 minutes |
| 99.999%      |              5.26 minutes |

Higher availability generally means less downtime.

---

## 7. Reliability

Reliability ka matlab hai system given conditions mein consistently aur correctly work kare.

Example:

Banking application mein agar user ₹1,000 transfer karta hai, toh system ko transaction correctly process karni chahiye.

Agar system baar-baar errors deta hai ya incorrect transactions karta hai, toh reliability poor hai.

**Availability vs Reliability**

| Availability                  | Reliability                                |
| ----------------------------- | ------------------------------------------ |
| System accessible hai ya nahi | System correctly work kar raha hai ya nahi |
| Uptime se related             | Failure-free operation se related          |
| Downtime important hai        | Failures aur errors important hain         |

Ek system available ho sakta hai, lekin incorrect results de raha ho. Isliye availability aur reliability same nahi hain.

---

## 8. Security

Security ka purpose application aur user data ko unauthorized access, attacks aur data theft se protect karna hai.

Important security concepts:

**1. Authentication**

Verify karna ki user kaun hai.

Example: Login using email and password.

**2. Authorization**

Decide karna ki authenticated user kya access kar sakta hai.

Example: Normal user admin dashboard access nahi kar sakta.

**3. Encryption**

Data ko protected format mein convert karna.

Example: HTTPS communication mein TLS encryption.

**4. Access Control**

Users ko unke roles aur permissions ke according access dena.

**5. Data Protection**

Sensitive user information ko protect karna.

---

## 9. Maintainability

Maintainability batati hai ki application ko modify, debug, update aur maintain karna kitna easy hai.

Example:

Agar tumhare project mein code properly organized hai aur components separate hain, toh future changes easy ho sakte hain.

Maintainability improve karne ke methods:

- Clean code.
- Modular architecture.
- Proper documentation.
- Automated testing.
- Consistent coding standards.

---

## 10. Usability

Usability batati hai ki user application ko kitni easily understand aur operate kar sakta hai.

Example:

Ek shopping application mein:

- Simple navigation.
- Easy checkout.
- Clear buttons.
- Readable text.
- Helpful error messages.

Ye sab usability improve karte hain.

---

## 11. Fault Tolerance

Fault Tolerance system ki ability hai jisse kisi component ke fail hone par bhi system apni required service continue rakh sake.

Example:

Maan lo application mein 3 backend servers hain.

Agar ek server fail ho jata hai, toh load balancer requests ko remaining healthy servers par bhej sakta hai.

Isse service completely stop hone se bach sakti hai.

---

## 12. Durability

Durability ka matlab hai ki successfully stored data system failure ke baad bhi lost nahi hona chahiye.

Example:

Banking application mein successful transaction ka record permanently preserve rehna chahiye.

Durability improve karne ke methods:

- Database backups.
- Replication.
- Persistent storage.
- Recovery mechanisms.

Note: Replication aur backup alag purposes serve karte hain. Replication immediate availability mein help kar sakti hai, jabki backup historical recovery mein useful hota hai.

---

## 13. Interoperability

Interoperability ka matlab hai different systems aur technologies ka ek dusre ke saath communicate aur work kar pana.

Example:

E-commerce application ka payment gateway se communicate karna.

- React frontend.
- Node.js backend.
- MongoDB database.
- External payment gateway.

Ye different systems APIs aur common communication standards ke through interact kar sakte hain.

---

## 14. Functional vs Non-Functional Requirements

Ye dono HLD ke important concepts hain.

| Functional Requirements    | Non-Functional Requirements          |
| -------------------------- | ------------------------------------ |
| What system does           | How well system works                |
| Features define karti hain | Quality attributes define karti hain |
| Login                      | Secure login                         |
| Product search             | Fast product search                  |
| Payment                    | Secure and reliable payment          |
| Order tracking             | Responsive order tracking            |
| Upload image               | Image upload performance             |

Example:

Functional Requirement:
System users ko products search karne dega.

Non-Functional Requirement:
System 95% product search requests ko 2 seconds ke andar complete karega under the specified expected load.

---

## 15. NFR Ko Measurable Kaise Banayein?

Ek achhi NFR clear aur measurable honi chahiye.

Weak Requirement:

Application fast honi chahiye.

Problem: Fast ka exact meaning clear nahi hai.

Better Requirement:

95% search requests expected load par 2 seconds ke andar complete honi chahiye.

Weak Requirement:

Application scalable honi chahiye.

Better Requirement:

System ko 10,000 concurrent users handle karne ke liye design kiya jana chahiye.

Weak Requirement:

Application available honi chahiye.

Better Requirement:

Monthly availability target 99.9% hona chahiye.

Important: Ye examples illustrative targets hain. Real system mein targets business requirements, budget aur workload ke according decide hote hain.

---

## 16. Common Mistakes

1. Functional aur Non-Functional Requirements ko confuse karna.
2. Performance ko sirf speed samajhna.
3. Availability aur Reliability ko same samajhna.
4. Scalability ko ignore karna.
5. Security ko development ke end mein consider karna.
6. NFR ko measurable form mein define na karna.
7. Infrastructure cost ignore karna.
8. Expected traffic aur workload estimate na karna.

---

## 17. Interview Questions

**Q1. What are Non-Functional Requirements?**

Answer: NFRs define the quality attributes and operational characteristics of a system, such as performance, scalability, security and availability.

**Q2. What is Performance?**

Answer: Performance describes how efficiently a system processes requests, commonly measured through latency, response time and throughput.

**Q3. What is Scalability?**

Answer: Scalability is the ability of a system to handle increasing workload by adding or upgrading resources.

**Q4. What is Availability?**

Answer: Availability is the percentage of time a system remains operational and accessible.

**Q5. What is Reliability?**

Answer: Reliability is the ability of a system to perform its intended functions correctly and consistently over time.

**Q6. What is Fault Tolerance?**

Answer: Fault Tolerance is the ability of a system to continue providing required services despite failures in some components.

**Q7. What is the difference between Latency and Throughput?**

Answer: Latency measures the time taken for a request to receive a response, while throughput measures the number of operations processed per unit of time.

**Q8. What is the difference between Availability and Reliability?**

Answer: Availability measures whether the system is accessible, while reliability measures whether it performs correctly and consistently.

**Q9. Why should NFRs be measurable?**

Answer: Measurable NFRs make it possible to evaluate, test and verify whether the system meets its quality targets.

**Q10. What is Durability?**

Answer: Durability ensures that successfully committed data remains preserved even after failures.

---

## 18. Practical Assignment

Imagine tum ek online banking application design kar rahe ho.

At least 10 Non-Functional Requirements identify karo.

Consider:

1. Performance.
2. Scalability.
3. Availability.
4. Reliability.
5. Security.
6. Fault Tolerance.
7. Durability.
8. Maintainability.
9. Usability.
10. Interoperability.

Bonus Task:

Inmein se 5 requirements ko measurable banao.

Example:

"The banking application should achieve a monthly availability target of 99.99%."

---

## 19. Quick Revision

| Term             | Meaning                               |
| ---------------- | ------------------------------------- |
| NFR              | How well system works                 |
| Performance      | System ki efficiency                  |
| Latency          | Request-response time                 |
| Throughput       | Operations per unit time              |
| Scalability      | Increasing workload handle karna      |
| Availability     | System accessible rehna               |
| Reliability      | Correct and consistent operation      |
| Security         | System aur data protection            |
| Maintainability  | Easy updates and maintenance          |
| Usability        | Easy user experience                  |
| Fault Tolerance  | Failures ke bawajood service continue |
| Durability       | Stored data preserve rehna            |
| Interoperability | Different systems ka saath work karna |

### Final Revision

NFR define karti hain ki software application kitni fast, secure, reliable, scalable aur available honi chahiye.

**Remember: Functional Requirements = WHAT**

**Non-Functional Requirements = HOW WELL**

Next Topic: System Design Estimation (Back-of-the-Envelope)

Next Filename: `05-System-Design-Estimation.md`
