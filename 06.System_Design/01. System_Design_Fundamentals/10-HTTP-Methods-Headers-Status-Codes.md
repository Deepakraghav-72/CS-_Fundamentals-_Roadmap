# Topic 10: HTTP Methods, Headers & Status Codes

## 1. Introduction

HTTP communication mein client aur server ke beech request aur response exchange hote hain.

Is communication ke 3 important parts hain:

1. HTTP Methods
2. HTTP Headers
3. HTTP Status Codes

In teeno ko samajhna API development aur System Design ke liye important hai.

Example:

Jab React frontend Express backend se users ka data fetch karta hai:

```http
GET /api/users HTTP/1.1
Host: example.com
Accept: application/json
```

Server response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": 1,
    "name": "Rahul"
  }
]
```

Is example mein:

- GET = HTTP Method.
- Host aur Accept = Request Headers.
- 200 OK = HTTP Status Code.
- Content-Type = Response Header.

# PART 1: HTTP METHODS

## 2. HTTP Methods Kya Hote Hain?

HTTP Methods batate hain ki client server par kisi resource ke saath kya action perform karna chahta hai.

Simple words mein:

**HTTP Method = Server ko batana ki kya action perform karna hai.**

Example:

```text
GET    /api/users
POST   /api/users
PUT    /api/users/10
PATCH  /api/users/10
DELETE /api/users/10
```

## 3. GET Method

GET method ka use server se data retrieve karne ke liye hota hai.

Example:

```http
GET /api/users HTTP/1.1
```

Meaning: Server se users ki list maango.

### Express Example

```javascript
app.get("/api/users", (req, res) => {
  res.status(200).json([
    { id: 1, name: "Rahul" },
    { id: 2, name: "Aman" },
  ]);
});
```

### Important Points

- Data retrieve karne ke liye use hota hai.
- Normally request body use nahi hoti.
- GET method safe hota hai.
- GET method idempotent hota hai.

## 4. POST Method

POST method ka use server ko data submit karne ke liye hota hai.

Iska common use new resource create karna hai.

Example:

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

### Express Example

```javascript
app.use(express.json());

