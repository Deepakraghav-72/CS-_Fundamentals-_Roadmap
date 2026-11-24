# Web Development Fundamentals – Complete Notes

## 1. What is Web Development?

**Definition:** Web Development is the process of creating, building and maintaining websites and web applications.

Web Development ke through websites, web applications, e-commerce platforms aur online services banayi jaati hain.

### Types of Web Development

**1. Frontend Development**

- Website ka visible part.
- User interface (UI) create karta hai.
- HTML, CSS, JavaScript, React.

**2. Backend Development**

- Server-side logic handle karta hai.
- Database operations aur authentication.
- Node.js, Express.js, Python, Java.

**3. Full Stack Development**

- Frontend + Backend + Database.
- Complete web application develop karna.

### Web Development Technologies

| Frontend   | Backend    | Database   |
| ---------- | ---------- | ---------- |
| HTML       | Node.js    | MongoDB    |
| CSS        | Express.js | MySQL      |
| JavaScript | Python     | PostgreSQL |
| React      | Java       | Redis      |

---

## 2. How Does the Web Work?

Jab hum browser mein website ka URL enter karte hain, browser server se request karta hai aur server response return karta hai.

### Working Process

1. User browser mein URL enter karta hai.
2. Browser DNS se domain ka IP address find karta hai.
3. Browser server ke saath connection establish karta hai.
4. HTTP/HTTPS request send hoti hai.
5. Server request process karta hai.
6. Server response return karta hai.
7. Browser HTML, CSS aur JavaScript process karke webpage display karta hai.

### Important Terms

**Client:** Device ya application jo request send karta hai.

**Server:** System jo client ki request process karke response deta hai.

**Browser:** Software used to access websites.

Examples:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Safari

**Website:** Related web pages ka collection.

**Web Application:** Interactive software accessed through a web browser.

Examples: Gmail, Google Docs, Trello.

---

## 3. Internet vs World Wide Web (WWW)

**Internet:** A global network of interconnected computer networks.

**WWW:** A system of interconnected web pages and resources accessed through the Internet.

| Internet                       | WWW                       |
| ------------------------------ | ------------------------- |
| Global network infrastructure  | Information system        |
| Supports multiple services     | Uses web technologies     |
| Includes email, FTP, web, etc. | Accessed through browsers |

Important: Internet aur WWW same nahi hain.

---

## 4. URL (Uniform Resource Locator)

URL is the address used to locate a resource on the Internet.

Example:

https://www.example.com:443/products?id=10#details

### URL Components

1. Protocol: `https`
2. Subdomain: `www`
3. Domain: `example.com`
4. Port: `443`
5. Path: `/products`
6. Query Parameter: `?id=10`
7. Fragment: `#details`

### Domain Name

A human-readable address used to access a website.

Example: google.com

### IP Address

An IP address identifies a device or network interface on an IP network.

Types:

- IPv4 – 32-bit address.
- IPv6 – 128-bit address.

### DNS (Domain Name System)

DNS translates domain names into IP addresses.

Example:

google.com → IP Address

DNS is often called the phonebook of the Internet.

---

## 5. HTTP and HTTPS

### HTTP

HTTP stands for HyperText Transfer Protocol.

It is an application-layer protocol used for communication between clients and web servers.

### HTTPS

HTTPS is HTTP secured using TLS encryption.

It provides:

- Data encryption.
- Server authentication.
- Data integrity.

### HTTP vs HTTPS

| HTTP                       | HTTPS                     |
| -------------------------- | ------------------------- |
| No TLS protection          | Uses TLS                  |
| Data not encrypted by HTTP | Data encrypted in transit |
| Less secure                | More secure               |
| Default port 80            | Default port 443          |

---

## 6. HTTP Methods

HTTP methods define the type of operation a client wants to perform.

| Method  | Purpose                               |
| ------- | ------------------------------------- |
| GET     | Retrieve data                         |
| POST    | Submit or create data                 |
| PUT     | Replace a resource                    |
| PATCH   | Partially update a resource           |
| DELETE  | Delete a resource                     |
| HEAD    | Retrieve headers only                 |
| OPTIONS | Check supported communication options |

Example:

```http
GET /api/users
POST /api/users
PUT /api/users/1
PATCH /api/users/1
DELETE /api/users/1
```

Important:

- GET is generally safe and idempotent.
- PUT is idempotent.
- DELETE is idempotent in its intended effect.
- POST is generally not idempotent.
- PATCH is not necessarily idempotent.

