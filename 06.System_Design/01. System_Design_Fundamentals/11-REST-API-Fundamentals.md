# Topic 11: REST API Fundamentals

## 1. API Kya Hai?

API ka full form **Application Programming Interface** hai.

API ek interface hai jiske through two software applications ek doosre ke saath communicate kar sakti hain.

Simple words mein:

**API = Do applications ke beech communication ka medium.**

### Real-Life Example

Socho tum restaurant mein khana order karte ho.

1. Tum customer ho.
2. Kitchen food prepare karta hai.
3. Waiter tumhara order kitchen tak pahunchata hai.
4. Kitchen food prepare karke waiter ko deta hai.
5. Waiter tumhe food serve karta hai.

Yahan waiter ko API ki tarah samajh sakte hain.

```text
       CUSTOMER
           |
           | Order
           v
         WAITER
           |
           | Order Details
           v
         KITCHEN
           |
           | Prepared Food
           v
         WAITER
           |
           v
        CUSTOMER
```

Ye ek simplified analogy hai. Real API software systems ke beech defined rules ke according communication karati hai.

## 2. API Ki Zaroorat Kyu Hoti Hai?

Aaj ke time mein different applications ko ek doosre ke saath communicate karna hota hai.

Examples:

- React frontend ko Node.js backend se data chahiye.
- Mobile application ko server se user details chahiye.
- Payment application ko payment gateway se communicate karna hota hai.
- E-commerce application ko delivery service se communicate karna hota hai.

API ke bina different applications ke beech standardized communication difficult ho sakta hai.

## 3. API Kaise Work Karti Hai?

Example: User apni profile dekhna chahta hai.

```text
       USER
         |
         v
    REACT FRONTEND
         |
         | API Request
         v
    EXPRESS BACKEND
         |
         v
       MONGODB
         |
         | User Data
         v
    EXPRESS BACKEND
         |
         | API Response
         v
    REACT FRONTEND
         |
         v
     USER PROFILE
```

Steps:

1. User React frontend par profile button click karta hai.
2. React API request send karta hai.
3. Express backend request receive karta hai.
4. Backend MongoDB se user data fetch karta hai.
5. Backend JSON response return karta hai.
6. React response receive karke profile display karta hai.

## 4. REST Kya Hai?

REST ka full form **Representational State Transfer** hai.

REST ek architectural style hai jo network-based applications ke liye design principles define karta hai.

REST ko Roy Fielding ne 2000 mein apni doctoral dissertation mein describe kiya tha.

Simple words mein:

**REST = APIs design karne ka ek architectural style.**

REST API banate time kuch principles follow kiye jaate hain.

REST khud programming language, framework ya protocol nahi hai.

## 5. REST API Kya Hai?

REST API ek API hoti hai jo REST architectural constraints follow karti hai.

Example:

```text
GET    /api/users
GET    /api/users/10
POST   /api/users
PUT    /api/users/10
PATCH  /api/users/10
DELETE /api/users/10
```

Yahan:

- `/api/users` = Users resource.
- `/api/users/10` = Particular user resource.
- GET = Resource retrieve karna.
- POST = Resource create karna.
- PUT/PATCH = Resource update karna.
- DELETE = Resource delete karna.

Ye REST-style endpoints ke examples hain.

## 6. Resource Kya Hota Hai?

REST mein resource ek important concept hai.

Resource kisi bhi object ya data ko represent karta hai jise API ke through access kiya ja sakta hai.

Examples:

- User
- Product
- Order
- Payment
- Course
- Student
- Book

Example:

```text
/api/users
/api/products
/api/orders
/api/courses
```

Yahan:

- `/users` = Users collection.
- `/products` = Products collection.
- `/orders` = Orders collection.

## 7. REST API Ke Important Principles

REST ke 6 architectural constraints hain.

### 1. Client-Server Architecture

Client aur server ki responsibilities separate honi chahiye.

Example:

- React = Frontend/client.
- Express = Backend/server.
- MongoDB = Database.

```text
CLIENT                 SERVER
React       <------>   Express
```

Benefits:

- Independent development.
- Better separation of responsibilities.
- Frontend aur backend separately maintain ho sakte hain.

### 2. Statelessness

REST mein har request mein server ko request process karne ke liye required information provide honi chahiye.

Server previous request ki application state ko automatically remember karne par depend nahi karta.