app.post("/api/users", (req, res) => {
  const user = req.body;

  res.status(201).json({
    message: "User created successfully",
    user,
  });
});
```

### Important Points

- Data server ko send karta hai.
- Commonly resource create karne ke liye use hota hai.
- Request body commonly use hoti hai.
- POST generally idempotent nahi hota.

## 5. PUT Method

PUT method ka use kisi resource ko completely replace karne ke liye hota hai.

Example:

Existing user:

```json
{
  "id": 10,
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

Request:

```http
PUT /api/users/10 HTTP/1.1
Content-Type: application/json

{
  "name": "Aman",
  "email": "aman@example.com"
}
```

Server resource ko supplied representation ke according replace karta hai.

### Express Example

```javascript
app.put("/api/users/:id", (req, res) => {
  const { id } = req.params;
  const updatedUser = req.body;

  res.status(200).json({
    message: `User ${id} replaced`,
    updatedUser,
  });
});
```

Note: Ye illustrative example hai. Real application mein database mein existing record find aur update karna hoga.

## 6. PATCH Method

PATCH method ka use resource ko partially update karne ke liye hota hai.

Example:

Existing user:

```json
{
  "id": 10,
  "name": "Rahul",
  "email": "rahul@example.com",
  "age": 22
}
```

Request:

```http
PATCH /api/users/10 HTTP/1.1
Content-Type: application/json

{
  "age": 23
}
```

Yahan sirf age update karne ka instruction diya gaya hai.

### Express Example

```javascript
app.patch("/api/users/:id", (req, res) => {
  const { id } = req.params;
  const updates = req.body;

  res.status(200).json({
    message: `User ${id} partially updated`,
    updates,
  });
});
```

## 7. DELETE Method

DELETE method ka use resource delete karne ke liye hota hai.

Example:

```http
DELETE /api/users/10 HTTP/1.1
```

### Express Example

```javascript
app.delete("/api/users/:id", (req, res) => {
  const { id } = req.params;

  res.status(200).json({
    message: `User ${id} deleted`,
  });
});
```

Real application mein database record delete ya soft-delete karna hoga.

## 8. HEAD Method

HEAD method GET ke similar hota hai.

Difference:

- GET response mein headers aur body aa sakte hain.
- HEAD response mein headers aate hain, body nahi.

Example:

```http
HEAD /api/users HTTP/1.1
```

Use:

- Resource available hai ya nahi check karna.
- Headers check karna.
- Content-Length jaise metadata check karna.

## 9. OPTIONS Method

OPTIONS method server se available communication options ke baare mein information maangta hai.

Example:

```http
OPTIONS /api/users HTTP/1.1
```

Server response:

```http
HTTP/1.1 204 No Content
Allow: GET, POST, PUT, PATCH, DELETE, OPTIONS
```

OPTIONS method CORS preflight requests mein bhi important role play karta hai.

## 10. CONNECT Method

CONNECT method client ko server ke through target server tak tunnel establish karne deta hai.

Iska common use HTTPS proxy tunneling mein hota hai.

Example:

```http
CONNECT example.com:443 HTTP/1.1
Host: example.com:443
```

## 11. TRACE Method

TRACE method diagnostic purpose ke liye request ko server tak trace karne ke liye designed hai.

Security reasons se production servers mein ise commonly disable rakha jata hai.

## 12. Safe Methods Kya Hote Hain?

Safe method wo hota hai jiska intended purpose server par requested resource ki state change karna nahi hota.

Common safe methods:

- GET
- HEAD
- OPTIONS
- TRACE

Example:

GET request se user profile read karna safe operation hai.

Important: Safe ka matlab ye nahi ki request se koi side effect kabhi ho hi nahi sakta. Logging jaise incidental effects ho sakte hain.

## 13. Idempotent Methods Kya Hote Hain?

Idempotent method ka meaning hai:

**Same request ko ek ya multiple times perform karne par intended server-side effect same rehta hai.**

Example:

```http
DELETE /api/users/10
```

First request user delete kar sakti hai.

Second request par user already deleted ho sakta hai.

Lekin intended final state same hai: user resource exist nahi karta.

### Common Idempotent Methods

- GET
- HEAD
- PUT
- DELETE
- OPTIONS
- TRACE

POST generally idempotent nahi hota.

PATCH ka idempotency behavior uske implementation par depend karta hai.

## 14. Safe vs Idempotent

| Method  | Safe? | Idempotent?    |
| ------- | ----- | -------------- |
| GET     | Yes   | Yes            |
| HEAD    | Yes   | Yes            |
| POST    | No    | Generally No   |
| PUT     | No    | Yes            |
| PATCH   | No    | Not guaranteed |
| DELETE  | No    | Yes            |
| OPTIONS | Yes   | Yes            |
| TRACE   | Yes   | Yes            |
| CONNECT | No    | No             |

Important:

- Safe = Intended operation resource state change nahi karta.
- Idempotent = Repeated requests ka intended effect same rehta hai.

## 15. GET vs POST

| GET                          | POST                            |
| ---------------------------- | ------------------------------- |
| Data retrieve karta hai      | Data submit karta hai           |
| Parameters commonly URL mein | Data commonly request body mein |
| Safe                         | Not safe                        |
| Idempotent                   | Generally not idempotent        |
| Read operations              | Create/submit operations        |

Important: POST ka data automatically encrypted nahi hota. Sensitive data ke liye HTTPS required hai.

## 16. PUT vs PATCH

| PUT                                   | PATCH                               |
| ------------------------------------- | ----------------------------------- |
| Resource replace karne ke liye        | Partial modification ke liye        |
| Complete representation bhejna common | Sirf required changes bhejna common |
| Idempotent                            | Implementation par depend           |
| Full update                           | Partial update                      |

Example:

PUT:

```json
{
  "name": "Rahul",
  "age": 23,
  "city": "Delhi"
}
```

PATCH:

```json
{
  "city": "Delhi"
}
```

# PART 2: HTTP HEADERS

## 17. HTTP Headers Kya Hote Hain?

HTTP Headers request aur response ke saath additional information ya metadata provide karte hain.

Simple words mein:

**Headers = Request/Response ke baare mein extra information.**

Example:

```http
GET /api/users HTTP/1.1
Host: example.com
Accept: application/json
Authorization: Bearer TOKEN
```

Yahan:

- Host = Target host.
- Accept = Client ko acceptable response format.
- Authorization = Authentication credentials.

## 18. Request Headers

Request headers client server ko send karta hai.

Important request headers:

| Header          | Purpose                         |
| --------------- | ------------------------------- |
| Host            | Target host identify karta hai  |
| Accept          | Acceptable response media types |
| Accept-Language | Preferred language              |
| Accept-Encoding | Supported compression formats   |
| Authorization   | Authentication credentials      |
| User-Agent      | Client software information     |
| Cookie          | Stored cookies send karta hai   |
| Origin          | Request ka origin               |
| Referer         | Referring page ka address       |
| Content-Type    | Request body ka media type      |
| Content-Length  | Request body ki length          |
| Cache-Control   | Request caching directives      |

### Example

```http
POST /api/login HTTP/1.1
Host: example.com
Content-Type: application/json
Accept: application/json
Authorization: Bearer abc123

{
  "email": "rahul@example.com",
  "password": "123456"
}
```

## 19. Response Headers

Response headers server client ko send karta hai.

Important response headers:

| Header                      | Purpose                                  |
| --------------------------- | ---------------------------------------- |
| Content-Type                | Response body ka media type              |
| Content-Length              | Response body length                     |
| Cache-Control               | Caching instructions                     |
| Set-Cookie                  | Browser ke liye cookie set karta hai     |
| Location                    | Redirect/new resource location           |
| Server                      | Server software information, if provided |
| ETag                        | Resource version identifier              |
| Last-Modified               | Resource modification time               |
| Access-Control-Allow-Origin | Allowed origin for CORS                  |
| Content-Encoding            | Response body encoding                   |

### Example

```http
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: no-store
Content-Length: 45

{
  "message": "Login successful"
}
```

## 20. Content-Type Kya Hai?

Content-Type batata hai ki message body mein kis type ka data hai.

Examples:

| Content-Type        | Meaning              |
| ------------------- | -------------------- |
| application/json    | JSON data            |
| text/html           | HTML document        |
| text/plain          | Plain text           |
| image/png           | PNG image            |
| image/jpeg          | JPEG image           |
| application/pdf     | PDF document         |
| multipart/form-data | Form data with files |

Example:

```http
Content-Type: application/json
```

Meaning: Request ya response body JSON format mein hai.

## 21. Accept Header Kya Hai?

Accept header batata hai ki client ko kaun-se response media types acceptable hain.

Example:

```http
Accept: application/json
```

Meaning: Client JSON response prefer karta hai.

Multiple types:

```http
Accept: application/json, text/html
```

Server supported formats ke according response select kar sakta hai.

## 22. Authorization Header Kya Hai?

Authorization header ka use server ko authentication credentials send karne ke liye hota hai.

Example:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Bearer token ka use API authentication mein common hai.

Example:

```javascript
fetch("https://api.example.com/profile", {
  headers: {
    Authorization: "Bearer YOUR_ACCESS_TOKEN",
  },
});
```

Important:

- Token secret rakho.
- HTTPS use karo.
- Token ko logs ya public GitHub repository mein expose mat karo.
- Server ko token validate karna hota hai.

## 23. Cookie Aur Set-Cookie Headers

Cookies browser aur server ke beech small pieces of data store aur transfer karne mein help karti hain.

### Set-Cookie

Server browser ko cookie set karne ka instruction deta hai.

```http
Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Lax
```

### Cookie

Browser next matching request mein cookie send kar sakta hai.

```http
Cookie: sessionId=abc123
```

Important cookie attributes:

| Attribute | Purpose                                                                |
| --------- | ---------------------------------------------------------------------- |
| HttpOnly  | JavaScript se cookie access restrict karta hai                         |
| Secure    | Cookie ko secure connections par send karne ke liye restrict karta hai |
| SameSite  | Cross-site cookie sending control karta hai                            |
| Max-Age   | Cookie ki lifetime seconds mein                                        |
| Expires   | Cookie expiry date                                                     |

Cookies aur sessions Topic 13 mein detail se padhenge.

## 24. Cache-Control Header

Cache-Control define karta hai ki browser aur intermediate caches response ko kaise cache kar sakte hain.

Common directives:

| Directive       | Meaning                                               |
| --------------- | ----------------------------------------------------- |
| no-store        | Response ko cache store nahi karna                    |
| no-cache        | Reuse se pehle validation required                    |
| public          | Shared caches mein store allowed                      |
| private         | Shared cache mein store nahi karna                    |
| max-age         | Freshness lifetime seconds mein                       |
| must-revalidate | Stale response use karne se pehle validation required |

Example:

```http
Cache-Control: public, max-age=3600
```

Meaning: Response ko eligible caches mein store kiya ja sakta hai aur 3600 seconds tak fresh maana ja sakta hai.

Important: `no-cache` ka matlab `no-store` nahi hota. `no-cache` response ko store karne de sakta hai, lekin reuse se pehle validation require karta hai.

# PART 3: HTTP STATUS CODES

## 25. HTTP Status Codes Kya Hote Hain?

HTTP Status Code ek numeric code hota hai jo server response ka result indicate karta hai.

Example:

```http
HTTP/1.1 200 OK
```

Yahan 200 status code hai.

Status codes ki five categories hoti hain:

| Category | Range   | Meaning       |
| -------- | ------- | ------------- |
| 1xx      | 100–199 | Informational |
| 2xx      | 200–299 | Success       |
| 3xx      | 300–399 | Redirection   |
| 4xx      | 400–499 | Client Error  |
| 5xx      | 500–599 | Server Error  |

## 26. 1xx – Informational Status Codes

Ye indicate karte hain ki request receive hui aur processing continue ho sakti hai.

| Code | Meaning             |
| ---- | ------------------- |
| 100  | Continue            |
| 101  | Switching Protocols |
| 102  | Processing          |
| 103  | Early Hints         |

Example:

100 Continue: Client body send karne ke liye continue kar sakta hai.

## 27. 2xx – Success Status Codes

Ye indicate karte hain ki request successfully process hui.

| Code | Meaning         | Use                                                          |
| ---- | --------------- | ------------------------------------------------------------ |
| 200  | OK              | Successful request                                           |
| 201  | Created         | Resource created                                             |
| 202  | Accepted        | Processing ke liye accept hui, complete hona guaranteed nahi |
| 204  | No Content      | Success, response body nahi                                  |
| 206  | Partial Content | Partial resource return hua                                  |

### Example: 200 OK

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "name": "Rahul"
}
```

### Example: 201 Created

```http
HTTP/1.1 201 Created
Location: /api/users/10
```

### Example: 204 No Content

```http
HTTP/1.1 204 No Content
```

Is response mein body nahi hoti.

## 28. 3xx – Redirection Status Codes

Ye indicate karte hain ki request complete karne ke liye redirection ya additional action ho sakta hai.

| Code | Meaning            |
| ---- | ------------------ |
| 301  | Moved Permanently  |
| 302  | Found              |
| 303  | See Other          |
| 304  | Not Modified       |
| 307  | Temporary Redirect |
| 308  | Permanent Redirect |

### 301 vs 302

| 301                           | 302                                           |
| ----------------------------- | --------------------------------------------- |
| Permanent redirect            | Temporary redirect                            |
| Resource permanently move hua | Resource temporarily another location par hai |

### 307 vs 308

In redirects mein original HTTP method aur request body preserve ki jati hai.

- 307 = Temporary redirect.
- 308 = Permanent redirect.

### 304 Not Modified

Client ke cached resource ko reuse kiya ja sakta hai, kyunki validation ke according resource change nahi hua.

## 29. 4xx – Client Error Status Codes

Ye indicate karte hain ki request mein client-side problem hai.

| Code | Meaning                | Example                                                  |
| ---- | ---------------------- | -------------------------------------------------------- |
| 400  | Bad Request            | Invalid request data                                     |
| 401  | Unauthorized           | Missing/invalid authentication                           |
| 403  | Forbidden              | Access denied                                            |
| 404  | Not Found              | Resource nahi mila                                       |
| 405  | Method Not Allowed     | Unsupported method for resource                          |
| 408  | Request Timeout        | Request time par receive nahi hui                        |
| 409  | Conflict               | Current resource state se conflict                       |
| 410  | Gone                   | Resource permanently unavailable                         |
| 413  | Content Too Large      | Request body too large                                   |
| 415  | Unsupported Media Type | Unsupported content type                                 |
| 422  | Unprocessable Content  | Content understood, but instructions cannot be processed |
| 429  | Too Many Requests      | Rate limit exceed                                        |

### 401 vs 403

**401 Unauthorized:**

Valid authentication credentials nahi hain ya credentials invalid hain.

**403 Forbidden:**

Server request samajh gaya, lekin requested action ki permission nahi hai.

Example:

- User login nahi hai = 401 ho sakta hai.
- User login hai, lekin admin-only page access kar raha hai = 403 ho sakta hai.

## 30. 5xx – Server Error Status Codes

Ye indicate karte hain ki server request process nahi kar pa raha.

| Code | Meaning               | Example                               |
| ---- | --------------------- | ------------------------------------- |
| 500  | Internal Server Error | Unexpected backend error              |
| 501  | Not Implemented       | Required functionality supported nahi |
| 502  | Bad Gateway           | Upstream server se invalid response   |
| 503  | Service Unavailable   | Server temporarily unavailable        |
| 504  | Gateway Timeout       | Upstream server response late         |

### 500 Internal Server Error

Example:

Express backend mein unexpected exception aa gaya.

### 502 Bad Gateway

Gateway ya proxy ko upstream server se invalid response mila.

### 503 Service Unavailable

Server maintenance ya overload ke karan temporarily unavailable ho sakta hai.

### 504 Gateway Timeout

Gateway ko upstream server se time par response nahi mila.

## 31. 401 vs 403 vs 404 vs 500

| Code | Simple Meaning                   |
| ---- | -------------------------------- |
| 401  | Authentication missing/invalid   |
| 403  | Permission nahi hai              |
| 404  | Resource nahi mila               |
| 500  | Server ke andar unexpected error |

Ye four status codes interviews aur real development mein bahut important hain.

# PART 4: MERN STACK PRACTICAL

## 32. Express Mein Status Codes Ka Use

Express mein `res.status()` se response status code set kar sakte hain.

Example:

```javascript
app.get("/api/users", (req, res) => {
  res.status(200).json({
    message: "Users fetched successfully",
  });
});
```

User create:

```javascript
app.post("/api/users", (req, res) => {
  res.status(201).json({
    message: "User created successfully",
  });
});
```

Invalid request:

```javascript
app.post("/api/users", (req, res) => {
  if (!req.body.name) {
    return res.status(400).json({
      message: "Name is required",
    });
  }

  res.status(201).json({
    message: "User created",
  });
});
```

User not found:

```javascript
app.get("/api/users/:id", async (req, res) => {
  const user = null; // Illustrative example

  if (!user) {
    return res.status(404).json({
      message: "User not found",
    });
  }

  res.status(200).json(user);
});
```

Server error:

```javascript
app.get("/api/data", async (req, res) => {
  try {
    // Database operation

    res.status(200).json({
      message: "Success",
    });
  } catch (error) {
    res.status(500).json({
      message: "Internal Server Error",
    });
  }
});
```

Production application mein errors ko properly log karna chahiye aur internal error details client ko expose nahi karni chahiye.

## 33. Complete HTTP API Example

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

// GET: Single user
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

// PATCH: Update user
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

// DELETE: Delete user
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
  console.log("Server running on port 5000");
});
```