---

## 7. HTTP Status Codes

HTTP status codes indicate the result of an HTTP request.

### 1xx – Informational

Request processing continues.

### 2xx – Success

| Code | Meaning    |
| ---- | ---------- |
| 200  | OK         |
| 201  | Created    |
| 202  | Accepted   |
| 204  | No Content |

### 3xx – Redirection

| Code | Meaning           |
| ---- | ----------------- |
| 301  | Moved Permanently |
| 302  | Found             |
| 304  | Not Modified      |

### 4xx – Client Errors

| Code | Meaning            |
| ---- | ------------------ |
| 400  | Bad Request        |
| 401  | Unauthorized       |
| 403  | Forbidden          |
| 404  | Not Found          |
| 405  | Method Not Allowed |
| 409  | Conflict           |
| 429  | Too Many Requests  |

### 5xx – Server Errors

| Code | Meaning               |
| ---- | --------------------- |
| 500  | Internal Server Error |
| 501  | Not Implemented       |
| 502  | Bad Gateway           |
| 503  | Service Unavailable   |
| 504  | Gateway Timeout       |

Remember:

- 2xx = Success.
- 3xx = Redirection.
- 4xx = Client-side issue.
- 5xx = Server-side issue.

---

## 8. Frontend Fundamentals

Frontend is the client-side part of a website that users interact with.

### HTML

HTML stands for HyperText Markup Language.

It defines the structure and content of a webpage.

Important elements:

- Heading
- Paragraph
- Image
- Link
- Form
- Table
- Semantic elements

### CSS

CSS stands for Cascading Style Sheets.

It controls the presentation and layout of webpages.

Important concepts:

- Selectors.
- Box Model.
- Flexbox.
- Grid.
- Positioning.
- Media Queries.
- Responsive Design.

### JavaScript

JavaScript is a programming language used to make webpages interactive.

Examples:

- Form validation.
- DOM manipulation.
- Event handling.
- API requests.
- Dynamic content.

### DOM

DOM stands for Document Object Model.

It represents an HTML document as a tree of objects that JavaScript can access and modify.

Example:

```javascript
document.querySelector("h1").textContent = "Hello World";
```

---

## 9. Responsive Web Design

Responsive Web Design means creating websites that adapt to different screen sizes and devices.

### Important Concepts

**1. Media Queries**

Apply CSS based on device or viewport conditions.

```css
@media (max-width: 768px) {
  .container {
    width: 100%;
  }
}
```

**2. Flexible Layouts**

Use Flexbox and CSS Grid.

**3. Flexible Images**

```css
img {
  max-width: 100%;
  height: auto;
}
```

**4. Viewport Meta Tag**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

### Benefits

- Mobile-friendly.
- Better user experience.
- Supports multiple devices.
- Easier maintenance than separate device-specific websites.

---

## 10. Backend Fundamentals

Backend is the server-side part of an application.

It handles:

- Business logic.
- Authentication.
- Database operations.
- API processing.
- Data validation.
- Server communication.

### Important Backend Technologies

**Node.js:** JavaScript runtime used to execute JavaScript outside the browser.

**Express.js:** A web framework for Node.js used to build APIs and web servers.

**API:** Application Programming Interface.

An API allows different software systems to communicate with each other.

### Request-Response Cycle

Client → HTTP Request → Server → Processing → HTTP Response → Client

---

## 11. API Fundamentals

API stands for Application Programming Interface.

An API defines how different software components or applications communicate.

### Types of APIs

1. REST API.
2. SOAP API.
3. GraphQL API.
4. WebSocket API.

### REST API

REST stands for Representational State Transfer.

It is an architectural style for designing network-based APIs.

Important REST principles:

- Client-Server.
- Stateless communication.
- Cacheability.
- Uniform Interface.
- Layered System.
- Code on Demand (optional).

### REST API Example

```http
GET /api/users
GET /api/users/1
POST /api/users
PUT /api/users/1
DELETE /api/users/1
```

### JSON

JSON stands for JavaScript Object Notation.

It is a lightweight data-interchange format.

Example:

```json
{
  "name": "Rahul",
  "age": 22,
  "role": "Developer"
}
```

### JSON vs XML

| JSON                 | XML                          |
| -------------------- | ---------------------------- |
| Lightweight          | More verbose                 |
| Uses key-value pairs | Uses tags                    |
| Easy to read         | Structured markup            |
| Common in REST APIs  | Used in various data systems |

---

## 12. Database Fundamentals

