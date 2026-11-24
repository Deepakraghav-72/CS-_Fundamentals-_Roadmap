# Topic 04: Client-Server Architecture

## 1. Client-Server Architecture Kya Hai?

Client-Server Architecture ek software architecture model hai jisme application ke do main parts hote hain:

1. Client
2. Server

**Client:** Client wo device ya application hoti hai jo server ko request bhejti hai aur response receive karti hai.

**Server:** Server wo computer ya software hota hai jo client ki request receive karta hai, process karta hai aur response return karta hai.

### Real-Life Example

Jab tum browser mein YouTube open karte ho:

1. Tumhara browser YouTube server ko request bhejta hai.
2. Server request receive karta hai.
3. Server required data process karta hai.
4. Server browser ko response bhejta hai.
5. Browser tumhe YouTube page show karta hai.

## 2. Client Kya Hota Hai?

Client ek application ya device hota hai jo kisi service ya resource ke liye server se request karta hai.

### Client Examples

- Web Browser (Chrome, Firefox)
- Mobile Application
- Desktop Application
- React Frontend
- Smart TV Application

**Example:**

Jab tum React application mein Login button click karte ho, frontend backend server ko login request bhejta hai.

## 3. Server Kya Hota Hai?

Server ek computer ya software hota hai jo clients ki requests receive aur process karta hai.

Server ke main tasks:

- Client ki request receive karna.
- Request validate karna.
- Business logic execute karna.
- Database se data read/write karna.
- Client ko response return karna.

### Server Examples

- Node.js Server
- Express.js Server
- Apache HTTP Server
- Nginx
- Database Server

**Important:** Server sirf ek physical computer nahi hota. Server ek software program bhi ho sakta hai jo kisi computer par requests handle karta hai.

## 4. Client-Server Architecture Kaise Work Karti Hai?

Is architecture mein communication generally request-response model par hota hai.

### Step-by-Step Working

Example: User login karta hai.

1. User React frontend par email aur password enter karta hai.
2. User Login button click karta hai.
3. React backend ko HTTP request bhejta hai.
4. Backend request receive karta hai.
5. Backend input validate karta hai.
6. Backend database se user information check karta hai.
7. Backend authentication result generate karta hai.
8. Backend client ko response return karta hai.
9. React response ke according dashboard ya error message show karta hai.

### Architecture Diagram

```text
       USER
         |
         v
   CLIENT (React)
         |
         | HTTP Request
         v
   SERVER (Node.js/
     Express.js)
         |
         v
      DATABASE
      (MongoDB)
         |
         v
   SERVER PROCESSES
      THE RESULT
         |
         | HTTP Response
         v
   CLIENT (React)
         |
         v
   RESULT TO USER
```

## 5. Request and Response Kya Hote Hain?

### Request

Client jab server se koi information ya service maangta hai, use request kehte hain.

Example:

```http
GET /api/users
```

Meaning: Client server se users ka data maang raha hai.

### Response

Server request process karne ke baad client ko jo result bhejta hai, use response kehte hain.

Example:

```json
{
  "message": "Users fetched successfully",
  "users": [
    {
      "name": "Rahul"
    },
    {
      "name": "Aman"
    }
  ]
}
```

Response mein status code, headers aur optional body ho sakti hai.

## 6. Client-Server Communication Mein HTTP Ka Role

HTTP ka full form **Hypertext Transfer Protocol** hai.

HTTP ek application-layer protocol hai jo client aur server ke beech request-response communication enable karta hai.

Example:

```text
Client  ---- HTTP Request ----> Server

Client  <--- HTTP Response --- Server
```

Common HTTP methods:

| Method | Purpose                         |
| ------ | ------------------------------- |
| GET    | Data fetch karna                |
| POST   | Data create/send karna          |
| PUT    | Resource update/replace karna   |
| PATCH  | Resource partially update karna |
| DELETE | Resource delete karna           |

HTTPS, HTTP ka secure version hai jo TLS encryption use karta hai.

HTTP aur HTTPS ko hum aage detail mein padhenge.

## 7. Types of Client-Server Architecture

### 1. Two-Tier Architecture

Is architecture mein client directly database server ke saath communicate karta hai.

```text
+------------------+
|      CLIENT      |
|  UI + Application|
+------------------+
         |
         |
         v
+------------------+
|  DATABASE SERVER |
+------------------+
```

Example:

- Simple desktop application.
- Small internal applications.

**Advantages:**

- Simple architecture.
- Easy to develop for small systems.
- Fewer components.

**Disadvantages:**

- Client directly database access karta hai.
- Security manage karna difficult ho sakta hai.
- Large-scale applications ke liye suitable nahi hota.
- Business logic multiple clients mein duplicate ho sakta hai.

### 2. Three-Tier Architecture

Is architecture mein three layers hoti hain:

1. Presentation Layer
2. Application Layer
3. Data Layer