Note: Ye in-memory learning example hai. Server restart hone par data reset ho jayega. Real MERN project mein MongoDB use karenge.

# PART 5: PRACTICAL TESTING

## 34. Browser Network Tab

1. Chrome open karo.
2. Kisi website ko open karo.
3. F12 press karo.
4. Network tab open karo.
5. Page reload karo.
6. Kisi request par click karo.

Observe:

- Request Method.
- Request URL.
- Status Code.
- Request Headers.
- Response Headers.
- Payload.
- Response.

## 35. CMD Se HTTP Methods Test Karna

### GET

```cmd
curl -i https://jsonplaceholder.typicode.com/posts/1
```

### POST

```cmd
curl -i -X POST https://jsonplaceholder.typicode.com/posts -H "Content-Type: application/json" -d "{\"title\":\"Hello\",\"body\":\"Testing\",\"userId\":1}"
```

### PUT

```cmd
curl -i -X PUT https://jsonplaceholder.typicode.com/posts/1 -H "Content-Type: application/json" -d "{\"id\":1,\"title\":\"Updated\",\"body\":\"New body\",\"userId\":1}"
```

### PATCH

```cmd
curl -i -X PATCH https://jsonplaceholder.typicode.com/posts/1 -H "Content-Type: application/json" -d "{\"title\":\"Updated title\"}"
```

