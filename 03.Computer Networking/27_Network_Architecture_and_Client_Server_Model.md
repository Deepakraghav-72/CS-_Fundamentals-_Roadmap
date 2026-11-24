# 27. Network Architecture and Client-Server Model – Complete Notes

## 1. What is Network Architecture?

Network Architecture ek design ya structure hota hai jo define karta hai ki network ke devices, services aur communication components kaise organized aur connected honge.

Easy language:

Network Architecture batata hai ki network mein kaun-kaun se devices honge, wo kaise communicate karenge aur resources kaise share karenge.

### Example

Ek company ke network mein:

- Client computers.
- Application servers.
- Database servers.
- Routers.
- Switches.
- Firewalls.

In sabka arrangement aur communication design Network Architecture ka part hai.

### Network Architecture ke Main Components

1. Clients – Services request karte hain.
2. Servers – Services provide karte hain.
3. Network Devices – Communication forward karte hain.
4. Protocols – Communication rules define karte hain.
5. Security – Network ko protect karti hai.
6. Network Infrastructure – Physical aur virtual connectivity provide karti hai.

## 2. Types of Network Architecture

Network Architecture ke commonly discussed models:

1. Client-Server Architecture.
2. Peer-to-Peer Architecture.
3. Hybrid Architecture.

## 3. What is Client-Server Architecture?

Client-Server Architecture ek networking model hai jisme client service ya resource request karta hai aur server us request ko process karke response deta hai.

Easy language:

Client = Request karne wala.

Server = Request receive aur process karne wala.

### Real-Life Example

Jab tum browser mein YouTube open karte ho:

1. Browser server ko request bhejta hai.
2. Server request process karta hai.
3. Server response return karta hai.
4. Browser content display karta hai.

### Diagram

```text
          CLIENT
        (Browser)
             |
             | Request
             v
          SERVER
       (Application)
             |
             | Response
             v
          CLIENT
        (Browser)
```

### Examples

- Website.
- Online Banking.
- Gmail.
- E-commerce applications.
- Social Media Platforms.

## 4. What is a Client?

Client ek device ya software application hota hai jo server se services ya resources request karta hai.

### Examples

- Web Browser.
- Mobile Application.
- Desktop Application.
- Email Client.
- API Client.

### Client Responsibilities

1. Server ko request bhejna.
2. User input collect karna.
3. Server response receive karna.
4. Data display karna.
5. User interaction handle karna.

## 5. What is a Server?

Server ek computer ya software process hota hai jo clients ko services, data ya resources provide karta hai.

### Examples

- Web Server.
- Database Server.
- File Server.
- Mail Server.
- Application Server.

### Server Responsibilities

1. Client requests receive karna.
2. Requests process karna.
3. Required data fetch karna.
4. Response generate karna.
5. Multiple clients ko serve karna.
6. Access control aur security enforce karna.

**Important:** Server ka matlab sirf powerful physical computer nahi hota. Server ek software process bhi ho sakta hai jo services provide karta hai.

## 6. How Client-Server Communication Works

Example: Browser se website open karna.

### Step-by-Step Process

**Step 1:** User browser open karta hai.

**Step 2:** User website ka URL enter karta hai.

**Step 3:** DNS domain name resolve karta hai.

**Step 4:** Browser server ke saath network connection establish karta hai.

**Step 5:** Browser HTTP/HTTPS request send karta hai.

**Step 6:** Server request process karta hai.

**Step 7:** Server response return karta hai.

**Step 8:** Browser response ko process karke webpage display karta hai.

### Diagram

```text
       USER
        |
        v
     BROWSER
        |
        | DNS Lookup
        v
       DNS
        |
        | IP Address
        v
   WEB SERVER
        |
        | HTTP Response
        v
     BROWSER
        |
        v
    WEB PAGE
```

## 7. What is Peer-to-Peer Architecture?

Peer-to-Peer (P2P) Architecture ek networking model hai jisme connected devices directly ek doosre ke saath resources share kar sakte hain.

Har peer zarurat ke according client aur server dono ki tarah behave kar sakta hai.

Easy language:

Is model mein ek central dedicated server har communication ke liye compulsory nahi hota.

### Diagram

```text
          PEER A
          /    \
         /      \
        v        v
     PEER B <-- PEER C
        |
        v
     PEER D
```

### Examples

- BitTorrent.
- Direct file sharing.
- Some decentralized communication systems.

### Advantages

1. Resource sharing.
2. Central server dependency reduce ho sakti hai.
3. Distributed workload.
4. Small networks mein simple setup.

### Disadvantages

