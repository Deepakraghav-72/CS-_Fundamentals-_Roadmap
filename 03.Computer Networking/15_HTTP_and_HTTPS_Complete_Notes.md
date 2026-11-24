# 15. HTTP and HTTPS – Complete Notes

## 1. What is HTTP?

HTTP ka full form **Hypertext Transfer Protocol** hai.

HTTP ek application-layer protocol hai jiska use client aur server ke beech data communicate karne ke liye hota hai.

Simple language mein:

Jab tum browser mein kisi website ko open karte ho, to browser server ko request bhejta hai aur server response return karta hai.

Example:

```text
User
  |
  v
Browser (Client)
  |
  | HTTP Request
  v
Web Server
  |
  | HTTP Response
  v
Browser
  |
  v
Website Display
```

HTTP ka use hota hai:

- Web pages access karne mein.
- Images aur videos receive karne mein.
- APIs ke through data exchange karne mein.
- Frontend aur backend communication mein.
- Forms submit karne mein.

## 2. Why Do We Need HTTP?

Internet par client aur server ko communicate karne ke liye common rules chahiye.

HTTP define karta hai:

1. Client request kaise bhejega.
2. Server response kaise dega.
3. Request mein kaunsa data hoga.
4. Response ka status kya hoga.
5. Headers aur body ka format kya hoga.

Example:

Maan lo tum browser mein open karte ho:

```text
https://example.com
```

Browser server ko request bhejta hai aur server website ka response return karta hai.

## 3. What is HTTPS?

HTTPS ka full form **Hypertext Transfer Protocol Secure** hai.

HTTPS, HTTP communication ko TLS (Transport Layer Security) ke through secure karta hai.

Iska main purpose client aur server ke beech data ko protect karna hai.

### HTTPS Provides

1. **Encryption:** Data ko transit ke dauran unauthorized reading se protect karta hai.
2. **Integrity:** Data transit mein modify hua hai ya nahi, detect karne mein help karta hai.
3. **Authentication:** Digital certificates ke through server identity verify karne mein help karta hai.

### Example

```text
HTTP:
http://example.com

HTTPS:
https://example.com
```

HTTPS websites mein commonly port `443` use hota hai.

HTTP mein commonly port `80` use hota hai.

## 4. Difference Between HTTP and HTTPS

| HTTP                              | HTTPS                                  |
| --------------------------------- | -------------------------------------- |
| Hypertext Transfer Protocol       | Hypertext Transfer Protocol Secure     |
| TLS security layer nahi hoti      | TLS security use hoti hai              |
| Data encrypted nahi hota by HTTP  | Data TLS ke through encrypted hota hai |
| Default port 80                   | Default port 443                       |
| Security comparatively kam        | Security better                        |
| Sensitive data ke liye unsuitable | Sensitive data ke liye recommended     |

**Important:** HTTPS ka matlab website completely safe hai, aisa nahi hai. HTTPS connection secure kar sakta hai, lekin malicious website bhi HTTPS use kar sakti hai.

## 5. What is Client-Server Architecture in HTTP?

HTTP communication generally client-server model follow karti hai.

### Client

Client wo application hoti hai jo server ko request bhejti hai.

Examples:

- Google Chrome.
- Firefox.
- Mobile application.
- React frontend.
- Postman.

### Server

Server client ki request receive karke response return karta hai.

Examples:

- Node.js server.
- Express.js server.
- Apache server.
- Nginx server.

### Communication

```text
        CLIENT
     (Browser/App)
          |
          | Request
          v
        SERVER
          |
          | Response
          v
        CLIENT
```

## 6. HTTP Request

HTTP Request ek message hota hai jo client server ko bhejta hai.

Example:

Jab user website open karta hai, browser server ko HTTP request bhej sakta hai.

### HTTP Request Structure

```text
Request Line
Headers

Blank Line

Optional Body
```

### Example Request

```http
GET /users HTTP/1.1
Host: example.com
Accept: application/json
User-Agent: Mozilla/5.0
```

### Request ke Main Parts

**1. Request Method**

Batata hai ki client server par kya action perform karna chahta hai.

Example:

- GET
- POST
- PUT
- PATCH
- DELETE

**2. Request URL/Target**

Batata hai ki server par kis resource ko access karna hai.

Example:

```text
/users
/products
/login
```

**3. HTTP Version**

Example:

