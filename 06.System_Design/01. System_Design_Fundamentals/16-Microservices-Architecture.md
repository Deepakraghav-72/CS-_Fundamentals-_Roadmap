# Topic 16: Microservices Architecture

## 1. Microservices Architecture Kya Hai?

Microservices Architecture ek software architecture style hai jisme ek large application ko multiple small, independent services mein divide kar diya jata hai.

Har service application ke ek specific business function ko handle karti hai.

**Simple Example:**

Maan lo hum ek E-commerce application bana rahe hain.

Isme multiple features hain:

- User Login
- Product Management
- Order Management
- Payment
- Notification

Monolithic Architecture mein ye saare features ek hi application ke andar ho sakte hain.

Lekin Microservices Architecture mein hum inhe separate services mein divide kar sakte hain:

1. Auth Service
2. Product Service
3. Order Service
4. Payment Service
5. Notification Service

Har service apna specific kaam karti hai.

### Simple Definition

Microservices Architecture is an architectural style in which a large application is divided into small, independent and loosely coupled services.

---

## 2. Real-Life Example

Maan lo tum Amazon jaisi E-commerce application use kar rahe ho.

Jab tum product purchase karte ho, to background mein multiple services kaam karti hain:

1. Auth Service: Check karti hai ki user logged in hai ya nahi.
2. Product Service: Product ki details provide karti hai.
3. Order Service: User ka order create karti hai.
4. Payment Service: Payment process karti hai.
5. Notification Service: Order confirmation message bhejti hai.

Har service ka apna responsibility area hota hai.

**Important:** Ye services ek doosre se communicate karti hain, lekin zaroori nahi ki sab ek hi codebase ya ek hi application process ka part hon.

---

## 3. Microservices Architecture Ka Structure

Ek basic Microservices Architecture kuch is tarah dikhti hai:

```text
              React Frontend
                    |
                    |
               API Gateway
                    |
       +------------+------------+
       |            |            |
       v            v            v
   Auth Service  Product      Order
                 Service      Service
       |            |            |
       v            v            v
    Auth DB      Product DB    Order DB
                                |
                                v
                          Payment Service
                                |
                                v
                            Payment DB
                                |
                                v
                       Notification Service
```

### Diagram Ko Samjho

- React Frontend: User interface provide karta hai.
- API Gateway: Incoming requests ko appropriate service tak pahunchata hai.
- Auth Service: Authentication handle karti hai.
- Product Service: Products manage karti hai.
- Order Service: Orders manage karti hai.
- Payment Service: Payments handle karti hai.
- Notification Service: Email, SMS ya push notifications bhejti hai.
- Database: Services apne data ki ownership maintain karti hain.

---

## 4. Independent Services Kya Hoti Hain?

Independent service ka matlab hai ki ek service ko doosri service se alag develop, deploy aur scale kiya ja sakta hai.

Example:

Maan lo Payment Service mein koi bug fix karna hai.

Monolithic application mein changes ke baad poori application ko redeploy karna pad sakta hai.

Microservices mein sirf Payment Service ko redeploy kiya ja sakta hai, agar architecture aur deployment properly configured ho.

### Benefits

- Independent deployment
- Independent development
- Independent scaling
- Better team ownership

**Note:** Independent deployment ka matlab ye nahi ki har service ko bina testing ya compatibility check ke update kar sakte hain.

---

## 5. Single Responsibility of a Service

Har microservice ka ek clearly defined business responsibility hona chahiye.

Example:

| Service              | Responsibility                |
| -------------------- | ----------------------------- |
| Auth Service         | Login, signup, authentication |
| Product Service      | Product management            |
| Order Service        | Order creation and management |
| Payment Service      | Payment processing            |
| Notification Service | Email, SMS notifications      |

Agar Payment Service ke andar product management, user profile aur notification ka code bhi daal diya, to service boundaries unclear ho jayengi.

**Rule:** Ek service ko ek related business capability par focus karna chahiye.

Iska matlab ye nahi ki har chhote function ke liye alag service bana deni chahiye.

---

## 6. Loose Coupling

Loose Coupling ka matlab hai ki services ek doosre par minimum dependency rakhti hain.

