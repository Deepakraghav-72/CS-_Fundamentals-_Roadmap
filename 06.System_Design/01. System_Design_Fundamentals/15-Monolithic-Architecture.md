# Topic 15: Monolithic Architecture

## 1. Architecture kya hoti hai?

Software Architecture ka matlab hai kisi application ke different components ko kaise organize aur connect kiya gaya hai, iska overall structure.

Simple language mein:

**Architecture = Application banane ka overall structure aur design.**

Example:

Maan lo hum ek E-commerce application bana rahe hain.

Ismein multiple features honge:

- User Registration
- User Login
- Product Management
- Cart Management
- Order Management
- Payment Management

Ab question hai ki in sabhi features ko application mein kaise organize karenge?

Isi structure ko Software Architecture kehte hain.

---

## 2. Monolithic Architecture kya hoti hai?

Monolithic Architecture ek software architecture style hai jisme application ke different functional components ko generally ek single application unit ke andar develop aur deploy kiya jata hai.

Simple language mein:

**Monolithic Architecture = Puri application ek single deployable unit ke roop mein hoti hai.**

Example:

Maan lo E-commerce application hai.

Ismein:

- User Module
- Product Module
- Cart Module
- Order Module
- Payment Module

Ye sabhi modules ek hi application ke parts hain.

```text
       E-Commerce Application
                 |
      +----------+----------+
      |          |          |
   User       Product      Cart
   Module     Module      Module
      |          |          |
      +----------+----------+
                 |
          Order Module
                 |
          Payment Module
                 |
             Database
```

Ye sabhi modules ek hi application ke andar kaam karte hain.

**Important:** Monolithic ka matlab ye nahi ki code ek hi file mein likha hota hai. Application ke andar multiple folders, files aur modules ho sakte hain. Main point ye hai ki application generally ek unit ke roop mein deploy hoti hai.

---

## 3. Monolithic Architecture ka Real-Life Example

Maan lo tum ek E-commerce website use kar rahe ho.

Website mein:

1. User login karta hai.
2. Products search karta hai.
3. Product cart mein add karta hai.
4. Order place karta hai.
5. Payment karta hai.

Monolithic application mein ye sabhi features ek hi application ka part ho sakte hain.

```text
              E-Commerce App
                    |
        +-----------+-----------+
        |           |           |
      Users       Products     Cart
        |           |           |
        +-----------+-----------+
                    |
                  Orders
                    |
                  Payment
                    |
                 Database
```

User application access karta hai aur application ke different modules uski request process karte hain.

---

## 4. Monolithic Architecture kaise kaam karti hai?

Iska basic working flow:

```text
        User / Client
              |
              | HTTP Request
              v
       Monolithic Backend
              |
       +------+------+
       |      |      |
     User  Product  Order
    Module  Module  Module
       |      |      |
       +------+------+
              |
           Database
              |
              v
        Backend Response
              |
              v
        User / Client
```

### Step-by-step Working

1. Client request send karta hai.
2. Request application ke backend par aati hai.
3. Backend correct route identify karta hai.
4. Related module request process karta hai.
5. Zarurat ke according database se data fetch ya update hota hai.
6. Backend response return karta hai.

Example:

User products dekhna chahta hai.

```http
GET /api/products
```

Product module request process karega aur database se products fetch karke response dega.

---

## 5. Monolithic Architecture ki Internal Structure

Monolithic application ko bhi properly organize kiya jata hai.

Example MERN backend structure:

```text
backend/
|
|-- src/
|   |
|   |-- config/
|   |    |-- db.js
|   |
|   |-- models/
|   |    |-- User.js
|   |    |-- Product.js
|   |    |-- Order.js
|   |
|   |-- controllers/
|   |    |-- userController.js
|   |    |-- productController.js
|   |    |-- orderController.js
|   |
|   |-- routes/
|   |    |-- userRoutes.js
|   |    |-- productRoutes.js
|   |    |-- orderRoutes.js
|   |
|   |-- middleware/
|   |    |-- authMiddleware.js
|   |
|   |-- app.js
|
|-- server.js
|-- package.json
```

Is structure mein:

- Models database ke data structures define karte hain.
- Controllers business logic handle karte hain.
- Routes API endpoints define karte hain.
- Middleware authentication aur validation jaise tasks handle karte hain.
- Config database connection manage karta hai.

Ye sabhi parts ek hi backend application ka hissa hain.

---

## 6. Monolithic Architecture ke Main Characteristics

### 1. Single Deployable Unit

Application ko generally ek unit ke roop mein deploy kiya jata hai.

### 2. Shared Codebase

Different modules same application codebase ka part hote hain.

### 3. Module Communication

Modules ek doosre ko direct function calls ya shared application components ke through access kar sakte hain.