1. Centralized management difficult.
2. Security management challenging.
3. Data availability peers par depend kar sakti hai.
4. Backup aur control difficult ho sakta hai.

## 8. Client-Server vs Peer-to-Peer

| Client-Server                               | Peer-to-Peer                               |
| ------------------------------------------- | ------------------------------------------ |
| Dedicated server commonly hota hai          | Dedicated central server necessary nahi    |
| Centralized management                      | Distributed management                     |
| Server services provide karta hai           | Peers resources share karte hain           |
| Central server failure impact kar sakta hai | Multiple peers ke through sharing possible |
| Example: Banking website                    | Example: BitTorrent                        |

## 9. What is 2-Tier Architecture?

2-Tier Architecture ek application architecture hai jisme application ko do main layers mein organize kiya jata hai:

1. Client Layer.
2. Database/Server Layer.

Easy language:

Client directly database server ya backend service se communicate karta hai.

### Diagram

```text
       CLIENT
   (Presentation)
          |
          |
          v
    DATABASE SERVER
       (Data)
```

### Example

Ek simple desktop application directly database server se connect karti hai.

### Advantages

- Simple architecture.
- Small applications ke liye suitable.
- Easy initial setup.

### Disadvantages

- Scaling difficult ho sakti hai.
- Direct database access security risk create kar sakta hai.
- Business logic client side par hone se maintenance difficult ho sakta hai.

## 10. What is 3-Tier Architecture?

3-Tier Architecture application ko three logical layers mein divide karti hai:

1. Presentation Layer.
2. Application Layer.
3. Data Layer.

### 1. Presentation Layer

User Interface provide karti hai.

Examples:

- HTML.
- CSS.
- JavaScript.
- React.

### 2. Application Layer

Business logic aur request processing handle karti hai.

Examples:

- Node.js.
- Express.js.
- Java Spring Boot.
- Python Django.

### 3. Data Layer

Data store aur retrieve karti hai.

Examples:

- MongoDB.
- MySQL.
- PostgreSQL.

### Diagram

```text
       PRESENTATION LAYER
          (React UI)
               |
               v
       APPLICATION LAYER
       (Node + Express)
               |
               v
           DATA LAYER
            (MongoDB)
```

### Advantages

1. Better separation of concerns.
2. Easier maintenance.
3. Better security boundaries.
4. Independent scaling possible.
5. Reusability.

### Disadvantages

1. More components.
2. Deployment complexity.
3. Inter-layer communication overhead.

## 11. What is N-Tier Architecture?

N-Tier Architecture ek architecture hai jisme application ko multiple logical ya physical layers/tiers mein organize kiya jata hai.

N ka matlab number hai.

3-Tier architecture bhi N-Tier architecture ka ek example ho sakti hai.

### Example

```text
       PRESENTATION
            |
            v
       API GATEWAY
            |
            v
       APPLICATION
            |
            v
        BUSINESS
          LOGIC
            |
            v
       CACHE LAYER
            |
            v
       DATABASE LAYER
```

### Components

- Presentation Layer.
- API Gateway.
- Authentication Service.
- Application Services.
- Cache.
- Database.
- Message Queue.

### Advantages

- Scalability.
- Separation of responsibilities.
- Better maintainability.
- Independent deployment possible.
- Large applications ke liye suitable.

### Disadvantages

- Complex architecture.
- More infrastructure.
- Monitoring difficult ho sakta hai.
- Network communication overhead.

## 12. 2-Tier vs 3-Tier vs N-Tier

| Feature     | 2-Tier             | 3-Tier            | N-Tier                       |
| ----------- | ------------------ | ----------------- | ---------------------------- |
| Layers      | 2                  | 3                 | Multiple                     |
| Complexity  | Low                | Medium            | High                         |
| Maintenance | Limited separation | Better separation | More modular                 |
| Scalability | Limited            | Better            | Architecture-dependent       |
| Example     | Client + DB        | UI + App + DB     | UI + Gateway + Services + DB |

**Important:** Tiers ka matlab deployment levels hota hai, jabki layers logical responsibilities ko represent karti hain. Dono terms closely related hain, lekin exactly identical nahi.

## 13. What is Web Server?

Web Server ek software ya computer system hota hai jo HTTP/HTTPS requests handle karta hai aur web content serve karta hai.

### Examples

- Apache HTTP Server.
- Nginx.
- Microsoft IIS.
- Caddy.

### Functions

1. HTTP requests receive karna.
2. Static files serve karna.
3. Reverse proxy ka role perform karna.
4. TLS termination support karna.
5. Request routing aur logging.

## 14. What is Application Server?