A database is an organized collection of data that can be stored, managed and retrieved.

### Types of Databases

**1. Relational Database (SQL)**

Stores data in tables consisting of rows and columns.

Examples:

- MySQL.
- PostgreSQL.
- SQL Server.

**2. NoSQL Database**

Supports different data models such as documents, key-value pairs and graphs.

Examples:

- MongoDB.
- Redis.
- Cassandra.

### SQL vs NoSQL

| SQL                | NoSQL                           |
| ------------------ | ------------------------------- |
| Relational         | Non-relational models           |
| Tables             | Documents, key-value, etc.      |
| Often fixed schema | Often flexible schema           |
| SQL queries        | Database-specific query methods |

### CRUD Operations

CRUD stands for:

- Create – Insert data.
- Read – Retrieve data.
- Update – Modify data.
- Delete – Remove data.

### MongoDB Example

```javascript
// Create
db.users.insertOne({ name: "Rahul" });

// Read
db.users.find();

// Update
db.users.updateOne({ name: "Rahul" }, { $set: { age: 22 } });

// Delete
db.users.deleteOne({ name: "Rahul" });
```

---

## 13. Cookies, Sessions and Local Storage

These are mechanisms used to store or maintain information related to users.

### Cookies

Small pieces of data stored by the browser and associated with websites.

Uses:

- Session management.
- Preferences.
- Tracking.

Important cookie attributes:

- HttpOnly.
- Secure.
- SameSite.
- Expires / Max-Age.

### Local Storage

Stores key-value data in the browser.

Features:

- Persists after browser restart.
- Stores strings.
- Accessible through JavaScript.
- Not automatically sent with HTTP requests.

Example:

```javascript
localStorage.setItem("username", "Rahul");

const name = localStorage.getItem("username");
```

### Session Storage

Stores data for a particular browser tab's page session.

### Comparison

| Cookies                          | Local Storage          | Session Storage        |
| -------------------------------- | ---------------------- | ---------------------- |
| Can have expiration              | Persistent             | Tab session            |
| Sent with matching HTTP requests | Not automatically sent | Not automatically sent |
| Small storage capacity           | Larger capacity        | Larger capacity        |
| Server-readable                  | JavaScript-accessible  | JavaScript-accessible  |

Important: Sensitive authentication tokens should not be casually stored in JavaScript-accessible storage.

---

## 14. Web Security Fundamentals

Web Security protects websites, users and data from attacks.

### 1. Authentication

Verifies WHO the user is.

Example: Login using email and password.

### 2. Authorization

Determines WHAT an authenticated user is allowed to access.

Example: Admin can manage users, normal users cannot.

### 3. Encryption

Converts readable data into an encoded form using cryptographic techniques.

### 4. Hashing

Converts input into a fixed-length digest using a hash function.

Passwords should be stored using secure password-hashing algorithms such as:

- bcrypt.
- Argon2.

### 5. Common Web Attacks

**XSS (Cross-Site Scripting)**

Attacker injects malicious scripts into a webpage viewed by other users.

Prevention:

- Output encoding.
- Safe rendering.
- Content Security Policy.
- Input sanitization where appropriate.

**CSRF (Cross-Site Request Forgery)**

Tricks an authenticated user's browser into sending an unwanted request.

Prevention:

- CSRF tokens.
- SameSite cookies.
- Origin checks.

**SQL Injection**

Attacker manipulates database queries through untrusted input.

Prevention:

- Parameterized queries.
- Input validation.
- Least-privilege database access.

**DDoS Attack**

A large volume of malicious traffic makes a service unavailable.

Prevention:

- Rate limiting.
- Traffic filtering.
- DDoS protection services.

### 6. CORS

CORS stands for Cross-Origin Resource Sharing.

It is a browser security mechanism that allows servers to specify which origins can access their resources through cross-origin requests.

### 7. JWT

JWT stands for JSON Web Token.

It is a compact token format used to transmit claims between parties.

Common uses:

- Authentication.
- Authorization information.

---

## 15. Browser Fundamentals

A browser is software used to access and display web content.

### Browser Components

1. User Interface – Address bar, tabs, buttons.
2. Browser Engine – Coordinates browser operations.
3. Rendering Engine – Displays HTML and CSS.
4. JavaScript Engine – Executes JavaScript.
5. Networking – Handles network requests.
6. Storage – Manages browser storage.

### Browser Rendering Process