### 4. Common Runtime

Application ke modules generally ek hi application process ya deployment environment ka hissa hote hain.

### 5. Centralized Management

Application ka deployment aur monitoring comparatively centralized ho sakta hai.

---

## 7. Monolithic Architecture ke Advantages

### 1. Easy to Develop

Starting mein application develop karna comparatively simple hota hai.

Kyunki sabhi modules ek hi codebase mein hote hain.

### 2. Easy Testing

Modules ko ek integrated application ke roop mein test kar sakte hain.

### 3. Simple Deployment

Generally ek application unit deploy karni hoti hai.

### 4. Easy Debugging

Ek hi application codebase mein request ka flow trace karna comparatively easy ho sakta hai.

### 5. Less Infrastructure Complexity

Starting mein multiple services, service discovery aur inter-service communication manage nahi karna padta.

### 6. Direct Module Communication

Same application ke modules function calls ke through communicate kar sakte hain.

Network communication ki zarurat har module interaction ke liye nahi hoti.

---

## 8. Monolithic Architecture ke Disadvantages

### 1. Scaling Problem

Maan lo application mein product search par bahut zyada traffic aa raha hai.

Lekin login aur cart modules par comparatively kam traffic hai.

Monolithic application ko scale karne par generally poori application ki additional instances chalani pad sakti hain.

Sirf product module ko independently deploy aur scale karna difficult hota hai.

### 2. Large Codebase

Application badi hone par codebase complex ho sakta hai.

### 3. Deployment Risk

Ek module mein change karne ke baad poori application ko rebuild aur redeploy karna pad sakta hai.

### 4. Technology Dependency

Application ke modules same overall technology stack aur runtime constraints share kar sakte hain.

Different modules ke liye independently technology choose karna comparatively difficult ho sakta hai.

### 5. Single Application Failure

Agar critical unhandled error ya resource exhaustion poori application process ko crash kar de, toh multiple modules unavailable ho sakte hain.

### 6. Team Coordination

Large teams ke liye same codebase mein changes manage karna difficult ho sakta hai.

---

## 9. Monolithic Architecture mein Scaling

Scaling ka matlab application ki capacity increase karna hai taaki woh more users aur requests handle kar sake.

Monolithic application ko bhi scale kar sakte hain.

### A. Vertical Scaling

Vertical Scaling ka matlab existing server ki capacity increase karna.

Example:

```text
Before:
4 CPU + 8 GB RAM

After:
8 CPU + 16 GB RAM
```

Isse same application ko more computing resources milte hain.

### B. Horizontal Scaling

Horizontal Scaling ka matlab same application ki multiple instances run karna.

Example:

```text
             Load Balancer
                   |
          +--------+--------+
          |        |        |
        App 1    App 2    App 3
          |        |        |
          +--------+--------+
                   |
                Database
```

Ismein same monolithic application ki multiple copies run ho sakti hain.

**Important:** Horizontal scaling ke liye session management, shared storage aur database connections ko properly handle karna padta hai. Har instance par local session store rakhna problems create kar sakta hai.

---

## 10. Monolithic Architecture mein Database

Monolithic application mein commonly ek shared database use kiya ja sakta hai.

Example:

```text
        Monolithic Backend
                |
      +---------+---------+
      |         |         |
    User     Product    Order
    Module   Module     Module
      |         |         |
      +---------+---------+
                |
             MongoDB
```

User, Product aur Order modules same database ko access kar sakte hain.

Lekin iska matlab ye nahi ki Monolithic Architecture mein sirf ek database hi use ho sakta hai. Architecture ke according multiple databases bhi possible hain.

### MERN Example

- User Model
- Product Model
- Order Model

Ye Mongoose models ek hi MongoDB database mein collections represent kar sakte hain.

---

## 11. Monolithic Architecture vs Modular Monolith

Dono terms ko samajhna important hai.

### Monolith

Application ek deployable unit hoti hai. Lekin internal code organization weak ho sakta hai.

Example:

```text
src/
  app.js
  allLogic.js
  database.js
```

### Modular Monolith

Application ab bhi ek deployable unit hoti hai, lekin code ko clearly separated modules mein organize kiya jata hai.

Example:

```text
src/
  modules/
    users/
    products/
    orders/
    payments/
```

Har module ki apni responsibilities aur boundaries hoti hain.

### Difference

| Monolith                                     | Modular Monolith                    |
| -------------------------------------------- | ----------------------------------- |
| Single deployable application                | Single deployable application       |
| Code organization weak bhi ho sakta hai      | Clear module boundaries             |
| Modules ke beech tight coupling ho sakti hai | Coupling control karne ki koshish   |
| Maintainability difficult ho sakti hai       | Maintainability better ho sakti hai |