Application Server application ki business logic aur processing execute karta hai.

Example:

- Node.js + Express.
- Java application server.
- Python application server.

### Web Server vs Application Server

| Web Server                         | Application Server                   |
| ---------------------------------- | ------------------------------------ |
| HTTP requests handle karta hai     | Application logic execute karta hai  |
| Static content serve kar sakta hai | Dynamic processing                   |
| Reverse proxy bhi ho sakta hai     | Business operations handle karta hai |
| Example: Nginx                     | Example: Node.js application         |

**Important:** Modern frameworks mein web server aur application server ke roles overlap kar sakte hain.

## 15. What is Database Server?

Database Server ek system ya service hoti hai jo data store, retrieve aur manage karti hai.

### Examples

- MongoDB.
- MySQL.
- PostgreSQL.
- Microsoft SQL Server.

### Functions

1. Data storage.
2. Data retrieval.
3. Query processing.
4. Access control.
5. Backup and recovery.
6. Data consistency.

## 16. What is Stateless Architecture?

Stateless Architecture mein server individual request ko process karne ke liye previous request ki in-memory session state par depend nahi karta.

Har request mein required context provide kiya jata hai ya external storage se retrieve kiya jata hai.

### Example

Ek API request mein authentication token bhejna.

```javascript
fetch("/api/profile", {
  headers: {
    Authorization: "Bearer YOUR_TOKEN",
  },
});
```

Server token verify karke request process karta hai.

### Benefits

- Horizontal scaling easier.
- Server replacement easier.
- Load balancing simpler.
- Server memory par session dependency reduce.

**Important:** Stateless ka matlab ye nahi ki application koi data store nahi karti. Application database ya external session store use kar sakti hai.

## 17. What is Stateful Architecture?

Stateful Architecture mein server previous interactions ya session information maintain karta hai.

### Example

Traditional server-side session:

1. User login karta hai.
2. Server session create karta hai.
3. Session ID client ko milti hai.
4. Client future requests mein session ID send karta hai.
5. Server stored session information verify karta hai.

### Stateless vs Stateful

| Stateless                                           | Stateful                                       |
| --------------------------------------------------- | ---------------------------------------------- |
| Previous request ki in-memory state par depend nahi | Session state maintain kar sakta hai           |
| Scaling comparatively easier                        | Shared session storage ki zarurat ho sakti hai |
| Token-based API common example                      | Server-side session common example             |
| Each request context carry karti hai                | Previous session context use hota hai          |

## 18. What is Horizontal Scaling?

Horizontal Scaling ka matlab system ki capacity increase karne ke liye additional servers/instances add karna hai.

### Example

```text
          LOAD BALANCER
                |
        -----------------
        |       |       |
        v       v       v
      SERVER  SERVER  SERVER
        A       B       C
```

### Advantages

- More traffic handle kar sakta hai.
- Availability improve ho sakti hai.
- Workload distribute hota hai.

## 19. What is Vertical Scaling?

Vertical Scaling ka matlab existing server ke resources increase karna hai.

Examples:

- More RAM.
- Faster CPU.
- More storage.
- Better hardware.

### Horizontal vs Vertical Scaling

| Horizontal Scaling                   | Vertical Scaling                              |
| ------------------------------------ | --------------------------------------------- |
| More servers add karna               | Existing server upgrade                       |
| Distributed workload                 | Single machine powerful                       |
| Load balancing useful                | Hardware limit important                      |
| Fault tolerance improve ho sakti hai | Single-server dependency remain kar sakti hai |

## 20. What is Load Balancing?

Load Balancing incoming requests ko multiple servers ke beech distribute karta hai.

### Purpose

- Traffic distribution.
- Better performance.
- High availability.
- Scalability.

### Common Algorithms

1. Round Robin.
2. Least Connections.
3. Weighted Round Robin.
4. IP Hash.

### Example

```text
          CLIENTS
              |
              v
        LOAD BALANCER
              |
      -----------------
      |       |       |
      v       v       v
    NODE 1  NODE 2  NODE 3
```

## 21. What is Microservices Architecture?

Microservices Architecture mein application ko small, independent services mein divide kiya jata hai.

Har service specific business capability handle karti hai.

### Example

E-commerce application:

- User Service.
- Product Service.
- Order Service.
- Payment Service.
- Notification Service.

### Diagram

```text
           CLIENT
              |
              v
          API GATEWAY
              |
      --------------------
      |        |         |
      v        v         v
    USER    PRODUCT    ORDER
   SERVICE  SERVICE   SERVICE
                         |
                         v
                   PAYMENT SERVICE
```

### Advantages