```text
HTTP/1.1
```

**4. Headers**

Request ke baare mein additional information provide karte hain.

**5. Body**

Optional data contain karti hai, jaise JSON payload.

## 7. HTTP Response

HTTP Response wo message hai jo server client ko return karta hai.

### HTTP Response Structure

```text
Status Line
Headers

Blank Line

Optional Body
```

### Example Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "name": "Rahul",
  "age": 22
}
```

### Response ke Main Parts

1. HTTP version.
2. Status code.
3. Status message/reason phrase.
4. Response headers.
5. Optional response body.

**Note:** Modern HTTP/2 aur HTTP/3 mein messages ka wire format HTTP/1.1 ki tarah textual nahi hota, lekin request/response concepts largely same rehte hain.

## 8. HTTP Request Methods

HTTP Methods batate hain ki client resource ke saath kis type ka operation karna chahta hai.

### 1. GET

Server se resource/data retrieve karne ke liye use hota hai.

Example:

```http
GET /users
```

Use:

- Users list fetch karna.
- Product details fetch karna.
- Profile information fetch karna.

### 2. POST

Server ko data submit karne ke liye commonly use hota hai.

Example:

```http
POST /users
```

Body:

```json
{
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

Use:

- New user create karna.
- Login request bhejna.
- Form submit karna.

**Important:** POST ka use sirf data create karne ke liye nahi hota. Iska use other processing operations ke liye bhi ho sakta hai.

### 3. PUT

Resource ko create ya completely replace karne ke liye use ho sakta hai.

Example:

```http
PUT /users/10
```

Body:

```json
{
  "name": "Rahul",
  "email": "new@example.com",
  "age": 23
}
```

PUT generally idempotent hota hai.

### 4. PATCH

Resource ke partial updates ke liye use hota hai.

Example:

```http
PATCH /users/10
```

Body:

```json
{
  "age": 24
}
```

PATCH ki idempotency uske implementation aur operation par depend karti hai.

### 5. DELETE

Resource delete karne ke liye use hota hai.

Example:

```http
DELETE /users/10
```

### 6. HEAD

GET jaisi request karta hai, lekin response mein generally body return nahi hoti.

Use:

- Resource metadata check karna.
- Headers check karna.

### 7. OPTIONS

Server ya resource ke supported communication options discover karne ke liye use hota hai.

CORS preflight requests mein iska important role hai.

### 8. CONNECT

HTTP connection ko tunnel mein convert karne ke liye use hota hai, commonly HTTPS proxy tunneling mein.

### 9. TRACE

Request ke communication path ko diagnose karne ke liye defined hai. Security reasons se many servers isse disable rakhte hain.

### HTTP Methods Summary

| Method  | Purpose                    |
| ------- | -------------------------- |
| GET     | Data retrieve              |
| POST    | Data submit/process        |
| PUT     | Create or replace resource |
| PATCH   | Partial update             |
| DELETE  | Delete resource            |
| HEAD    | GET without response body  |
| OPTIONS | Communication options      |
| CONNECT | Create tunnel              |
| TRACE   | Diagnostic request         |

## 9. Safe, Idempotent and Cacheable Methods

Interview mein ye concepts important hain.

### Safe Method

Safe method ka intended purpose server par resource state change karna nahi hota.

Examples:

- GET
- HEAD
- OPTIONS

### Idempotent Method

Idempotent method ko same request multiple times perform karne par intended server-side effect same rehta hai.

Examples:

- GET
- HEAD
- PUT
- DELETE
- OPTIONS
- TRACE

**Important:** DELETE idempotent hai, lekin iska matlab har repeated DELETE request same status code return karegi, aisa nahi. First request 204 aur next request 404 de sakti hai.

### Cacheable Methods

GET responses commonly cacheable hote hain, subject to cache headers and rules.

HEAD responses bhi cache-related behavior support karte hain.

POST responses bhi specific conditions mein cacheable ho sakte hain, lekin commonly POST caching use nahi hoti.

## 10. HTTP Status Codes

HTTP Status Code server ke response ka result batata hai.

Status codes 5 categories mein divided hote hain.

### 1xx – Informational

Request receive hui hai aur processing continue hai.

Examples:

| Code | Meaning             |
| ---- | ------------------- |
| 100  | Continue            |
| 101  | Switching Protocols |

### 2xx – Success

Request successfully receive, understand aur process hui.

| Code | Meaning    |
| ---- | ---------- |
| 200  | OK         |
| 201  | Created    |
| 202  | Accepted   |
| 204  | No Content |

### 3xx – Redirection

Client ko redirect ya additional action ki zaroorat ho sakti hai.

| Code | Meaning            |
| ---- | ------------------ |
| 301  | Moved Permanently  |
| 302  | Found              |
| 304  | Not Modified       |
| 307  | Temporary Redirect |
| 308  | Permanent Redirect |

### 4xx – Client Errors

Client ki request mein problem hoti hai.

| Code | Meaning                                |
| ---- | -------------------------------------- |
| 400  | Bad Request                            |
| 401  | Unauthorized / Authentication Required |
| 403  | Forbidden                              |
| 404  | Not Found                              |
| 405  | Method Not Allowed                     |
| 408  | Request Timeout                        |
| 409  | Conflict                               |
| 422  | Unprocessable Content                  |
| 429  | Too Many Requests                      |

### 5xx – Server Errors

Server request process karte waqt fail hota hai.

| Code | Meaning               |
| ---- | --------------------- |
| 500  | Internal Server Error |
| 501  | Not Implemented       |
| 502  | Bad Gateway           |
| 503  | Service Unavailable   |
| 504  | Gateway Timeout       |

### Important Interview Difference

**401 vs 403**

- 401: Authentication required ya valid authentication credentials missing/invalid hain.
- 403: Server request samajh gaya, lekin access allow nahi kar raha.

**502 vs 504**

- 502: Gateway/proxy ko upstream server se invalid response mila.
- 504: Gateway/proxy ko upstream server se time par response nahi mila.

## 11. HTTP Headers

HTTP Headers request aur response ke saath additional metadata provide karte hain.

Headers mein information hoti hai:

- Content type.
- Authentication.
- Caching.
- Browser information.
- Accepted response formats.
- Connection-related details.

### Common Request Headers

| Header        | Purpose                                   |
| ------------- | ----------------------------------------- |
| Host          | Target host identify karta hai (HTTP/1.1) |
| User-Agent    | Client software information               |
| Accept        | Client accepted media types               |
| Content-Type  | Request body ka media type                |
| Authorization | Authentication credentials                |
| Cookie        | Cookies send karna                        |
| Origin        | Request ka origin                         |
| Referer       | Referring page information                |

### Common Response Headers

| Header                      | Purpose                                    |
| --------------------------- | ------------------------------------------ |
| Content-Type                | Response body ka media type                |
| Content-Length              | Content length in bytes, where applicable  |
| Cache-Control               | Caching rules                              |
| Set-Cookie                  | Browser ko cookie set karne ka instruction |
| Location                    | Redirect/resource location                 |
| Access-Control-Allow-Origin | CORS origin policy                         |
| ETag                        | Resource version identifier                |
| Last-Modified               | Resource modification time                 |

### Example

```http
Content-Type: application/json
Cache-Control: no-store
```

Iska matlab:

- Response body JSON format mein hai.
- Response ko store/cache nahi karna chahiye.

## 12. Content-Type vs Accept

Dono headers interview mein frequently pooche jaate hain.

### Content-Type

Batata hai ki current request ya response body kis format mein hai.

Example:

```http
Content-Type: application/json
```

### Accept

Batata hai ki client kis type ka response receive karna prefer karta hai.

Example:

```http
Accept: application/json
```

| Content-Type                                    | Accept                    |
| ----------------------------------------------- | ------------------------- |
| Current body ka format                          | Preferred response format |
| Request aur response dono mein use ho sakta hai | Primarily request header  |
| Example: application/json                       | Example: text/html        |

## 13. HTTP Request Body and JSON

Client server ko request body mein data bhej sakta hai.

Example:

```http
POST /users HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "name": "Rahul",
  "age": 22
}
```

Common body formats:

- JSON
- Form URL Encoded
- Multipart Form Data
- Plain Text
- XML

### JSON

JSON ka full form JavaScript Object Notation hai.

Example:

```json
{
  "name": "Rahul",
  "age": 22,
  "city": "Delhi"
}
```

MERN applications mein JSON commonly API data exchange ke liye use hota hai.

## 14. HTTP Cookies

Cookie ek small piece of data hota hai jo server browser ko bhej sakta hai aur browser future requests mein applicable rules ke according wapas send karta hai.

Example response:

```http
Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Lax
```

Next request mein browser cookie send kar sakta hai:

```http
Cookie: sessionId=abc123
```

### Cookie Uses

- Session management.
- Login state maintain karna.
- User preferences.
- Tracking, subject to privacy rules.

### Important Cookie Attributes

| Attribute | Purpose                                        |
| --------- | ---------------------------------------------- |
| HttpOnly  | JavaScript se cookie access restrict karta hai |
| Secure    | Cookie HTTPS connections par send hoti hai     |
| SameSite  | Cross-site cookie sending control karta hai    |
| Max-Age   | Cookie lifetime specify karta hai              |
| Expires   | Cookie expiration date specify karta hai       |
| Domain    | Cookie ka domain scope                         |
| Path      | Cookie ka URL path scope                       |

**Security Tip:** Sensitive session cookies ke liye `HttpOnly`, `Secure` aur suitable `SameSite` settings important hain.

## 15. HTTP vs HTTPS – TLS Working

HTTPS mein TLS use hota hai.

Simplified TLS connection process:

1. Client server se secure connection establish karne ki shuruaat karta hai.
2. Client aur server TLS parameters negotiate karte hain.
3. Server apna digital certificate provide kar sakta hai.
4. Client certificate chain aur hostname verify karta hai.
5. TLS handshake ke through session keys establish hoti hain.
6. Application data encrypted form mein exchange hota hai.

### Simplified Diagram

```text
          CLIENT
             |
             | TLS Handshake
             v
          SERVER
             |
             | Certificate
             v
      Certificate Validation
             |
             v
       Session Keys Established
             |
             v
      Encrypted Communication
```

**Important:** Modern TLS versions mein handshake details aur key establishment process more advanced hota hai. Upar diya gaya flow conceptual hai.

## 16. HTTP Versions

HTTP ki different versions hain.

### HTTP/0.9

- Very early version.
- Basic GET request.
- Simple HTML response.

### HTTP/1.0

- Headers introduce hue.
- Different requests ke liye commonly separate connections use hote the.

### HTTP/1.1

- Persistent connections.
- Host header.
- Better caching support.
- Chunked transfer encoding.

### HTTP/2

- Binary framing.
- Multiplexing.
- Header compression (HPACK).
- Single connection par multiple streams.

### HTTP/3

- QUIC transport protocol use karta hai.
- QUIC UDP par operate karta hai.
- TLS 1.3 security integrated hoti hai.
- Stream multiplexing support karta hai.

### HTTP Versions Comparison

| Feature            | HTTP/1.1                   | HTTP/2         | HTTP/3                   |
| ------------------ | -------------------------- | -------------- | ------------------------ |
| Message format     | Text-based                 | Binary framing | Binary framing over QUIC |
| Transport          | TCP                        | TCP            | QUIC over UDP            |
| Multiplexing       | Limited                    | Yes            | Yes                      |
| Header compression | No HPACK                   | HPACK          | QPACK                    |
| TLS                | Optional at protocol level | Commonly used  | Integrated through QUIC  |

**Important:** HTTP/2 mein multiplexing hone ke baad bhi TCP-level packet loss ek connection ke multiple streams ko affect kar sakta hai. HTTP/3 QUIC streams ke through is problem ko reduce karne mein help karta hai.

## 17. What is Stateless Protocol?

HTTP ko traditionally stateless protocol kaha jata hai.

Iska matlab server har request ko independently understand karne ke liye design kiya gaya hai; protocol automatically previous request ki application state maintain nahi karta.

Example:

```text
Request 1: Login
Request 2: Profile
Request 3: Logout
```

HTTP khud automatically ye yaad nahi rakhta ki user login hai ya nahi.

Application session, cookies, tokens aur databases ka use karke state maintain kar sakti hai.

**Important:** Stateless hone ka matlab server kisi bhi tarah ki information store nahi kar sakta, aisa nahi hai.

## 18. HTTP vs WebSocket

| HTTP                                 | WebSocket                                               |
| ------------------------------------ | ------------------------------------------------------- |
| Request-response model               | Persistent two-way communication                        |
| Client request karta hai             | Dono sides messages send kar sakti hain                 |
| Traditional HTTP connection behavior | Connection upgrade/handshake ke baad WebSocket protocol |
| Normal APIs and websites             | Real-time applications                                  |

### WebSocket Uses

- Live chat.
- Multiplayer games.
- Real-time notifications.
- Live dashboards.

WebSocket commonly `ws://` aur secure WebSocket `wss://` schemes use karta hai.

## 19. CORS – Cross-Origin Resource Sharing

CORS ka full form Cross-Origin Resource Sharing hai.

Ye browser-based security mechanism hai jo control karta hai ki ek origin se chalne wala web page doosre origin ke resources access kar sakta hai ya nahi.

### What is an Origin?

Origin ke 3 main parts hote hain:

1. Scheme (HTTP/HTTPS)
2. Hostname
3. Port

Example:

```text
http://localhost:3000
http://localhost:5000
```

Dono ka hostname same hai, lekin ports different hain. Isliye ye different origins hain.

### Example

React frontend:

```text
http://localhost:3000
```

Express backend:

```text
http://localhost:5000
```

Browser CORS policy apply kar sakta hai.

Backend ko suitable CORS headers return karne hote hain.

### Express.js Example

```javascript
const express = require("express");
const cors = require("cors");

const app = express();

app.use(
  cors({
    origin: "http://localhost:3000",
  }),
);

app.get("/users", (req, res) => {
  res.json([{ name: "Rahul" }, { name: "Aman" }]);
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

### CORS Important Points

- CORS mainly browser-enforced security mechanism hai.
- CORS authentication ka replacement nahi hai.
- CORS server ko malicious requests se universally protect nahi karta.
- Non-browser clients par browser CORS restrictions apply nahi hoti.
- Preflight requests mein browser OPTIONS request bhej sakta hai.

## 20. HTTP in MERN Stack

MERN application mein HTTP frontend aur backend ke beech communication ka common medium hai.

Example architecture:

```text
          React Frontend
                |
                | HTTP Request
                v
          Express Backend
                |
                v
          Node.js Runtime
                |
                v
             MongoDB
                |
                v
          JSON Response
                |
                v
          React Frontend
```

### Example: Fetch API

React/JavaScript se API call:

```javascript
fetch("http://localhost:5000/users")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Request Failed");
    }

    return response.json();
  })
  .then((data) => {
    console.log(data);
  })
  .catch((error) => {
    console.log(error.message);
  });