### DELETE

```cmd
curl -i -X DELETE https://jsonplaceholder.typicode.com/posts/1
```

Note: JSONPlaceholder testing API hai. Iske mutation requests simulated hain; permanent database changes expect mat karna.

# PART 6: COMMON MISTAKES

## 36. Developers Ki Common Mistakes

1. GET method se data create karna.
2. POST aur PUT ko same samajhna.
3. PUT aur PATCH ka difference bhoolna.
4. Har successful request par 200 use karna.
5. Resource create hone par 201 ki jagah galat status code dena.
6. 401 aur 403 confuse karna.
7. 404 aur 500 confuse karna.
8. Sensitive information URL mein send karna.
9. Authorization token expose karna.
10. Content-Type galat set karna.
11. `no-cache` aur `no-store` ko same samajhna.
12. DELETE ko non-idempotent samajhna.

# PART 7: INTERVIEW QUESTIONS

## 37. Important Interview Questions

**Q1. What are HTTP methods?**

Ans: HTTP methods define the intended action that a client wants to perform on a resource.

**Q2. What is the difference between GET and POST?**

Ans: GET retrieves data, whereas POST submits data and is commonly used to create resources.

**Q3. What is the difference between PUT and PATCH?**

Ans: PUT generally replaces a resource representation, while PATCH applies partial modifications.