```text
+----------------------+
|  PRESENTATION LAYER  |
|      (React)         |
+----------------------+
           |
           v
+----------------------+
|  APPLICATION LAYER   |
| (Node.js + Express)  |
+----------------------+
           |
           v
+----------------------+
|      DATA LAYER      |
|      (MongoDB)       |
+----------------------+
```

**Presentation Layer:**
User interface handle karti hai.

Example: React frontend.

**Application Layer:**
Business logic aur request processing handle karti hai.

Example: Node.js + Express.js backend.

**Data Layer:**
Application ka data store aur retrieve karti hai.

Example: MongoDB.

**Advantages:**

- Better separation of responsibilities.
- Security manage karna easier.
- Maintenance easier.
- Application ko independently modify karna easier.

**Disadvantages:**

- Two-tier ke comparison mein complexity zyada.
- Multiple layers ke beech communication overhead ho sakta hai.

### 3. N-Tier Architecture

N-Tier Architecture mein application ko multiple independent layers ya tiers mein divide kiya jata hai.

Example:

```text
       CLIENT
          |
          v
    WEB SERVER
          |
          v
    API GATEWAY
          |
          v
   APPLICATION SERVER
          |
     +----+-----+
     |          |
     v          v
   CACHE     DATABASE
```

Real-world applications mein authentication, caching, payment, notification aur other services ke liye separate components ho sakte hain.

**Advantages:**

- Better separation.
- Independent scaling possible.
- Large applications ko manage karna easier ho sakta hai.

**Disadvantages:**

- Architecture complex ho sakti hai.
- Deployment aur monitoring difficult ho sakte hain.
- Network communication overhead increase ho sakta hai.

**Note:** Two-tier, three-tier aur N-tier application layers/tiers ko describe karte hain. Ye monolithic aur microservices architecture ke exactly same concepts nahi hain.

## 8. Client-Server Architecture vs Peer-to-Peer Architecture

### Peer-to-Peer (P2P) Architecture

Peer-to-Peer architecture mein devices (peers) directly ek dusre ke saath resources share kar sakte hain.

Har peer resources provide bhi kar sakta hai aur receive bhi.

Example:

- BitTorrent file sharing.

### Difference

| Client-Server                                | Peer-to-Peer                                                            |
| -------------------------------------------- | ----------------------------------------------------------------------- |
| Central server important role play karta hai | Peers directly communicate kar sakte hain                               |
| Client request karta hai                     | Peer request bhi kar sakta hai aur serve bhi                            |
| Central management easier                    | Management distributed hota hai                                         |
| Server bottleneck ban sakta hai              | Load peers mein distribute ho sakta hai                                 |
| Server failure service affect kar sakta hai  | Architecture ke according peers ke paas alternate sources ho sakte hain |

## 9. Stateless vs Stateful Server

### Stateless Server

Stateless server har request ko independently process karta hai.

Server ko previous request ki application state yaad rakhna necessary nahi hota.

Example:
Client har protected request ke saath valid authentication token bhejta hai. Server token verify karke request process karta hai.

### Stateful Server

Stateful server client ki session ya application state ko requests ke beech maintain karta hai.

Example:
Traditional server-side session-based login.

### Difference

| Stateless                                              | Stateful                                        |
| ------------------------------------------------------ | ----------------------------------------------- |
| Previous request ki state par depend nahi karta        | Stored state maintain karta hai                 |
| Scaling easier ho sakti hai                            | Session management ki zaroorat ho sakti hai     |
| Har request mein required context bhejna pad sakta hai | Server/session store context maintain karta hai |
| Example: Token-based API design                        | Example: Server-side session                    |

**Important:** Stateful systems mein session data shared store mein rakhkar multiple servers ke saath scaling possible hai. Stateless ka matlab ye nahi ki application mein koi state exist hi nahi karti.

## 10. Client-Server Architecture Ke Advantages

1. **Centralized Management:** Server side par application logic aur data manage kiya ja sakta hai.
2. **Security:** Database ko directly public client se expose karne ki zaroorat nahi hoti.
3. **Maintenance:** Backend logic ko central place par update kiya ja sakta hai.
4. **Resource Sharing:** Multiple clients same server resources use kar sakte hain.
5. **Scalability:** Infrastructure ko requirements ke according scale kiya ja sakta hai.

## 11. Client-Server Architecture Ke Disadvantages

1. **Server Failure:** Single server par dependency hone se failure service ko unavailable kar sakta hai.
2. **Network Dependency:** Communication ke liye network required hota hai.
3. **Server Overload:** Bahut saari requests server ko slow kar sakti hain.
4. **Maintenance Cost:** Servers ko maintain karne ke liye resources chahiye.
5. **Network Latency:** Client aur server ke beech communication mein delay ho sakta hai.

## 12. MERN Stack Mein Client-Server Architecture

MERN ka full form:

- M = MongoDB
- E = Express.js
- R = React.js
- N = Node.js

### MERN Architecture Diagram

```text
        USER
          |
          v
   REACT FRONTEND
       (Client)
          |
          | HTTP Request
          v
    EXPRESS SERVER
          |
          v
      NODE.JS
    (Runtime)
          |
          v
       MONGODB
      (Database)
          |
          v
    RESPONSE BACK
          |
          v
    REACT FRONTEND
          |
          v
       USER
```

