# Topic 06: Client-Server Architecture

## 1. Client-Server Architecture Kya Hai?

Client-Server Architecture ek software architecture model hai jisme application ke do main parts hote hain:

1. Client
2. Server

**Client:** Client wo device ya application hoti hai jo server ko request bhejti hai aur response receive karti hai.

**Server:** Server wo system hota hai jo client ki request receive karta hai, process karta hai aur response return karta hai.

### Simple Example

Maan lo tum Chrome browser mein YouTube open karte ho.

- Chrome = Client
- YouTube ka backend = Server
- Video aur user data = Server/database/storage se aane wala data

Jab tum YouTube par video search karte ho, browser server ko request bhejta hai. Server search process karta hai aur results wapas bhejta hai.

## 2. Client Kya Hota Hai?

Client ek application ya device hota hai jo kisi server se service ya data request karta hai.

### Client ke Examples

- Web Browser (Chrome, Firefox)
- Mobile Application
- Desktop Application
- Smart TV Application
- Frontend Website

### Client ke Main Responsibilities

1. User Interface show karna.
2. User se input lena.
3. Server ko requests bhejna.
4. Server ka response receive karna.
5. Data ko user ke saamne display karna.

### Example

Jab tum login form mein email aur password enter karte ho, frontend ye information backend server ko bhejta hai.

## 3. Server Kya Hota Hai?

Server ek computer ya software program hota hai jo clients ki requests receive aur process karta hai.

Server ka kaam sirf data bhejna nahi hota. Ye business logic execute kar sakta hai, authentication check kar sakta hai aur database se communicate kar sakta hai.

### Server ke Main Responsibilities

1. Client requests receive karna.
2. Request validate karna.
3. Business logic execute karna.
4. Database se data read/write karna.
5. Client ko response bhejna.
6. Errors handle karna.

### Example

Jab user login karta hai:

- Server email aur password receive karta hai.
- Database mein user search karta hai.
- Password verify karta hai.
- Login successful ya failed response return karta hai.

## 4. Client-Server Architecture Kaise Work Karti Hai?

Is architecture mein communication generally request-response model follow karti hai.

### Working Flow

1. User browser mein website open karta hai.
2. Client server ko request bhejta hai.
3. Server request receive karta hai.
4. Server required processing karta hai.
5. Zarurat hone par database se data leta hai.
6. Server response generate karta hai.
7. Client response receive karta hai.
8. Browser user ko result display karta hai.

### Architecture Diagram

```text
        USER
          |
          v
   +--------------+
   |    CLIENT    |
   | Chrome/React |
   +--------------+
          |
          | HTTP Request
          v
   +--------------+
   |    SERVER    |
   | Node/Express |
   +--------------+
          |
          | Database Query
          v
   +--------------+
   |   DATABASE   |
   |   MongoDB    |
   +--------------+
          |
          | Data
          v
   +--------------+
   |    SERVER    |
   +--------------+
          |
          | HTTP Response
          v
   +--------------+
   |    CLIENT    |
   +--------------+
          |
          v
     USER RESULT
```

## 5. Request and Response Kya Hote Hain?

Client-server communication mein do important terms hain:

### Request

Jab client server se koi data ya service maangta hai, use request kehte hain.

Examples:

- Login request
- Profile fetch request
- Product search request
- New post create request

### Response

Server jab client ki request process karke result return karta hai, use response kehte hain.

Example:

Client Request:

```http
GET /api/users/101
```

Server Response:

```json
{
  "id": 101,
  "name": "Rahul",
  "role": "Student"
}
```

Yahan client ne user details maangi aur server ne user data return kiya.

## 6. HTTP Kya Hai?

HTTP ka full form hai HyperText Transfer Protocol.

HTTP ek communication protocol hai jo client aur server ke beech data exchange karne ke liye use hota hai.

### HTTP Methods

| Method | Use                                       |
| ------ | ----------------------------------------- |
| GET    | Data receive karna                        |
| POST   | New data create/send karna                |
| PUT    | Existing resource ko replace/update karna |
| PATCH  | Resource ka partial update karna          |
| DELETE | Data delete karna                         |

### Example

```http
GET /api/products
POST /api/products
PUT /api/products/10
PATCH /api/products/10
DELETE /api/products/10
```

Note: Actual API mein method ka behaviour backend implementation aur API contract par depend karta hai.

## 7. HTTPS Kya Hai?

HTTPS ka full form hai HyperText Transfer Protocol Secure.

HTTPS, HTTP ka secure version hai. Ye TLS encryption ka use karke client aur server ke beech communication ko protect karta hai.

### HTTP vs HTTPS