**Q4. What is an idempotent method?**

Ans: A method is idempotent if repeating the same request has the same intended effect as performing it once.

**Q5. Is POST idempotent?**

Ans: Generally, no. Repeating a POST request may create multiple resources.

**Q6. Is DELETE idempotent?**

Ans: Yes. Repeating a DELETE request has the same intended final effect: the resource remains deleted.

**Q7. What is a safe HTTP method?**

Ans: A method whose defined semantics are read-only and do not intend to change server resource state.

**Q8. What are HTTP headers?**

Ans: Headers provide metadata about HTTP requests and responses.

**Q9. What is Content-Type?**

Ans: It indicates the media type of the message body.

**Q10. What is the Accept header?**

Ans: It tells the server which response media types the client can accept.

**Q11. What is the Authorization header?**

Ans: It carries credentials used for authentication or authorization.

**Q12. What is Cache-Control?**

Ans: It defines caching directives for browsers and intermediary caches.

**Q13. What does status code 201 mean?**

Ans: The request was successful and resulted in a resource being created.

**Q14. What is the difference between 401 and 403?**

Ans: 401 indicates missing or invalid authentication credentials; 403 indicates the server refuses the requested action.

**Q15. What is the difference between 502 and 504?**

Ans: 502 means a gateway received an invalid response from an upstream server. 504 means it did not receive an upstream response in time.