Example:

```http
GET /api/profile HTTP/1.1
Authorization: Bearer ACCESS_TOKEN
```

Client request ke saath authentication token bhejta hai.

Server token validate karke user identify kar sakta hai.

Important:

Statelessness ka matlab ye nahi ki server ke paas database ya persistent data nahi ho sakta. Server user data aur application data store kar sakta hai.

### 3. Cacheability

REST responses ko caching ke liye rules define karne chahiye.

Example:

Product list frequently access hoti hai.

Agar response cacheable hai, to eligible cache us response ko reuse kar sakta hai.

Benefits:

- Server load reduce.
- Response time improve.
- Network traffic reduce.

### 4. Uniform Interface

Client aur server ke beech communication consistent rules follow kare.

Iske important parts:

- Resources ko identify karna.
- Resources ko representations ke through manipulate karna.
- Self-descriptive messages.
- Hypermedia as the Engine of Application State (HATEOAS).

Example:

```http
GET /api/users/10
```

Response:

```json
{
  "id": 10,
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

### 5. Layered System

Client ko ye pata hona zaroori nahi ki request directly server tak ja rahi hai ya beech mein proxy, gateway ya load balancer hai.

Example:

```text
CLIENT
   |
   v
LOAD BALANCER
   |
   v
API GATEWAY
   |
   v
BACKEND SERVER
   |
   v
DATABASE
```

Benefits:

- Better scalability.
- Security layers.
- Flexible architecture.

### 6. Code on Demand (Optional)

Server client ko executable code bhej sakta hai jise client execute kare.

Example:

- JavaScript code browser ko bhejna.

Ye REST ka optional constraint hai.

## 8. REST API HTTP Methods Kaise Use Karti Hai?

REST APIs commonly HTTP methods use karti hain.

| Method | Action         | Example                   |
| ------ | -------------- | ------------------------- |
| GET    | Read           | Users fetch karna         |
| POST   | Create         | New user banana           |
| PUT    | Replace        | User replace karna        |
| PATCH  | Partial update | User ka name update karna |
| DELETE | Delete         | User delete karna         |

Example:

```text
GET     /api/products
GET     /api/products/5
POST    /api/products
PUT     /api/products/5
PATCH   /api/products/5
DELETE  /api/products/5
```

Ye resource-oriented API design ka common pattern hai.

## 9. REST API Mein JSON Kya Hai?

JSON ka full form **JavaScript Object Notation** hai.

JSON ek lightweight data-interchange format hai.

REST APIs commonly JSON mein data send aur receive karti hain.

Example:

```json
{
  "id": 101,
  "name": "Rahul",
  "email": "rahul@example.com",
  "isActive": true
}
```

JSON data types:

| Type    | Example            |
| ------- | ------------------ |
| String  | `"Rahul"`          |
| Number  | `25`               |
| Boolean | `true`             |
| Array   | `[1, 2, 3]`        |
| Object  | `{"name":"Rahul"}` |
| Null    | `null`             |

Important:
JSON mein property names aur string values double quotes mein hoti hain.

## 10. REST API Endpoint Kya Hota Hai?

Endpoint API ka specific URL/path hota hai jahan client request send karta hai.

Example:

```text
https://api.example.com/api/users
```

Is URL mein:

- `https` = Scheme.
- `api.example.com` = Host.
- `/api/users` = Path.

Different endpoints different resources ya operations represent karte hain.

Examples:

```text
/api/users
/api/products
/api/orders
/api/payments
```

## 11. Collection vs Individual Resource

REST APIs mein collection aur individual resource ka difference samajhna important hai.

### Collection

Multiple resources represent karti hai.

```text
GET /api/users
```

Response:

```json
[
  {
    "id": 1,
    "name": "Rahul"
  },
  {
    "id": 2,
    "name": "Aman"
  }
]
```

### Individual Resource

Ek particular resource represent karta hai.

```text
GET /api/users/1
```

Response:

```json
{
  "id": 1,
  "name": "Rahul"
}
```

## 12. REST API Naming Conventions

API endpoints design karte time consistent naming use karni chahiye.

### Good Examples

```text
GET    /api/users
GET    /api/users/10
POST   /api/users
DELETE /api/users/10
GET    /api/products
GET    /api/orders
```

### Avoid These Examples

```text
/getAllUsers
/createNewUser
/deleteUserById/10
```

Reason:

REST-style resource URLs mein nouns use karna common convention hai. HTTP method operation indicate karta hai.

### Naming Best Practices

1. Resource names ke liye nouns use karo.
2. Consistent plural naming rakho.
3. Resource relationships clearly show karo.
4. URLs mein spaces avoid karo.
5. Consistent lowercase naming use karo.

Example:

```text
/api/users/10/orders
```

Meaning: User 10 ke orders.

## 13. REST API Mein Query Parameters

Query parameters ka use filtering, sorting, searching aur pagination ke liye hota hai.

Example:

```text
GET /api/products?category=mobile
```

Meaning: Mobile category ke products fetch karo.

### Filtering

```text
/api/products?category=mobile
```

### Sorting

```text
/api/products?sort=price
```

### Searching

```text
/api/products?search=iphone
```

### Pagination

```text
/api/products?page=2&limit=10
```

Meaning:

- Page = 2
- Limit = 10

Query parameters generally optional conditions provide karte hain.

## 14. REST API Mein Path Parameters

Path parameters specific resource identify karne ke liye use hote hain.

Example:

```text
/api/users/10
```

Yahan `10` user ID hai.

Express example:

```javascript
app.get("/api/users/:id", (req, res) => {
  const userId = req.params.id;

  res.json({
    userId,
  });
});
```

Agar request ho:

```text
/api/users/10
```

To `req.params.id` ki value `"10"` hogi.

## 15. REST API Mein Request Body

Request body mein client server ko data send kar sakta hai.

Example:

```http
POST /api/users
Content-Type: application/json