### Example: MERN Login Flow

1. User React form mein email/password enter karta hai.
2. React `fetch()` ya Axios se API request bhejta hai.
3. Express route request receive karta hai.
4. Node.js environment mein backend code execute hota hai.
5. Backend MongoDB se user record check karta hai.
6. Password hash verify hota hai.
7. Backend appropriate response bhejta hai.
8. React success ya error show karta hai.

### Simple Code Example

**Client Side (React / JavaScript):**

```javascript
async function getUsers() {
  const response = await fetch("http://localhost:5000/api/users");

  const data = await response.json();

  console.log(data);
}

getUsers();
```

**Server Side (Node.js + Express):**

```javascript
const express = require("express");

const app = express();

app.get("/api/users", (req, res) => {
  res.json([{ name: "Rahul" }, { name: "Aman" }]);
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

Client `/api/users` par GET request bhejta hai aur Express server JSON response return karta hai.

_Note: Ye basic demonstration hai. Production application mein CORS, error handling, validation aur security bhi configure karni hoti hai._

## 13. Important Terms

| Term     | Meaning                                              |
| -------- | ---------------------------------------------------- |
| Client   | Request bhejne wala application/device               |
| Server   | Request process karne wala software/computer         |
| Request  | Client se server ko bheja gaya message               |
| Response | Server se client ko bheja gaya result                |
| HTTP     | Communication protocol                               |
| API      | Software components ke beech communication interface |
| Frontend | User interface                                       |
| Backend  | Server-side logic                                    |
| Database | Data store karne ka system                           |
| Latency  | Request-response mein hone wala delay                |

## 14. Common Mistakes

1. Client aur server ko same samajhna.
2. Ye samajhna ki server hamesha ek physical machine hota hai.
3. Frontend se directly database connect karna in a typical secure web architecture.
4. HTTP request aur response ka difference bhoolna.
5. Three-tier architecture ko microservices samajhna.
6. Stateless ka matlab application mein state nahi hai, aisa samajhna.
7. Ye assume karna ki har server request database tak zaroor jaati hai. Caching se response mil sakta hai.

## 15. Interview Questions and Answers

**Q1. What is Client-Server Architecture?**

Ans: It is an architecture in which clients send requests to servers, and servers process those requests and return responses.

**Q2. What is a client?**

Ans: A client is an application or device that requests services or resources from a server.

**Q3. What is a server?**

Ans: A server is software or a computer that receives and processes client requests.

**Q4. What is the difference between two-tier and three-tier architecture?**

Ans: Two-tier architecture generally has a client and database tier, whereas three-tier architecture separates presentation, application logic and data layers.

**Q5. What is N-Tier Architecture?**

Ans: It is an architecture in which an application is divided into multiple logical layers or physical tiers.

**Q6. What is Peer-to-Peer Architecture?**

Ans: It is a distributed architecture in which peers can communicate and share resources directly.

**Q7. What is the difference between stateless and stateful servers?**

Ans: Stateless servers process requests independently, while stateful servers maintain relevant state across requests.

**Q8. What happens if a server goes down?**

Ans: Clients may fail to get responses from that server. Redundant servers and failover mechanisms can help maintain availability.

**Q9. Why is the database generally not directly connected to the browser?**

Ans: Exposing database credentials and direct database access to public clients creates serious security risks. A backend server safely manages database operations.

## 16. Practical Tasks

### Task 1: Draw Architecture

Ek simple MERN application ka diagram banao:

- React
- Express
- Node.js
- MongoDB

### Task 2: Explain Request-Response

Apne words mein explain karo ki jab user login karta hai to client aur server ke beech kya hota hai.

### Task 3: Identify Architecture

In examples mein architecture identify karo:

1. Browser → Backend → Database
2. Desktop App → Database
3. Multiple computers directly sharing files

### Task 4: Coding Practice

Upar diya gaya Express server run karo aur browser mein ye URL open karo:

`http://localhost:5000/api/users`

JSON response observe karo.

## 17. Quick Revision

- Client = Request bhejta hai.
- Server = Request process karta hai.
- Request = Client to Server.
- Response = Server to Client.
- HTTP = Client-server communication protocol.
- Two-Tier = Client + Database.
- Three-Tier = Presentation + Application + Data.
- N-Tier = Multiple layers/tiers.
- P2P = Peers directly resources share kar sakte hain.
- Stateless = Requests independently process hoti hain.
- Stateful = State requests ke beech maintain hoti hai.
- MERN = React + Express + Node.js + MongoDB.

## 18. Topic Completion Checklist

- [ ] Client kya hota hai?
- [ ] Server kya hota hai?
- [ ] Request and Response
- [ ] HTTP communication
- [ ] Two-Tier Architecture
- [ ] Three-Tier Architecture
- [ ] N-Tier Architecture
- [ ] Peer-to-Peer Architecture
- [ ] Stateless vs Stateful
- [ ] MERN Architecture