**Important:** Modular Monolith bhi Monolithic Architecture hi hai. Modules ko separately deploy karna zaroori nahi hota.

---

## 12. Monolithic vs Microservices Architecture

Ye System Design ka important comparison hai.

### Monolithic Architecture

Application ke modules ek single deployable application ka part hote hain.

### Microservices Architecture

Application ko multiple small, independently deployable services mein divide kiya jata hai.

Example:

```text
             Monolithic
                 |
       +---------+---------+
       |         |         |
     Users    Products   Orders
       |         |         |
       +---------+---------+
                 |
             Database
```

Microservices example:

```text
             API Gateway
                  |
        +---------+---------+
        |         |         |
     User      Product    Order
    Service    Service   Service
        |         |         |
      DB-1      DB-2      DB-3
```

### Comparison Table

| Monolithic                              | Microservices                                    |
| --------------------------------------- | ------------------------------------------------ |
| Single deployable application           | Multiple independently deployable services       |
| Simple initial setup                    | More infrastructure complexity                   |
| Direct internal function calls possible | Services communicate over network or messaging   |
| Whole application scaling common        | Services independently scale ho sakti hain       |
| Shared codebase common                  | Services ke separate codebases ho sakte hain     |
| Deployment generally centralized        | Independent deployment possible                  |
| Smaller projects ke liye useful         | Large, complex systems mein useful ho sakte hain |

**Important:** Microservices automatically better nahi hoti. Architecture project ki requirements, team size aur operational capacity ke according choose karni chahiye.

---

## 13. Real-World Example: E-commerce Application

Maan lo hum ek E-commerce platform build kar rahe hain.

Features:

1. User Registration
2. Login
3. Product Search
4. Cart
5. Orders
6. Payments

### Monolithic Design

```text
          E-Commerce Application
                    |
        +-----------+-----------+
        |           |           |
      User        Product      Cart
      Module      Module      Module
        |           |           |
        +-----------+-----------+
                    |
                 Order
                    |
                 Payment
                    |
                 Database
```

Is architecture mein:

- User module login handle karta hai.
- Product module product information handle karta hai.
- Cart module cart operations handle karta hai.
- Order module orders create karta hai.
- Payment module payment integration handle karta hai.

Sabhi modules ek backend application mein hain.

---

## 14. MERN Stack Monolithic Application Example

MERN stack mein React frontend aur Express/Node backend ka example:

```text
           React Frontend
                  |
                  | HTTP API Requests
                  v
           Express Backend
                  |
       +----------+----------+
       |          |          |
    User       Product     Order
   Routes      Routes      Routes
       |          |          |
   Controllers Controllers Controllers
       |          |          |
       +----------+----------+
                  |
               Mongoose
                  |
               MongoDB
```

### Example Express Routes

```javascript
const express = require("express");

const app = express();

app.use(express.json());

// User Module
app.get("/api/users", (req, res) => {
  res.json({
    message: "Users fetched",
  });
});

// Product Module
app.get("/api/products", (req, res) => {
  res.json({
    message: "Products fetched",
  });
});

// Order Module
app.get("/api/orders", (req, res) => {
  res.json({
    message: "Orders fetched",
  });
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

Ye simple example ek hi Express application mein multiple modules ke routes show karta hai.

Production project mein routes, controllers, services aur models ko separate files mein organize karna chahiye.

---

## 15. Monolithic Architecture Kab Use Karni Chahiye?

Monolithic Architecture useful ho sakti hai jab:

1. Project small ya medium size ka ho.
2. Initial development fast rakhna ho.
3. Team small ho.
4. Application ki complexity manageable ho.
5. Independent service deployment ki requirement na ho.
6. Infrastructure simple rakhna ho.

### Example Projects

- Portfolio Website Backend
- Small E-commerce Application
- College Management System
- Blog Application
- Basic Social Media Application

Ye examples hain; actual architecture requirements par depend karti hai.

---

## 16. Monolithic Architecture se Microservices ki taraf Migration

Maan lo tumhari application initially Monolithic thi.

Time ke saath:

- Users badh gaye.
- Product search par heavy traffic aane laga.
- Development teams badi ho gayi.
- Independent deployments ki requirement aane lagi.

Ab organization kuch modules ko independently deployable services mein convert karne ka decision le sakti hai.

Example:

```text
       Initially Monolithic
                |
       +--------+--------+
       |        |        |
     Users   Products  Orders
                |
                v
        Gradual Extraction
                |
       +--------+--------+
       |        |        |
     Users   Product   Orders
    Service  Service  Service