**Q16. When should we use 204?**

Ans: When a request succeeds but there is no response content to return.

# PART 8: QUICK REVISION

## 38. Quick Revision Table

| Concept          | Meaning                                           |
| ---------------- | ------------------------------------------------- |
| GET              | Retrieve data                                     |
| POST             | Submit/create                                     |
| PUT              | Replace resource                                  |
| PATCH            | Partial update                                    |
| DELETE           | Delete resource                                   |
| HEAD             | GET without response body                         |
| OPTIONS          | Discover communication options                    |
| CONNECT          | Establish tunnel                                  |
| TRACE            | Diagnostic request tracing                        |
| Safe             | Intended operation does not change resource state |
| Idempotent       | Repeated requests have same intended effect       |
| Request Headers  | Client metadata                                   |
| Response Headers | Server metadata                                   |
| Content-Type     | Body ka media type                                |
| Accept           | Acceptable response media types                   |
| Authorization    | Credentials                                       |
| Cookie           | Client cookie data                                |
| Set-Cookie       | Set browser cookie                                |
| Cache-Control    | Caching instructions                              |
| 200              | OK                                                |
| 201              | Created                                           |
| 204              | No Content                                        |
| 301              | Permanent Redirect                                |
| 304              | Not Modified                                      |
| 400              | Bad Request                                       |
| 401              | Unauthorized                                      |
| 403              | Forbidden                                         |
| 404              | Not Found                                         |
| 409              | Conflict                                          |
| 429              | Too Many Requests                                 |
| 500              | Internal Server Error                             |
| 502              | Bad Gateway                                       |
| 503              | Service Unavailable                               |
| 504              | Gateway Timeout                                   |

# PART 9: TOPIC COMPLETION CHECKLIST

- [ ] HTTP Methods
- [ ] GET
- [ ] POST
- [ ] PUT
- [ ] PATCH
- [ ] DELETE
- [ ] HEAD
- [ ] OPTIONS
- [ ] CONNECT
- [ ] TRACE
- [ ] Safe Methods
- [ ] Idempotent Methods
- [ ] Safe vs Idempotent
- [ ] GET vs POST
- [ ] PUT vs PATCH
- [ ] Request Headers
- [ ] Response Headers
- [ ] Content-Type
- [ ] Accept
- [ ] Authorization
- [ ] Cookie and Set-Cookie
- [ ] Cache-Control
- [ ] All Five Status Code Categories
- [ ] Important Status Codes
- [ ] Express Practical Example
- [ ] CMD Practical Tasks
- [ ] Interview Questions