Example:

Order Service ko Payment Service se payment process karwana hai.

Order Service ko Payment Service ke internal code ya database structure ki knowledge hone ki zaroorat nahi hai.

Use sirf Payment Service ka defined API ya event contract pata hona chahiye.

### Tightly Coupled vs Loosely Coupled

| Tightly Coupled                 | Loosely Coupled                  |
| ------------------------------- | -------------------------------- |
| Services ki dependency zyada    | Dependency kam                   |
| Changes difficult ho sakte hain | Changes comparatively easier     |
| Internal details par dependency | Defined contracts par dependency |
| Maintenance difficult           | Maintenance easier               |

---

## 7. Database Per Service

Microservices ka ek important principle hai:

**Each service should own its data.**

Iska matlab har service apne data ko manage karne ke liye responsible hoti hai.

Example:

| Service              | Data Ownership       |
| -------------------- | -------------------- |
| Auth Service         | Users, credentials   |
| Product Service      | Products, inventory  |
| Order Service        | Orders               |
| Payment Service      | Payment records      |
| Notification Service | Notification records |

### Database Per Service Diagram

```text
Auth Service ---------- Auth Database

Product Service ------- Product Database

Order Service --------- Order Database

Payment Service ------- Payment Database

Notification Service - Notification Database
```

### Iska Benefit Kya Hai?

Agar Product Service apne database ka structure change karti hai, to doosri services ko directly us database ke internal structure par depend nahi hona padta.

### Important Point

Database Per Service ka matlab hamesha physically alag database server hona nahi hai.

Multiple services ek hi database server ya database cluster use kar sakti hain, lekin unki data ownership aur access boundaries separate honi chahiye.

**Avoid:** Multiple services ko ek hi shared database schema mein freely read/write karne dena. Isse tight coupling create hoti hai.

---

## 8. Microservices Communication

Microservices ko apna kaam karne ke liye ek doosre se communicate karna padta hai.

Communication ke mainly do types hain:

1. Synchronous Communication
2. Asynchronous Communication

### 8.1 Synchronous Communication

Synchronous communication mein ek service doosri service ko request bhejti hai aur response ka wait karti hai.

Example:

Order Service → Payment Service

```text
Order Service
      |
      | HTTP Request
      v
Payment Service
      |
      | HTTP Response
      v
Order Service
```

Common technologies:

- HTTP / REST API
- gRPC

**Example:** Order create karte waqt Payment Service se payment authorization ka response lena.

### 8.2 Asynchronous Communication

Asynchronous communication mein sender message publish karta hai aur zaroori nahi ki receiver ka response immediately wait kare.

Example:

```text
Order Service
      |
      | Publish Event
      v
   Message Broker
      |
      +-------------------+
      |                   |
      v                   v
Notification Service   Analytics Service
```

Common technologies:

- Apache Kafka
- RabbitMQ
- Message Queues

**Example:** Order successfully create hone ke baad Notification Service ko event bhejna.

### Difference

| Synchronous                  | Asynchronous                            |
| ---------------------------- | --------------------------------------- |
| Response ka wait hota hai    | Immediate response ka wait zaroori nahi |
| Request-response model       | Message/event model                     |
| HTTP, REST, gRPC             | Kafka, RabbitMQ                         |
| Caller ko delay ho sakta hai | Sender aage kaam kar sakta hai          |

---

## 9. API Gateway

API Gateway ek entry point hota hai jiske through client multiple microservices ko access karta hai.

Example:

React Frontend ko directly 5 services ke URLs manage nahi karne padte.

Wo API Gateway ko request bhejta hai.

API Gateway request ko correct service tak route karta hai.

```text
       React Frontend
              |
              v
         API Gateway
              |
      +-------+-------+
      |       |       |
      v       v       v
     Auth  Product   Order
    Service Service Service
```

### API Gateway Ke Main Functions

- Request routing
- Authentication checks
- Rate limiting
- Request/response handling
- Logging

API Gateway ke detailed concepts hum HLD ke topic `23-API-Gateway.md` mein padhenge.

---

## 10. Service Discovery