1. Independent deployment.
2. Independent scaling.
3. Team autonomy.
4. Fault isolation can improve.

### Disadvantages

1. Distributed system complexity.
2. Network failures.
3. Monitoring complexity.
4. Data consistency challenges.
5. Service communication overhead.

## 22. What is Monolithic Architecture?

Monolithic Architecture mein application ke major components ek single deployable application ke andar organized hote hain.

### Example

Ek application mein:

- Authentication.
- Product Management.
- Orders.
- Payments.

Sab ek application codebase/deployment ka part hain.

### Monolithic vs Microservices

| Monolithic                            | Microservices                              |
| ------------------------------------- | ------------------------------------------ |
| Single deployable application         | Multiple independently deployable services |
| Simple initial setup                  | Complex setup                              |
| Internal function calls common        | Network communication common               |
| Scaling usually application level par | Services independently scale ho sakti hain |
| Small projects ke liye useful         | Large distributed systems mein useful      |

**Important:** Monolithic architecture automatically bad nahi hoti. Small aur medium applications ke liye ye excellent choice ho sakti hai.

## 23. Network Architecture in MERN Stack

MERN Stack ka full form:

- MongoDB.
- Express.js.
- React.js.
- Node.js.

### Typical MERN Architecture

```text
          USER
           |
           v
       REACT FRONTEND
           |
           | HTTP/HTTPS
           v
      EXPRESS + NODE.JS
           |
           | Database Connection
           v
         MONGODB
```

### Working

1. User React application open karta hai.
2. User button click karta hai.
3. React API request send karta hai.
4. Express request receive karta hai.
5. Node.js business logic execute karta hai.
6. Backend MongoDB se data fetch karta hai.
7. Backend response return karta hai.
8. React UI update karta hai.

### Example Code

React frontend:

```javascript
async function getUsers() {
  const response = await fetch("/api/users");

  const data = await response.json();

  console.log(data);
}
```

Express backend:

```javascript
app.get("/api/users", async (req, res) => {
  const users = await User.find();

  res.json(users);
});
```

### Important Interview Point

React frontend directly database se connect nahi karna chahiye.

Generally React → Backend API → Database architecture follow ki jaati hai.

Isse database credentials aur business logic client se hidden rehte hain.

## 24. Common Mistakes

1. Client ko hamesha physical computer samajhna.
2. Server ko hamesha physical machine samajhna.
3. Client-Server aur Peer-to-Peer ko same samajhna.
4. 2-Tier aur 3-Tier architecture confuse karna.
5. Layer aur Tier ko exactly same samajhna.
6. Web Server aur Database Server ka role confuse karna.
7. Stateless ka matlab data store nahi hota samajhna.
8. Horizontal aur Vertical Scaling confuse karna.
9. Monolithic architecture ko outdated ya useless samajhna.
10. Microservices ko har project ke liye best samajhna.
11. React ko directly MongoDB se connect karna.
12. Load Balancer ko application server samajhna.

## 25. Important Interview Questions and Answers

### Q1. What is Network Architecture?

Network devices, services aur communication components ka design aur structure.

### Q2. What is Client-Server Architecture?

Ek model jisme client request karta hai aur server service provide karta hai.

### Q3. What is a Client?

Client ek device ya application hai jo server se services request karta hai.

### Q4. What is a Server?

Server ek computer ya software process hai jo clients ko services provide karta hai.

### Q5. What is Peer-to-Peer Architecture?

Aisa model jisme peers directly resources share kar sakte hain aur client/server roles perform kar sakte hain.

### Q6. What is 3-Tier Architecture?

Presentation, Application aur Data layers mein divided application architecture.

### Q7. What is N-Tier Architecture?

Multiple logical ya physical tiers mein organized architecture.

### Q8. What is a Web Server?

HTTP/HTTPS requests handle karke web content serve karne wala software/system.

### Q9. What is an Application Server?

Application logic aur processing execute karne wala server component.

### Q10. What is a Database Server?

Data store, retrieve aur manage karne wali service/system.

### Q11. What is Stateless Architecture?

Aisi architecture jisme request processing previous request ki in-memory session state par depend nahi karti.

### Q12. What is Stateful Architecture?

Aisi architecture jisme server client ki session state maintain kar sakta hai.

### Q13. What is Horizontal Scaling?

Capacity increase karne ke liye additional servers add karna.

### Q14. What is Vertical Scaling?

Existing server ke CPU, RAM ya other resources increase karna.

### Q15. What is Load Balancing?

Incoming traffic ko multiple servers ke beech distribute karna.

### Q16. What is Microservices Architecture?

Application ko small, independently deployable services mein divide karna.