```

### Example: Express Backend

```javascript
const express = require("express");

const app = express();

app.use(express.json());

app.get("/users", (req, res) => {
  res.status(200).json({
    message: "Users fetched successfully",
    users: ["Rahul", "Aman"],
  });
});

app.post("/users", (req, res) => {
  const user = req.body;

  res.status(201).json({
    message: "User created",
    user,
  });
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

### Important Express Methods

| Method         | Purpose                   |
| -------------- | ------------------------- |
| `req.params`   | URL route parameters      |
| `req.query`    | URL query parameters      |
| `req.body`     | Request body              |
| `req.headers`  | Request headers           |
| `res.status()` | Response status set karna |
| `res.json()`   | JSON response send karna  |
| `res.send()`   | Response send karna       |

## 21. HTTP Authentication

Authentication ka purpose user ki identity verify karna hai.

Common methods:

### 1. Basic Authentication

Username aur password ko Base64 encoding ke saath Authorization header mein send kiya jata hai.

Example:

```http
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

Base64 encryption nahi hai. HTTPS ke bina Basic Authentication secure nahi hoti.

### 2. Bearer Token Authentication

Client request mein token send karta hai.

Example:

```http
Authorization: Bearer YOUR_TOKEN
```

### 3. Session-Based Authentication

Server session maintain karta hai aur browser commonly session cookie send karta hai.

### 4. JWT-Based Authentication

JWT ka full form JSON Web Token hai.

Token ko request ke saath send kiya ja sakta hai.

Example:

```http
Authorization: Bearer YOUR_JWT
```

**Important:** Authentication aur Authorization alag concepts hain.

- Authentication = Tum kaun ho?
- Authorization = Tumhe kya access karne ki permission hai?

## 22. HTTP Caching

HTTP caching ka purpose repeated resource requests ko efficiently handle karna hai.

Common cache headers:

### Cache-Control

```http
Cache-Control: max-age=3600
```

Resource ko specified caching rules ke according 3600 seconds tak fresh maana ja sakta hai.

### ETag

ETag resource ka validator hota hai.

Example:

```http
ETag: "abc123"
```

Client next request mein `If-None-Match` bhej sakta hai.

### Last-Modified

Resource ki last modification time provide karta hai.

Client `If-Modified-Since` bhej sakta hai.

Agar resource change nahi hua, server `304 Not Modified` return kar sakta hai.

## 23. Common HTTP Errors and Troubleshooting

| Error | Possible Meaning        |
| ----- | ----------------------- |
| 400   | Invalid request         |
| 401   | Authentication required |
| 403   | Access forbidden        |
| 404   | Resource not found      |
| 405   | Method not allowed      |
| 429   | Too many requests       |
| 500   | Server error            |
| 502   | Bad gateway             |
| 503   | Service unavailable     |
| 504   | Gateway timeout         |

### MERN Debugging Example

Agar React frontend API call kar raha hai aur 404 error aa raha hai, check karo:

1. API URL correct hai ya nahi.
2. Backend server running hai ya nahi.
3. Express route defined hai ya nahi.
4. HTTP method correct hai ya nahi.
5. Route path match kar raha hai ya nahi.

Agar CORS error aa raha hai, check karo:

1. Frontend origin.
2. Backend CORS configuration.
3. Allowed methods.
4. Allowed headers.
5. Preflight response.

## 24. Common Interview Questions and Answers

### Q1. What is HTTP?

HTTP ek application-layer protocol hai jo client aur server ke beech request-response communication enable karta hai.

### Q2. What is HTTPS?

HTTPS HTTP communication ko TLS ke through secure karta hai.

### Q3. What is the default HTTP port?

80.

### Q4. What is the default HTTPS port?

443.

### Q5. What is an HTTP Request?

Client ka server ko bheja gaya message HTTP Request hota hai.

### Q6. What is an HTTP Response?

Server ka client ko return kiya gaya message HTTP Response hota hai.

### Q7. What are HTTP Methods?

HTTP Methods client ke requested operation ko define karte hain, jaise GET, POST, PUT, PATCH aur DELETE.

### Q8. Difference between PUT and PATCH?

PUT generally resource ko completely replace karta hai, jabki PATCH partial update karta hai.

### Q9. What is HTTP Status Code?

Status code response ka result ya request processing status indicate karta hai.

### Q10. Difference between 401 and 403?

401 authentication se related hai, jabki 403 access permission deny hone ko indicate karta hai.

### Q11. What is a Stateless Protocol?

HTTP stateless protocol hai, jisme protocol automatically previous request ki application state maintain nahi karta.

### Q12. What is HTTPS Security Based On?

HTTPS TLS use karta hai jo encryption, integrity aur server authentication provide karne mein help karta hai.

### Q13. What is CORS?

CORS browser-based mechanism hai jo cross-origin resource access control karta hai.

### Q14. What is a Cookie?

Cookie browser mein store kiya gaya small data hota hai jo sessions aur preferences maintain karne mein help kar sakta hai.

### Q15. What is HTTP/2?

HTTP/2 HTTP ka version hai jo binary framing, multiplexing aur HPACK header compression support karta hai.

### Q16. What is HTTP/3?

HTTP/3 HTTP ka version hai jo QUIC transport protocol use karta hai.

### Q17. What is the difference between HTTP and WebSocket?

HTTP traditional request-response model use karta hai, jabki WebSocket persistent two-way communication support karta hai.

### Q18. What is an OPTIONS Request?

OPTIONS request resource ya server ke supported communication options discover karne mein help karti hai.

### Q19. What is an Idempotent Method?

Aisa method jiske same request ko multiple times perform karne par intended server-side effect same rahe.

### Q20. What is the difference between Authentication and Authorization?

Authentication identity verify karta hai, authorization access permissions determine karta hai.

## 25. Common Mistakes

1. HTTP aur HTTPS ko same samajhna.
2. HTTPS ko complete website safety guarantee samajhna.
3. GET aur POST ko interchangeable samajhna.
4. PUT aur PATCH ka difference bhoolna.
5. 401 aur 403 ko same samajhna.
6. 502 aur 504 ko same samajhna.
7. Content-Type aur Accept ko same samajhna.
8. Base64 encoding ko encryption samajhna.
9. CORS ko authentication mechanism samajhna.
10. HTTP ko stateful protocol samajhna.
11. HTTP/3 ko TCP par based samajhna.
12. DELETE ko non-idempotent samajhna.

## 26. Quick Revision

- HTTP = Hypertext Transfer Protocol.
- HTTPS = HTTP Secure.
- HTTP application-layer protocol hai.
- HTTP default port = 80.
- HTTPS default port = 443.
- HTTPS TLS use karta hai.
- Request client se server ko jaati hai.
- Response server se client ko aata hai.
- GET = Retrieve.
- POST = Submit/process.
- PUT = Replace/create.
- PATCH = Partial update.
- DELETE = Delete.
- HEAD = GET without response body.
- OPTIONS = Communication options.
- 2xx = Success.
- 3xx = Redirection.
- 4xx = Client error.
- 5xx = Server error.
- 200 = OK.
- 201 = Created.
- 301 = Moved Permanently.
- 400 = Bad Request.
- 401 = Unauthorized/authentication required.
- 403 = Forbidden.
- 404 = Not Found.
- 500 = Internal Server Error.
- 502 = Bad Gateway.
- 503 = Service Unavailable.
- 504 = Gateway Timeout.
- CORS = Cross-Origin Resource Sharing.
- HTTP stateless protocol hai.
- HTTP/2 = Multiplexing.
- HTTP/3 = QUIC over UDP.

## 27. Practical Tasks

### Task 1: Browser Mein HTTP Headers Dekho

1. Chrome open karo.
2. Kisi website ko open karo.
3. Press `F12`.
4. Network tab select karo.
5. Page refresh karo.
6. Kisi request par click karo.
7. Headers section observe karo.

### Task 2: API Request Test Karo

Browser mein open karo:

```text
https://jsonplaceholder.typicode.com/users
```

JSON response observe karo.

### Task 3: Browser Developer Tools

Network tab mein observe karo:

- Request URL.
- Request Method.
- Status Code.
- Request Headers.
- Response Headers.
- Response Body.
- Timing.

### Task 4: Express API Banao

GET route banao:

```javascript
app.get("/products", (req, res) => {
  res.status(200).json({
    products: ["Laptop", "Mobile"],
  });
});
```

POST route banao:

```javascript
app.post("/products", (req, res) => {
  res.status(201).json({
    message: "Product created",
  });
});
```

### Task 5: Status Codes Test Karo

Express mein alag-alag status codes return karke browser ya Postman mein observe karo.

---

## 28. Interview Practice Quiz – 10 Questions

**Q1. HTTP ka full form kya hai?**

A. Hyper Text Transfer Protocol  
B. High Transfer Text Protocol  
C. Hyper Tool Transfer Process  
D. Host Text Transfer Protocol

**Q2. HTTPS ka default port kya hai?**

A. 80  
B. 443  
C. 21  
D. 53

**Q3. GET method ka main purpose kya hai?**

A. Data delete karna  
B. Data retrieve karna  
C. Server shutdown karna  
D. Database create karna

**Q4. Kaunsa status code successful resource creation indicate karta hai?**

A. 200  
B. 201  
C. 404  
D. 500

**Q5. 404 ka meaning kya hai?**

A. Server Error  
B. Unauthorized  
C. Not Found  
D. Success

**Q6. PUT aur PATCH mein main difference kya hai?**

A. Dono same hain  
B. PUT generally replace karta hai, PATCH partial update  
C. PATCH data delete karta hai  
D. PUT sirf GET ke liye hai

**Q7. HTTPS mein security ke liye kya use hota hai?**

A. FTP  
B. TLS  
C. DHCP  
D. DNS

**Q8. CORS ka full form kya hai?**

A. Cross-Origin Resource Sharing  
B. Common Object Request Service  
C. Client Origin Response System  
D. Cross Online Request Security

**Q9. HTTP/3 kis transport protocol par operate karta hai?**

A. TCP  
B. FTP  
C. QUIC over UDP  
D. SMTP

**Q10. HTTP ko traditionally kya kaha jata hai?**

A. Stateful Protocol  
B. Stateless Protocol  
C. Hardware Protocol  
D. Database Protocol

### Answer Key

1. A – Hypertext Transfer Protocol
2. B – 443
3. B – Data retrieve karna
4. B – 201
5. C – Not Found
6. B – PUT generally replace karta hai, PATCH partial update
7. B – TLS
8. A – Cross-Origin Resource Sharing
9. C – QUIC over UDP
10. B – Stateless Protocol

---

**Topic 15 Completed – HTTP and HTTPS**