Microservices environment mein services ke network addresses aur instances change ho sakte hain.

Service Discovery ka kaam services ko ek doosre ka current network location find karne mein help karna hai.

Example:

Order Service ko Payment Service se communicate karna hai.

Lekin Payment Service ke multiple instances ho sakte hain.

Service Discovery available instances ki information provide kar sakta hai.

```text
          Service Registry
                 |
        +--------+--------+
        |                 |
        v                 v
   Payment Instance 1  Payment Instance 2
        ^                 ^
        |                 |
        +------Order------+
              Service
```

Common approaches:

- Service Registry
- DNS-based Discovery
- Platform-based service discovery

---

## 11. Load Balancing in Microservices

Agar kisi service ke multiple instances chal rahe hain, to incoming requests ko unke beech distribute karna hota hai.

Is process ko Load Balancing kehte hain.

Example:

```text
           Incoming Requests
                   |
                   v
              Load Balancer
                   |
          +--------+--------+
          |        |        |
          v        v        v
       Server 1 Server 2 Server 3
```

Isse ek hi server par saara load nahi aata.

Load Balancer ko hum HLD ke Topic 05 mein detail mein padhenge.

---

## 12. Independent Scaling

Microservices ka ek major advantage hai ki individual services ko independently scale kiya ja sakta hai.

Example:

Maan lo E-commerce application mein:

- Product Service par 10,000 requests per minute aa rahi hain.
- Payment Service par 1,000 requests per minute aa rahi hain.

To hum Product Service ke multiple instances run kar sakte hain, jabki Payment Service ke fewer instances enough ho sakte hain.

```text
Product Service:
[Instance 1] [Instance 2] [Instance 3] [Instance 4]

Payment Service:
[Instance 1] [Instance 2]
```

**Important:** Independent scaling possible hai, automatic nahi. Iske liye infrastructure, monitoring aur deployment setup chahiye.

---

## 13. Technology Independence

Microservices mein different services ke liye different technologies use ki ja sakti hain.

Example:

| Service           | Technology |
| ----------------- | ---------- |
| Auth Service      | Node.js    |
| Product Service   | Node.js    |
| Order Service     | Java       |
| Payment Service   | Go         |
| Analytics Service | Python     |

Database choices bhi service requirements ke according different ho sakti hain.

Lekin har service ke liye alag technology use karna compulsory nahi hai.

**Practical Advice:** Starting mein same technology stack rakhna simpler hota hai.

---

## 14. Fault Isolation

Fault Isolation ka matlab hai ki ek service ki failure ko doosri services tak spread hone se rokna.

Example:

Agar Notification Service down ho jati hai, to ideally user ka order create hona band nahi hona chahiye.

Order Service notification ko queue mein bhej sakti hai aur Notification Service recover hone par message process kar sakti hai.

Lekin agar Order Service ko Payment Service ki successful response zaroori hai, to Payment Service unavailable hone par order ka payment flow affect ho sakta hai.

Isliye fault isolation ke liye ye concepts useful hote hain:

- Timeouts
- Retries
- Circuit Breaker
- Message Queues
- Fallbacks

Inhe HLD mein detail mein padhenge.

---

## 15. Distributed Transactions

Monolithic application mein multiple database operations ek single ACID transaction ka part ho sakte hain, agar same transactional database use ho raha ho.

Microservices mein har service apne data ki owner hoti hai.

Example:

Order Service aur Payment Service ke databases alag hain.

Order create hua, lekin payment fail ho gaya.

Ab dono services ke data ko consistent rakhna challenge hai.

Is problem ko Distributed Transaction Problem kaha ja sakta hai.

### Example

```text
1. User places order
        |
        v
2. Order Service creates order
        |
        v
3. Payment Service processes payment
        |
        +------ Payment Success
        |             |
        |             v
        |       Confirm Order
        |
        +------ Payment Failed
                      |
                      v
                Cancel / Update Order
```

Different services ke databases par ek normal single ACID transaction assume nahi kar sakte.

### Saga Pattern (Introduction)

Saga Pattern ek approach hai jisme distributed business transaction ko multiple local transactions mein divide kiya jata hai.