| HTTP                                          | HTTPS                                     |
| --------------------------------------------- | ----------------------------------------- |
| Data encrypted nahi hota by default           | Data TLS se encrypted hota hai            |
| Less secure                                   | More secure                               |
| Usually port 80                               | Usually port 443                          |
| Sensitive communication ke liye suitable nahi | Sensitive communication ke liye preferred |

Example:

```text
http://example.com
https://example.com
```

Real-world websites mein HTTPS use karna important hai.

## 8. Client-Server Architecture Ke Types

Client-server architecture ko different layers ke basis par samajh sakte hain.

### A. Two-Tier Architecture

Is architecture mein client directly server/database layer ke saath communicate karta hai.

```text
+------------------+
|      CLIENT      |
|   UI + Logic     |
+------------------+
         |
         |
         v
+------------------+
| SERVER / DATABASE|
+------------------+
```

Example:

- Simple desktop application connected to a database server.

Limitation:

- Application grow hone par maintenance aur security difficult ho sakti hai.
- Client ko database access dena risky ho sakta hai.

### B. Three-Tier Architecture

Is architecture mein application ko three layers mein divide kiya jata hai:

1. Presentation Layer
2. Application Layer
3. Database Layer

```text
+----------------------+
|  PRESENTATION LAYER  |
|    React Frontend    |
+----------------------+
           |
           v
+----------------------+
|  APPLICATION LAYER   |
|   Node + Express     |
|    Business Logic    |
+----------------------+
           |
           v
+----------------------+
|     DATABASE LAYER   |
|       MongoDB        |
+----------------------+
```

**Presentation Layer:** User interface handle karti hai.

**Application Layer:** Business logic aur API requests handle karti hai.

**Database Layer:** Application ka data store karti hai.

Example: MERN Stack application.

### C. N-Tier Architecture

Jab application ko three se zyada logical ya physical layers/services mein divide kiya jata hai, use broadly N-Tier Architecture kaha jata hai.

Example:

```text
CLIENT
  |
  v
LOAD BALANCER
  |
  v
API SERVER
  |
  v
APPLICATION SERVICES
  |
  +------> CACHE
  |
  +------> DATABASE
  |
  +------> FILE STORAGE
```

Large applications mein different responsibilities ko separate karne ke liye ye approach useful hoti hai.

Note: N-tier architecture aur microservices same cheez nahi hain. N-tier layers ko describe karta hai, jabki microservices independently deployable services ko describe karta hai.

## 9. Stateless vs Stateful Server

### Stateless Server

Stateless server har request ko independently process karta hai.

Server ko previous request ka session state apne local memory mein maintain karna zaroori nahi hota.

Example:

- Client har request ke saath valid authentication token bhejta hai.
- Server token verify karke request process karta hai.

Advantages:

- Horizontal scaling easier ho sakti hai.
- Multiple servers ke beech requests distribute karna easier hota hai.

### Stateful Server

Stateful server client ki session ya previous interaction se related state maintain karta hai.

Example:

- Server local memory mein user session maintain karta hai.

Advantages:

- Session-related information easily available ho sakti hai.

Disadvantages:

- Server change hone par session access ka issue aa sakta hai.
- Scaling ke liye shared session storage ya sticky sessions ki zarurat pad sakti hai.

### Difference

| Stateless                                | Stateful                                 |
| ---------------------------------------- | ---------------------------------------- |
| Request independently process hoti hai   | Previous session state maintain hoti hai |
| Local session memory par dependency nahi | Session state maintain hoti hai          |
| Scaling generally easier                 | Scaling more complex ho sakti hai        |
| Token-based API common example           | Server-side session common example       |

## 10. Client-Server Architecture Ke Advantages

1. **Separation of Responsibilities:** Client aur server ke tasks separate hote hain.
2. **Centralized Data:** Data ko central server/database par manage kiya ja sakta hai.
3. **Security:** Sensitive business logic aur database access server par rakhe ja sakte hain.
4. **Maintenance:** Backend aur frontend ko independently update kiya ja sakta hai.
5. **Scalability:** Traffic badhne par server infrastructure scale kiya ja sakta hai.
6. **Multiple Clients:** Same backend ko web, mobile aur desktop clients use kar sakte hain.

## 11. Client-Server Architecture Ke Disadvantages

1. **Network Dependency:** Client-server communication ke liye network connection chahiye.
2. **Server Failure:** Server unavailable hua to service impact ho sakti hai.
3. **Network Latency:** Request aur response mein time lag sakta hai.
4. **Server Cost:** Traffic badhne par infrastructure cost increase ho sakti hai.
5. **Security Risks:** Poor authentication ya insecure APIs se attacks ho sakte hain.