1. Browser receives HTML.
2. HTML is parsed into DOM.
3. CSS is parsed into CSSOM.
4. DOM and CSSOM are combined into Render Tree.
5. Layout calculates element positions.
6. Painting draws visual elements.
7. Compositing combines layers for display.

### Important Concepts

**Reflow (Layout):** Recalculating the size or position of elements.

**Repaint:** Redrawing visual changes that do not require layout recalculation.

**Caching:** Storing resources to reduce repeated network requests and improve performance.

---

## 16. Web Hosting and Deployment

Web Hosting is a service that makes websites accessible over the Internet.

### Types of Hosting

1. Shared Hosting.
2. VPS Hosting.
3. Dedicated Hosting.
4. Cloud Hosting.
5. Static Hosting.

### Domain vs Hosting

| Domain                     | Hosting                            |
| -------------------------- | ---------------------------------- |
| Website address            | Stores website files and resources |
| Example: example.com       | Server or hosting platform         |
| Helps users locate website | Makes website available            |

### Popular Platforms

- Vercel.
- Netlify.
- Render.
- AWS.
- DigitalOcean.

### Deployment

Deployment means releasing an application into an environment where users can access it.

---

## 17. Web Performance Optimization

Web performance optimization improves loading speed, responsiveness and user experience.

### Important Techniques

1. Image Compression.
2. Lazy Loading.
3. Minification of CSS and JavaScript.
4. Browser Caching.
5. CDN Usage.
6. Code Splitting.
7. Gzip/Brotli Compression.
8. Database Query Optimization.
9. Reduce Unnecessary API Requests.

### CDN

CDN stands for Content Delivery Network.

It distributes cached content through geographically distributed servers to deliver content efficiently.

### Core Web Vitals

Google's important user-experience metrics:

1. LCP – Largest Contentful Paint: Loading performance.
2. INP – Interaction to Next Paint: Responsiveness.
3. CLS – Cumulative Layout Shift: Visual stability.

---

## 18. MERN Stack Fundamentals

MERN is a JavaScript-based technology stack used to build full-stack web applications.

### MERN Stands For

- M – MongoDB.
- E – Express.js.
- R – React.js.
- N – Node.js.

### Role of Each Technology

**MongoDB:** Stores application data.

**Express.js:** Handles backend routes and APIs.

**React.js:** Builds interactive frontend interfaces.

**Node.js:** Runs JavaScript on the server.

### MERN Architecture

React Frontend → HTTP Request → Express/Node Backend → MongoDB Database → Response → React Frontend

### Example

For a login system:

1. User enters email and password.
2. React sends request to backend.
3. Express handles the API route.
4. Backend validates credentials.
5. MongoDB provides user information.
6. Backend returns an appropriate response.
7. React displays the result.

---

## 19. Important Web Development Concepts

### 1. Authentication vs Authorization

Authentication = Who are you?

Authorization = What can you access?

### 2. Synchronous vs Asynchronous

Synchronous operations execute in sequence and can block further execution.

Asynchronous operations allow other work to continue while waiting for an operation to complete.

### 3. Client-Side Rendering (CSR)

The browser uses JavaScript to render application content on the client.

### 4. Server-Side Rendering (SSR)

HTML is generated on the server and sent to the browser.

### 5. Static Site Generation (SSG)

HTML pages are generated ahead of time, generally during the build process.

### 6. SPA (Single Page Application)

A web application that updates content dynamically without requiring a full page reload for every navigation.

### 7. MPA (Multi Page Application)

A website architecture where navigation typically loads separate HTML pages.

### 8. WebSocket

A communication protocol that enables persistent, two-way communication between client and server.

Example: Real-time chat applications.

### 9. Webhook

A mechanism through which one system sends an HTTP notification to another system when an event occurs.

### 10. Rate Limiting

Controls how many requests a client can make within a specified time period.

---

## 20. Important Interview Questions

**Q1. What is Web Development?**

Web Development is the process of building and maintaining websites and web applications.

**Q2. What is the difference between Frontend and Backend?**

Frontend handles the user interface, whereas Backend handles server-side logic, APIs and database operations.

**Q3. What is the difference between Internet and WWW?**

Internet is the global network infrastructure, while WWW is a collection of interconnected web resources accessed through the Internet.

**Q4. What is DNS?**

DNS translates domain names into IP addresses.

**Q5. What is HTTP?**

HTTP is an application-layer protocol used for communication between web clients and servers.

**Q6. What is HTTPS?**

HTTPS is HTTP secured using TLS encryption.

**Q7. What is an API?**