```

Is process ko Microservices Migration ya Service Extraction kaha ja sakta hai.

### Migration ke Important Steps

1. Existing application ko understand karo.
2. Modules aur dependencies identify karo.
3. Clear module boundaries establish karo.
4. Ek suitable module select karo.
5. Us module ko independent service banao.
6. API ya messaging ke through communication establish karo.
7. Testing aur monitoring karo.
8. Gradually migration continue karo.

**Important:** Migration ek step mein karna compulsory nahi hai. Gradual migration risk ko control karne mein help kar sakti hai.

---

## 17. Common Mistakes

1. Monolithic ka matlab ek hi code file samajhna.
2. Monolithic application ko non-scalable samajhna.
3. Ye samajhna ki Monolithic mein multiple modules nahi ho sakte.
4. Modular Monolith aur Microservices ko same samajhna.
5. Har project mein Microservices use karna.
6. Modules ke beech unnecessary tight coupling create karna.
7. Horizontal scaling mein session management ignore karna.
8. Ek module ka change poori application ko affect kar sakta hai, is risk ko ignore karna.

---

## 18. Interview Questions and Answers

### Q1. Monolithic Architecture kya hai?

Aisi architecture jisme application ke multiple functional modules generally ek single deployable unit ka part hote hain.

### Q2. Kya Monolithic application mein multiple modules ho sakte hain?

Haan. User, Product, Cart aur Order jaise multiple modules ek Monolithic application mein ho sakte hain.

### Q3. Monolithic Architecture ka biggest advantage kya hai?

Initial development, testing aur deployment comparatively simple ho sakte hain.

### Q4. Monolithic Architecture ka disadvantage kya hai?

Application grow hone par codebase complex ho sakta hai aur independent module deployment/scaling difficult ho sakti hai.

### Q5. Kya Monolithic application scale ho sakti hai?

Haan. Vertical aur Horizontal dono tarah se scale kar sakte hain.

### Q6. Modular Monolith kya hai?

Aisi Monolithic application jisme code ko clearly separated modules aur responsibilities mein organize kiya jata hai.

### Q7. Monolithic aur Microservices mein main difference kya hai?

Monolith generally ek deployable application hoti hai, jabki Microservices mein multiple independently deployable services hoti hain.

### Q8. Kya Monolithic Architecture small projects ke liye suitable hai?

Haan, small aur medium projects mein ye practical choice ho sakti hai.

### Q9. Kya Monolithic application mein ek hi database hona compulsory hai?

Nahi. Ek ya multiple databases use kiye ja sakte hain.

### Q10. Microservices mein migration kab consider karni chahiye?

Jab independent scaling, deployment, team ownership ya technology requirements ka real need ho.

---

## 19. Practical Tasks

### Task 1: Architecture Diagram

Ek E-commerce Monolithic Architecture ka diagram banao jisme:

- User Module
- Product Module
- Cart Module
- Order Module
- Payment Module
- Database

Include hon.

### Task 2: Express Application

Ek Express backend banao jisme:

- `/api/users`
- `/api/products`
- `/api/orders`

Teen alag routes hon.

### Task 3: Modular Structure

Apne Express project mein folders create karo:

```text
modules/
  users/
  products/
  orders/
```

Har module ke routes aur controllers separate rakho.

### Task 4: Comparison

Monolithic aur Microservices ke 5 advantages/disadvantages likho.

---

## 20. Quick Revision

- Software Architecture = Application ka overall structure.
- Monolithic Architecture = Single deployable application unit.
- Modules = Application ke different functional parts.
- Single Deployable Unit = Application generally ek unit mein deploy hoti hai.
- Advantages = Simple development, testing aur deployment.
- Disadvantages = Large codebase, tight coupling aur independent deployment ki difficulty.
- Vertical Scaling = Server resources increase karna.
- Horizontal Scaling = Multiple application instances run karna.
- Modular Monolith = Clear boundaries wali Monolithic application.
- Microservices = Multiple independently deployable services.
- MERN Monolith = React frontend + single Express/Node backend application + database.
- Migration = Monolith ke modules ko gradually independent services mein extract karna.

---

## 21. Topic Completion Checklist

- [ ] Software Architecture samajh li.
- [ ] Monolithic Architecture samajh li.
- [ ] Monolithic working flow samajh liya.
- [ ] Internal folder structure samajh li.
- [ ] Main characteristics samajh li.
- [ ] Advantages samajh liye.
- [ ] Disadvantages samajh liye.
- [ ] Vertical aur Horizontal Scaling samajh li.
- [ ] Database structure samajh li.
- [ ] Modular Monolith samajh liya.
- [ ] Monolithic vs Microservices samajh liya.
- [ ] MERN practical example samajh liya.
- [ ] Migration ka basic process samajh liya.

**Topic 15 Complete – Monolithic Architecture.**