Agar beech mein koi step fail ho jaye, to pehle complete ho chuke steps ko compensate karne ke liye compensating actions run kiye ja sakte hain.

Example:

- Order create
- Payment process
- Inventory reserve

Agar payment fail ho jaye, to order cancel karna ya inventory reservation release karna compensating action ho sakta hai.

Saga Pattern ko HLD mein detail mein padhenge.

---

## 16. Eventual Consistency

Microservices mein alag-alag services ka data har moment par immediately consistent hona zaroori nahi hota.

Kabhi-kabhi data thode time baad update hota hai.

Is concept ko Eventual Consistency kehte hain.

Example:

1. User order place karta hai.
2. Order Service order create karti hai.
3. Event publish hota hai.
4. Notification Service kuch time baad event process karti hai.
5. Notification send ho jata hai.

Is process mein kuch delay ho sakta hai.

Lekin system ke successful processing ke baad services ka related data expected consistent state mein aa sakta hai.

**Note:** Eventual consistency ka matlab data ko ignore karna nahi hai. System ko failures, duplicate events aur delayed messages bhi handle karne chahiye.

---

## 17. Observability

Microservices mein multiple independent services hoti hain. Isliye errors ko track karna difficult ho sakta hai.

Observability ka matlab hai system ke internal behavior ko logs, metrics aur traces ki help se understand karna.

### Main Components

**1. Logging**

Application mein kya events aur errors hue, unka record.

**2. Metrics**

System ki numerical measurements.

Examples:

- CPU usage
- Memory usage
- Request count
- Error rate
- Response time

**3. Distributed Tracing**

Ek request ne multiple services ke through kaunsa path follow kiya, use track karna.

```text
User Request
     |
     v
API Gateway
     |
     v
Order Service
     |
     v
Payment Service
     |
     v
Notification Service
```

Tracing se pata chal sakta hai ki request kis service par slow hui ya fail hui.

---

## 18. Security in Microservices

Microservices mein security sirf frontend aur backend ke beech nahi, balki service-to-service communication mein bhi important hai.

Important security practices:

1. Authentication: Request kis user ya service ki hai?
2. Authorization: Kya usko requested action perform karne ki permission hai?
3. HTTPS / TLS: Communication encrypt karna.
4. Secrets Management: Passwords, API keys aur tokens ko safely store karna.
5. Least Privilege: Har service ko sirf required permissions dena.
6. Input Validation: Incoming data validate karna.

**Important:** Internal network mein hone ka matlab ye nahi ki service automatically trusted hai.

---

## 19. Microservices Architecture Ke Advantages

| Advantage              | Explanation                                               |
| ---------------------- | --------------------------------------------------------- |
| Independent Deployment | Service ko separately deploy kar sakte hain               |
| Independent Scaling    | Required service ko separately scale kar sakte hain       |
| Technology Flexibility | Different technologies choose kar sakte hain              |
| Fault Isolation        | Failure ko limit karne mein help milti hai                |
| Team Independence      | Different teams different services manage kar sakti hain  |
| Maintainability        | Clear boundaries hone par maintenance easier ho sakti hai |

---

## 20. Microservices Architecture Ke Disadvantages

| Disadvantage          | Explanation                                                  |
| --------------------- | ------------------------------------------------------------ |
| Complexity            | Multiple services manage karni padti hain                    |
| Network Latency       | Service-to-service calls mein delay ho sakta hai             |
| Deployment Complexity | Multiple deployments manage karne padte hain                 |
| Data Consistency      | Different databases ka data consistent rakhna difficult      |
| Debugging             | Errors trace karna complex ho sakta hai                      |
| Testing               | Integration aur end-to-end testing difficult ho sakti hai    |
| Infrastructure Cost   | Monitoring, networking aur deployment ka cost badh sakta hai |

**Important:** Microservices automatically faster, cheaper, safer ya more scalable nahi hoti. Inke benefits tab milte hain jab architecture aur operations properly designed hon.

---

## 21. Monolithic vs Microservices Architecture