An API allows different software applications or components to communicate.

**Q8. What is REST API?**

REST API is an API designed using REST architectural principles.

**Q9. What is JSON?**

JSON is a lightweight data-interchange format.

**Q10. What are HTTP methods?**

GET, POST, PUT, PATCH, DELETE, HEAD and OPTIONS.

**Q11. What is the difference between GET and POST?**

GET is generally used to retrieve data, whereas POST is generally used to submit data or create resources.

**Q12. What is the difference between PUT and PATCH?**

PUT generally replaces a resource, whereas PATCH partially updates it.

**Q13. What is CORS?**

CORS is a browser security mechanism that controls cross-origin resource sharing.

**Q14. What is CRUD?**

CRUD stands for Create, Read, Update and Delete.

**Q15. What is the difference between SQL and NoSQL?**

SQL databases use relational tables, while NoSQL databases support different non-relational data models.

**Q16. What is the DOM?**

DOM is an object-based representation of an HTML document.

**Q17. What is Responsive Web Design?**

It is an approach to designing websites that adapt to different screen sizes.

**Q18. What is Local Storage?**

Local Storage stores key-value data in the browser that persists across browser sessions.

**Q19. What is a Cookie?**

A cookie is a small piece of data stored by a browser and associated with a website.

**Q20. What is JWT?**

JWT is a compact token format used to securely transmit claims between parties when properly implemented.

**Q21. What is Authentication?**

Authentication verifies the identity of a user.

**Q22. What is Authorization?**

Authorization determines the resources and actions a user is permitted to access.

**Q23. What is XSS?**

XSS is an attack in which malicious scripts are injected into web content viewed by users.

**Q24. What is CSRF?**

CSRF tricks an authenticated browser into making an unwanted request.

**Q25. What is CDN?**

CDN is a geographically distributed network that delivers content efficiently.

**Q26. What is WebSocket?**

WebSocket enables persistent two-way communication between client and server.

**Q27. What is the MERN Stack?**

MERN consists of MongoDB, Express.js, React.js and Node.js.

**Q28. What is the difference between CSR and SSR?**

CSR renders content mainly in the browser, whereas SSR generates HTML on the server.

**Q29. What is a Webhook?**

A webhook sends an HTTP notification when a specific event occurs in another system.

**Q30. What is Caching?**

Caching stores frequently used data or resources to improve performance and reduce repeated requests.

---

## 21. Quick Revision

- Web Development = Building websites and web applications.
- Frontend = User interface.
- Backend = Server-side logic.
- Full Stack = Frontend + Backend + Database.
- HTML = Structure.
- CSS = Styling.
- JavaScript = Interactivity.
- DOM = Document Object Model.
- Internet = Global network.
- WWW = Interconnected web resources.
- URL = Resource address.
- DNS = Domain to IP translation.
- HTTP = Web communication protocol.
- HTTPS = HTTP secured with TLS.
- GET = Retrieve.
- POST = Submit/Create.
- PUT = Replace.
- PATCH = Partial update.
- DELETE = Delete.
- 2xx = Success.
- 3xx = Redirection.
- 4xx = Client error.
- 5xx = Server error.
- API = Application Programming Interface.
- REST = Architectural style.
- JSON = Data-interchange format.
- CRUD = Create, Read, Update, Delete.
- SQL = Relational database.
- NoSQL = Non-relational data models.
- Authentication = Identity verification.
- Authorization = Access permission.
- JWT = Token format.
- CORS = Cross-origin resource sharing.
- CDN = Content Delivery Network.
- CSR = Client-Side Rendering.
- SSR = Server-Side Rendering.
- SPA = Single Page Application.
- MERN = MongoDB + Express + React + Node.

---

## 22. Self-Assessment Practice

1. Explain how a website works from entering a URL to displaying a page.
2. Explain DNS and IP addresses.
3. Differentiate between HTTP and HTTPS.
4. Explain HTTP methods with examples.
5. Explain all five HTTP status code categories.
6. Explain REST API and its principles.
7. Differentiate between SQL and NoSQL.
8. Explain Cookies, Local Storage and Session Storage.
9. Differentiate between Authentication and Authorization.
10. Explain XSS, CSRF and SQL Injection.
11. Explain how browsers render webpages.
12. Differentiate between CSR, SSR and SSG.
13. Explain CDN and caching.
14. Explain MERN architecture with a login example.
15. Explain WebSockets and Webhooks.

**End of Web Development Fundamentals Notes.**