{
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

Express mein:

```javascript
app.use(express.json());

app.post("/api/users", (req, res) => {
  const userData = req.body;

  res.status(201).json({
    message: "User received",
    user: userData,
  });
});
```

`express.json()` JSON request body ko parse karne ke liye middleware provide karta hai.

## 16. REST API Mein Response

Server client ko response return karta hai.

Response mein ho sakta hai:

- Status code.
- Headers.
- Response body.

Example:

```javascript
app.get("/api/users", (req, res) => {
  res.status(200).json({
    success: true,
    data: [
      {
        id: 1,
        name: "Rahul",
      },
    ],
  });
});
```

Possible response:

```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "Rahul"
    }
  ]
}
```

Response structure consistent rakhna good practice hai.

## 17. REST API Versioning

API versioning ka use API ke different versions maintain karne ke liye hota hai.

Example:

```text
/api/v1/users
/api/v2/users
```

Suppose old API response:

```json
{
  "name": "Rahul"
}
```

New API response:

```json
{
  "firstName": "Rahul",
  "lastName": "Sharma"
}
```

Agar existing clients old structure use kar rahe hain, to new version introduce karna useful ho sakta hai.

Detailed API versioning Topic 12 mein cover karenge.

## 18. REST API vs RESTful API

In terms ka use often interchangeably hota hai.

- REST API: REST architectural style se related API.
- RESTful API: Aisi API jo REST constraints follow karti ho.

Important: Sirf HTTP aur JSON use karne se API automatically fully RESTful nahi ban jaati.

## 19. REST API vs SOAP

SOAP ka full form **Simple Object Access Protocol** hai.

SOAP ek messaging protocol hai, jabki REST ek architectural style hai.

| REST                              | SOAP                                |
| --------------------------------- | ----------------------------------- |
| Architectural style               | Messaging protocol                  |
| Lightweight design commonly       | More structured protocol            |
| JSON commonly used                | XML-based messages                  |
| HTTP commonly used                | Multiple transport options          |
| Flexible resource-oriented design | Operation/message-oriented approach |

REST web APIs mein widely used hai.

SOAP bhi kuch enterprise aur legacy systems mein use hota hai.

## 20. REST API vs GraphQL

GraphQL ek query language aur runtime hai APIs ke liye.

| REST                               | GraphQL                                       |
| ---------------------------------- | --------------------------------------------- |
| Multiple resource endpoints common | Commonly single endpoint                      |
| Server-defined response structure  | Client requested fields specify karta hai     |
| Over-fetching possible             | Required fields request kiye ja sakte hain    |
| Under-fetching possible            | Related data ek query mein fetch ho sakta hai |
| HTTP methods commonly used         | Commonly POST requests                        |

Example:

REST:

```text
GET /api/users/10
GET /api/users/10/orders
```

GraphQL:

```graphql
query {
  user(id: 10) {
    name
    orders {
      id
      total
    }
  }
}
```

Dono ke apne use cases hain.

## 21. REST API Security Basics

REST APIs design karte waqt security important hai.

Important practices:

1. HTTPS use karo.
2. Authentication implement karo.
3. Authorization check karo.
4. Input validation karo.
5. Rate limiting use karo.
6. Sensitive data response mein expose mat karo.
7. Proper error handling karo.
8. CORS ko correctly configure karo.
9. Secrets environment variables mein rakho.
10. Dependencies updated rakho.

Important:

CORS authentication ya authorization ka replacement nahi hai.

## 22. MERN Stack Mein REST API

MERN ka full form:

- MongoDB
- Express.js
- React.js
- Node.js

MERN applications mein REST APIs commonly use hoti hain.

```text
       USER
         |
         v
       REACT
         |
         | HTTP Request
         v
      REST API
         |
         v
      EXPRESS
         |
         v
       NODE
         |
         v
      MONGODB
         |
         v
      RESPONSE
         |
         v
       REACT
```

### React Frontend

```javascript
async function fetchUsers() {
  const response = await fetch("http://localhost:5000/api/users");

  const data = await response.json();

  console.log(data);
}

fetchUsers();
```

### Express Backend

```javascript
const express = require("express");

const app = express();

app.use(express.json());

const users = [
  { id: 1, name: "Rahul" },
  { id: 2, name: "Aman" },
];

app.get("/api/users", (req, res) => {
  res.status(200).json({
    success: true,
    data: users,
  });
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

## 23. Complete REST API Example

Is example mein basic CRUD operations implement kiye gaye hain.

```javascript
const express = require("express");

const app = express();

app.use(express.json());

let users = [
  { id: 1, name: "Rahul" },
  { id: 2, name: "Aman" },
];

// GET: All users
app.get("/api/users", (req, res) => {
  res.status(200).json(users);
});

// GET: One user
app.get("/api/users/:id", (req, res) => {
  const id = Number(req.params.id);

  const user = users.find((user) => user.id === id);

  if (!user) {
    return res.status(404).json({
      message: "User not found",
    });
  }

  res.status(200).json(user);
});

// POST: Create user
app.post("/api/users", (req, res) => {
  const { name } = req.body;

  if (!name) {
    return res.status(400).json({
      message: "Name is required",
    });
  }

  const newUser = {
    id: Date.now(),
    name,
  };

  users.push(newUser);

  res.status(201).json(newUser);
});

// PUT: Replace user
app.put("/api/users/:id", (req, res) => {
  const id = Number(req.params.id);

  const index = users.findIndex((user) => user.id === id);

  if (index === -1) {
    return res.status(404).json({
      message: "User not found",
    });
  }

  const { name } = req.body;

  if (!name) {
    return res.status(400).json({
      message: "Name is required",
    });
  }

  users[index] = { id, name };

  res.status(200).json(users[index]);
});

// PATCH: Partial update
app.patch("/api/users/:id", (req, res) => {
  const id = Number(req.params.id);

  const user = users.find((user) => user.id === id);

  if (!user) {
    return res.status(404).json({
      message: "User not found",
    });
  }

  if (req.body.name !== undefined) {
    user.name = req.body.name;
  }

  res.status(200).json(user);
});

// DELETE: Remove user
app.delete("/api/users/:id", (req, res) => {
  const id = Number(req.params.id);

  const index = users.findIndex((user) => user.id === id);

  if (index === -1) {
    return res.status(404).json({
      message: "User not found",
    });
  }

  users.splice(index, 1);

  res.status(204).send();
});

app.listen(5000, () => {
  console.log("REST API running on port 5000");
});
```

Note: Ye learning example hai. Isme data memory mein store hota hai, MongoDB mein nahi. Server restart hone par data reset ho jayega.

## 24. Common REST API Mistakes

1. Resource URLs mein unnecessary verbs use karna.
2. GET request se data create/update karna.
3. Har response par 200 status code dena.
4. Inconsistent JSON response structure.
5. Input validation skip karna.
6. Authentication aur authorization ignore karna.
7. Sensitive information return karna.
8. API versioning ka plan na banana.
9. Pagination ke bina bahut bada data return karna.
10. Error responses properly handle na karna.
11. REST aur HTTP ko same cheez samajhna.
12. Sirf JSON use karne ko RESTful hone ka proof samajhna.

## 25. Interview Questions and Answers

**Q1. What is an API?**

Ans: An API is an interface that allows software applications to communicate through defined rules.

**Q2. What is REST?**

Ans: REST is an architectural style for designing network-based applications.

**Q3. What is a REST API?**

Ans: A REST API is an API designed to follow REST architectural constraints.

**Q4. What are the six REST constraints?**

Ans:

1. Client-Server
2. Stateless
3. Cacheable
4. Uniform Interface
5. Layered System
6. Code on Demand (optional)

**Q5. What is a resource in REST?**

Ans: A resource is an identifiable piece of information or entity, such as a user, product or order.

**Q6. Why is REST stateless?**

Ans: Each request contains the information needed to process it without relying on stored application context from previous requests.

**Q7. What is a REST endpoint?**

Ans: An endpoint is a URL/path through which a client accesses an API resource.

**Q8. What is JSON?**

Ans: JSON is a lightweight data-interchange format commonly used by REST APIs.

**Q9. What is the difference between REST and SOAP?**

Ans: REST is an architectural style, whereas SOAP is a messaging protocol.

**Q10. What is the difference between REST and GraphQL?**

Ans: REST commonly uses resource-based endpoints, whereas GraphQL lets clients request specific fields through queries.

**Q11. What is API versioning?**

Ans: API versioning allows different versions of an API to coexist.

**Q12. What is HATEOAS?**

Ans: HATEOAS means Hypermedia as the Engine of Application State. It allows responses to provide links describing possible next actions.

## 26. Practical Tasks

### Task 1: Understand REST Endpoints

Identify the resource and operation:

```text
GET    /api/users
GET    /api/users/10
POST   /api/products
PATCH  /api/products/5
DELETE /api/orders/20
```

### Task 2: Test Public API

Browser ya CMD mein:

```cmd
curl -i https://jsonplaceholder.typicode.com/users
```

Observe:

- Endpoint.
- HTTP method.
- Status code.
- Response headers.
- JSON response.

### Task 3: Test Query Parameters

```cmd
curl "https://jsonplaceholder.typicode.com/posts?userId=1"
```

Observe filtered response.

### Task 4: Build Your Own REST API

Express mein users ke liye ye endpoints banao:

```text
GET    /api/users
GET    /api/users/:id
POST   /api/users
PUT    /api/users/:id
PATCH  /api/users/:id
DELETE /api/users/:id
```

Har endpoint ko Postman ya curl se test karo.

## 27. Quick Revision

- API = Application Programming Interface.
- REST = Representational State Transfer.
- REST = Architectural Style.
- REST API = REST principles follow karne wali API.
- Resource = User, Product, Order etc.
- Endpoint = API resource ka URL/path.
- Stateless = Har request independently process ho sakti hai.
- Cacheable = Responses caching ke liye eligible ho sakti hain.
- Uniform Interface = Consistent communication rules.
- Client-Server = Client aur server responsibilities separate.
- Layered System = Beech mein proxy/gateway jaise layers ho sakti hain.
- Code on Demand = Optional REST constraint.
- JSON = Common data-interchange format.
- GET = Read.
- POST = Create/Submit.
- PUT = Replace.
- PATCH = Partial Update.
- DELETE = Remove.
- Query Parameters = Filtering, sorting, searching, pagination.
- Path Parameters = Particular resource identify karna.
- Versioning = API ke multiple versions maintain karna.

## 28. Topic Completion Checklist

- [ ] API Introduction
- [ ] API Working
- [ ] REST Introduction
- [ ] REST API
- [ ] Resource
- [ ] Six REST Constraints
- [ ] HTTP Methods in REST
- [ ] JSON
- [ ] Endpoint
- [ ] Collection vs Individual Resource
- [ ] Naming Conventions
- [ ] Query Parameters
- [ ] Path Parameters
- [ ] Request Body
- [ ] API Response
- [ ] API Versioning
- [ ] REST vs SOAP
- [ ] REST vs GraphQL
- [ ] API Security
- [ ] MERN Integration
- [ ] CRUD API Practical
- [ ] Interview Questions