## 12. Real-World Example: Online Shopping Application

Maan lo tum Amazon jaisi shopping application use kar rahe ho.

### Step-by-Step Flow

1. User React website open karta hai.
2. React frontend backend API ko request bhejta hai.
3. Express server request receive karta hai.
4. Server MongoDB se products fetch karta hai.
5. MongoDB product details return karta hai.
6. Express response React ko bhejta hai.
7. React products user ko display karta hai.

### Diagram

```text
       USER
         |
         v
   REACT FRONTEND
         |
         | GET /api/products
         v
   EXPRESS SERVER
         |
         v
      MONGODB
         |
         | Product Data
         v
   EXPRESS SERVER
         |
         | JSON Response
         v
   REACT FRONTEND
         |
         v
  PRODUCTS DISPLAY
```

## 13. MERN Stack Mein Client-Server Architecture

MERN ka full form:

- M = MongoDB
- E = Express.js
- R = React.js
- N = Node.js

| MERN Technology | Responsibility                 |
| --------------- | ------------------------------ |
| React           | Client / Frontend              |
| Node.js         | JavaScript Runtime for Backend |
| Express.js      | Backend Web Framework          |
| MongoDB         | Database                       |

Important:

Node.js khud database nahi hai. Ye JavaScript runtime hai jo server-side JavaScript run karta hai.

Express.js Node.js par web server aur APIs build karne mein help karta hai.

### Example Code

React Client:

```javascript
fetch("http://localhost:5000/api/users")
  .then((response) => response.json())
  .then((data) => console.log(data));
```

Express Server:

```javascript
const express = require("express");

const app = express();

app.get("/api/users", (req, res) => {
  res.json([
    { id: 1, name: "Rahul" },
    { id: 2, name: "Aman" },
  ]);
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

Yahan:

- React client request bhej raha hai.
- Express server request receive kar raha hai.
- Server JSON response return kar raha hai.

## 14. Important Interview Questions

**Q1. What is Client-Server Architecture?**

Ans: It is an architecture in which a client sends requests to a server, and the server processes those requests and returns responses.

**Q2. What is a Client?**

Ans: A client is an application or device that requests services or data from a server.

**Q3. What is a Server?**

Ans: A server is a computer or software program that receives and processes client requests.

**Q4. What is HTTP?**

Ans: HTTP is a protocol used for communication between clients and servers.

**Q5. What is HTTPS?**

Ans: HTTPS is the secure version of HTTP that uses TLS encryption.

**Q6. What is Three-Tier Architecture?**

Ans: It divides an application into presentation, application, and database layers.

**Q7. What is the difference between Stateless and Stateful servers?**

Ans: Stateless servers process requests independently without depending on locally stored session state, while stateful servers maintain session-related state.

**Q8. What is Request-Response Communication?**

Ans: It is a communication pattern where the client sends a request and the server returns a response.

**Q9. Can multiple clients use the same server?**

Ans: Yes. Web browsers, mobile applications, and desktop applications can use the same backend services.

**Q10. Is React a client or server?**

Ans: In a typical MERN application, React runs on the client side. React can also support server rendering in other architectures.

## 15. Practical Assignment

### Task 1: Identify Client and Server

In examples mein client aur server identify karo:

1. YouTube video play karna.
2. Online shopping website par product search karna.
3. Mobile banking application mein balance check karna.

### Task 2: Draw Architecture

Ek simple MERN application ka diagram banao:

```text
React
  |
  v
Express + Node.js
  |
  v
MongoDB
```

### Task 3: Coding Practice

Ek Express API banao:

```text
GET /api/products
```

Aur JSON format mein 3 products return karo.

### Task 4: Explain in Your Own Words

Khud explain karo:

- Client kya hota hai?
- Server kya hota hai?
- Request kya hoti hai?
- Response kya hota hai?
- Three-tier architecture kya hai?

## 16. Quick Revision

- Client = Request bhejne wala application/device.
- Server = Request process karne wala system.
- Request = Client ki demand.
- Response = Server ka result.
- HTTP = Client-server communication protocol.
- HTTPS = HTTP + TLS security.
- Two-Tier = Two main layers.
- Three-Tier = Presentation + Application + Database.
- N-Tier = Multiple layers.
- Stateless = Requests independently process hoti hain.
- Stateful = Session state maintain hoti hai.
- React = Typical MERN client.
- Express + Node.js = Typical MERN backend.
- MongoDB = Database.

**Topic 06 Complete: Client-Server Architecture**

Next Topic: Topic 07 – Monolithic vs Microservices Architecture.