| Feature        | Monolithic                     | Microservices                    |
| -------------- | ------------------------------ | -------------------------------- |
| Structure      | Single application             | Multiple services                |
| Deployment     | Usually whole application      | Services independently           |
| Scaling        | Often whole application        | Individual services              |
| Database       | Often shared                   | Separate ownership               |
| Communication  | Mostly internal function calls | Network/API/events               |
| Complexity     | Initially simpler              | Operationally complex            |
| Debugging      | Often easier initially         | Distributed tracing needed       |
| Technology     | Usually common stack           | Different stacks possible        |
| Team Structure | Shared codebase ownership      | Service-level ownership possible |

### Important: Modular Monolith vs Microservices

Modular Monolith mein application ek deployable unit hoti hai, lekin code internally well-defined modules mein divided hota hai.

Microservices mein modules separate deployable services ban jati hain.

**Practical advice:** Most new projects ke liye pehle well-structured Modular Monolith banana sensible choice ho sakta hai. Jab real scaling, team ownership ya deployment needs justify karein, tab selected modules ko microservices mein split kar sakte hain.

---

## 22. Microservices Kab Use Karni Chahiye?

Microservices useful ho sakti hain jab:

1. Application ka size aur complexity kaafi badh chuki ho.
2. Different teams independently services develop kar rahi hon.
3. Different features ki scaling needs alag hon.
4. Independent deployment important ho.
5. Organization ke paas monitoring aur deployment infrastructure ho.
6. Business capabilities ki boundaries clearly defined hon.

### Microservices Kab Avoid Karni Chahiye?

1. Small beginner project ho.
2. Application ke users aur traffic abhi kam hon.
3. Development team bahut small ho.
4. Deployment infrastructure ready na ho.
5. Service boundaries clear na hon.
6. Distributed systems manage karne ka experience na ho.

**Remember:** Sirf modern technology use karne ke liye microservices mat banao.

---

## 23. MERN Stack Mein Microservices Architecture

Maan lo hum Node.js, Express.js, React.js aur MongoDB se E-commerce application bana rahe hain.

Possible architecture:

```text
                  React Frontend
                        |
                        v
                   API Gateway
                        |
          +-------------+-------------+
          |             |             |
          v             v             v
      Auth Service  Product Service  Order Service
          |             |             |
          v             v             v
       Auth DB       Product DB     Order DB
                                      |
                                      v
                                Payment Service
                                      |
                                      v
                                  Payment DB
                                      |
                                      v
                              Notification Service
```

### Possible Folder Structure

```text
ecommerce-microservices/
|
|-- frontend/
|   |-- src/
|   |-- package.json
|
|-- api-gateway/
|   |-- src/
|   |-- package.json
|
|-- services/
|   |
|   |-- auth-service/
|   |   |-- controllers/
|   |   |-- models/
|   |   |-- routes/
|   |   |-- server.js
|   |
|   |-- product-service/
|   |   |-- controllers/
|   |   |-- models/
|   |   |-- routes/
|   |   |-- server.js
|   |
|   |-- order-service/
|   |   |-- controllers/
|   |   |-- models/
|   |   |-- routes/
|   |   |-- server.js
|   |
|   |-- payment-service/
|   |   |-- controllers/
|   |   |-- models/
|   |   |-- routes/
|   |   |-- server.js
|   |
|   |-- notification-service/
|       |-- controllers/
|       |-- services/
|       |-- server.js
|
|-- docker-compose.yml
|-- README.md
```

Ye sirf ek illustrative folder structure hai. Real projects mein structure requirements ke according different ho sakta hai.

### MERN Stack Mein Technologies

| Requirement       | Possible Technology          |
| ----------------- | ---------------------------- |
| Frontend          | React.js                     |
| Backend           | Node.js + Express.js         |
| Database          | MongoDB                      |
| API Communication | REST API                     |
| Messaging         | Kafka / RabbitMQ             |
| API Gateway       | Nginx / Gateway service      |
| Containerization  | Docker                       |
| Deployment        | Cloud platforms / Kubernetes |

Har microservice ka Node.js ya MongoDB use karna compulsory nahi hai. Technology service ki requirements ke according select ki ja sakti hai.

---

## 24. Important Challenges

Microservices implement karte waqt kuch additional problems ko solve karna padta hai:

- Network failures
- Duplicate messages
- Service downtime
- Data consistency
- API version compatibility
- Distributed transactions
- Centralized monitoring
- Secure service-to-service communication

In challenges ko handle karne ke liye HLD ke upcoming topics mein hum detailed concepts padhenge.

---

## 25. Interview Questions and Answers

### Q1. What is Microservices Architecture?

Microservices Architecture ek architectural style hai jisme large application ko small, independent aur loosely coupled services mein divide kiya jata hai.

### Q2. What is the main difference between Monolithic and Microservices?

Monolithic mein application generally ek deployable unit hoti hai, jabki microservices mein application multiple independently deployable services mein divided hoti hai.

### Q3. What is Database Per Service?

Is principle mein har service apne data ki ownership aur access control maintain karti hai.

### Q4. What is Loose Coupling?

Jab services ek doosre ke internal implementation par minimum depend karti hain aur defined interfaces ke through communicate karti hain, use loose coupling kehte hain.

### Q5. What is API Gateway?

API Gateway ek entry point hai jo client requests ko appropriate backend services tak route karta hai.

### Q6. What is Service Discovery?

Service Discovery services ko ek doosre ke available network locations ya instances find karne mein help karta hai.

### Q7. What is Eventual Consistency?

Iska matlab hai ki distributed system mein different data copies ya services ka data immediately consistent na ho, lekin successful processing ke baad eventually consistent state mein aa sakta hai.

### Q8. What is Saga Pattern?

Saga Pattern distributed business transaction ko multiple local transactions mein divide karta hai aur failures ke liye compensating actions define kar sakta hai.

### Q9. Are Microservices always better than Monolithic Architecture?

Nahi. Small projects aur small teams ke liye monolithic architecture simpler aur more practical ho sakti hai.

### Q10. Can Microservices use different programming languages?

Haan. Different services apni requirements ke according different programming languages aur technologies use kar sakti hain.

---

## 26. Practical Tasks

### Task 1: Service Identification

Ek E-commerce application ke liye kam se kam 5 microservices identify karo.

### Task 2: Responsibility

Har service ki responsibility likho.

### Task 3: Database Ownership

Har service ke liye decide karo ki wo kaunsa data own karegi.

### Task 4: Communication

Decide karo ki kaun-si services REST API use karengi aur kaun-si events/message queues use karengi.

### Task 5: Diagram

Apni E-commerce Microservices Architecture ka diagram draw karo.

---

## 27. Quick Revision

| Concept                | Meaning                                                  |
| ---------------------- | -------------------------------------------------------- |
| Microservices          | Application divided into independent services            |
| Service                | Specific business capability handle karne wala component |
| Loose Coupling         | Minimum dependency between services                      |
| Independent Deployment | Service separately deploy ho sakti hai                   |
| Database Per Service   | Each service owns its data                               |
| API Gateway            | Client ke liye common entry point                        |
| Service Discovery      | Services ki location find karna                          |
| Load Balancing         | Requests ko instances mein distribute karna              |
| Synchronous            | Request bhejna aur response wait karna                   |
| Asynchronous           | Message bhejna without immediate response wait           |
| Eventual Consistency   | Data eventually consistent hona                          |
| Saga Pattern           | Distributed transaction coordination approach            |
| Observability          | Logs, metrics aur traces se system understand karna      |

---

## 28. Final Checklist

Is topic ko complete tab samjho jab tum:

- [ ] Microservices Architecture define kar sako.
- [ ] Monolithic aur Microservices ka difference samajh sako.
- [ ] Independent Services explain kar sako.
- [ ] Loose Coupling samajh sako.
- [ ] Database Per Service explain kar sako.
- [ ] Synchronous aur Asynchronous Communication differentiate kar sako.
- [ ] API Gateway aur Service Discovery samajh sako.
- [ ] Independent Scaling explain kar sako.
- [ ] Distributed Transactions aur Eventual Consistency samajh sako.
- [ ] Microservices ke advantages aur disadvantages bata sako.
- [ ] MERN application ka basic Microservices diagram bana sako.

**Topic 16 Complete – Microservices Architecture**