### Q17. What is Monolithic Architecture?

Application ke major components ko ek single deployable application mein organize karna.

### Q18. What is the difference between Monolithic and Microservices?

Monolithic ek single deployable unit hota hai, jabki Microservices multiple independently deployable services hoti hain.

### Q19. Which architecture does MERN commonly follow?

MERN applications commonly three-tier style architecture follow karti hain: React presentation, Node/Express application logic aur MongoDB data layer.

### Q20. Why should frontend not connect directly to database?

Database credentials expose ho sakte hain aur authorization, validation aur business logic ko securely enforce karna difficult ho sakta hai.

## 26. Quick Revision

- Network Architecture = Network ka design.
- Client = Request karta hai.
- Server = Service provide karta hai.
- Client-Server = Request and response model.
- P2P = Peers resources share karte hain.
- 2-Tier = Client + Server/Database.
- 3-Tier = Presentation + Application + Data.
- N-Tier = Multiple tiers.
- Web Server = Web requests/content.
- Application Server = Business logic.
- Database Server = Data management.
- Stateless = Previous in-memory session state par dependency nahi.
- Stateful = Session state maintain hoti hai.
- Horizontal Scaling = More servers.
- Vertical Scaling = More resources.
- Load Balancer = Traffic distribution.
- Monolithic = Single deployable application.
- Microservices = Multiple independent services.
- MERN = MongoDB + Express + React + Node.js.

## 27. Practical Tasks

### Task 1: Client-Server Diagram

Ek browser aur web server ka diagram banao.

Explain:

- Request.
- Response.
- DNS.
- HTTP/HTTPS.

### Task 2: 3-Tier Architecture

MERN application ka diagram banao:

- React.
- Express + Node.js.
- MongoDB.

### Task 3: Architecture Comparison

2-Tier, 3-Tier aur N-Tier ke differences apne words mein likho.

### Task 4: Scaling

Ek application par traffic increase ho raha hai.

Explain:

- Horizontal scaling.
- Vertical scaling.
- Load balancing.

### Task 5: Monolithic vs Microservices

E-commerce application ka example lekar dono architectures explain karo.

### Task 6: Interview Practice

Bina notes dekhe explain karo:

1. Client-Server Architecture.
2. Peer-to-Peer Architecture.
3. Stateless vs Stateful.
4. Horizontal vs Vertical Scaling.
5. Monolithic vs Microservices.

---

# 28. Interview Practice Quiz – 10 Questions

**Q1. Client-Server Architecture mein request kaun send karta hai?**

A. Client  
B. Server  
C. Router  
D. Switch

**Q2. Server ka main role kya hai?**

A. Only data display karna  
B. Client ko services provide karna  
C. Keyboard control karna  
D. Monitor connect karna

**Q3. Peer-to-Peer Architecture mein kya hota hai?**

A. Only one client  
B. Peers directly resources share kar sakte hain  
C. Only database server  
D. No network communication

**Q4. 3-Tier Architecture mein kaunsi layers hoti hain?**

A. CPU, RAM, ROM  
B. Presentation, Application, Data  
C. Input, Output, Storage  
D. Client, Router, Switch

**Q5. React MERN architecture mein kis layer ka part hai?**

A. Presentation Layer  
B. Data Layer  
C. Physical Layer  
D. Network Cable

**Q6. Horizontal Scaling ka matlab kya hai?**

A. RAM remove karna  
B. More servers add karna  
C. Screen size increase karna  
D. Database delete karna

**Q7. Vertical Scaling ka matlab kya hai?**

A. Existing server ke resources increase karna  
B. More users delete karna  
C. More routers connect karna  
D. Application uninstall karna

**Q8. Load Balancer ka purpose kya hai?**

A. Traffic distribute karna  
B. Database permanently delete karna  
C. Password display karna  
D. Monitor control karna

**Q9. Microservices Architecture mein application kaise organized hoti hai?**

A. Single HTML file mein  
B. Small independent services mein  
C. Only database mein  
D. Only browser mein

**Q10. MERN application mein React normally data kahan se receive karta hai?**

A. Direct MongoDB se  
B. Backend API se  
C. BIOS se  
D. RAM se

### Answer Key

1. A – Client
2. B – Client ko services provide karna
3. B – Peers directly resources share kar sakte hain
4. B – Presentation, Application, Data
5. A – Presentation Layer
6. B – More servers add karna
7. A – Existing server ke resources increase karna
8. A – Traffic distribute karna
9. B – Small independent services mein
10. B – Backend API se

---

# Topic 27 Completed – Network Architecture and Client-Server Model
