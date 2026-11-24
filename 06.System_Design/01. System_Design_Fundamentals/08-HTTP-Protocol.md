# Topic 08: HTTP Protocol

## 1. HTTP Kya Hai?

HTTP ka full form **Hypertext Transfer Protocol** hai.

HTTP ek application-layer protocol hai jo client aur server ke beech data communication enable karta hai.

Simple words mein:

**HTTP = Client aur Server ke beech communication ka rule.**

Example:

Jab tum browser mein YouTube open karte ho:

1. Browser server ko HTTP request bhejta hai.
2. Server request process karta hai.
3. Server HTTP response return karta hai.
4. Browser response ke according webpage display karta hai.

```text
       CLIENT
      (Browser)
          |
          | HTTP Request
          v
        SERVER
          |
          | HTTP Response
          v
       CLIENT
```

## 2. HTTP Ki Zaroorat Kyu Hoti Hai?

HTTP define karta hai ki client aur server ke beech communication kaise hoga.

HTTP ke through:

- Web pages request kiye ja sakte hain.
- API se data fetch kiya ja sakta hai.
- Server par data send kiya ja sakta hai.
- Files aur images receive ki ja sakti hain.
- Web applications communicate kar sakti hain.

Example:

React frontend Express backend se users ka data fetch kar sakta hai.

## 3. HTTP Kaise Work Karta Hai?

HTTP generally request-response model follow karta hai.

### Step 1: Client Request Bhejta Hai

Browser ya frontend server ko request bhejta hai.

Example:

```http
GET /api/users HTTP/1.1
Host: example.com
```

Meaning:

- `GET` = Data fetch karna.
- `/api/users` = Requested resource ka path.
- `HTTP/1.1` = HTTP version.
- `Host` = Target host ka domain name.

### Step 2: Server Request Receive Karta Hai

Server request ko receive aur interpret karta hai.

### Step 3: Server Processing Karta Hai

Server:

- Request validate karta hai.
- Business logic execute karta hai.
- Zaroorat hone par database access karta hai.

### Step 4: Server Response Bhejta Hai

Example:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "Users fetched successfully"
}
```

### Step 5: Client Response Process Karta Hai

Browser ya frontend response ko process karke user ko result show karta hai.

## 4. HTTP Request Kya Hoti Hai?

HTTP Request ek message hota hai jo client server ko bhejta hai.

HTTP request ke main parts:

1. Request Line
2. Headers
3. Blank Line
4. Optional Body

### Example

```http
POST /api/users HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

**Request Line:**

```text
POST /api/users HTTP/1.1
```

Isme:

- Method = POST
- Path = /api/users
- Version = HTTP/1.1

**Headers:**

```text
Host: example.com
Content-Type: application/json
```

Headers request ke baare mein additional information dete hain.

**Body:**

```json
{
  "name": "Rahul",
  "email": "rahul@example.com"
}
```

Body mein server ko bheja ja raha data hai.

Note: GET request mein generally body use nahi ki jaati. Request body optional hoti hai aur method/application ke according use hoti hai.

## 5. HTTP Response Kya Hota Hai?

HTTP Response wo message hai jo server client ko return karta hai.

HTTP response ke main parts:

1. Status Line
2. Headers
3. Blank Line
4. Optional Body

### Example

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "message": "User created successfully",
  "id": 101
}
```

**Status Line:**

```text
HTTP/1.1 201 Created
```

Isme:

- HTTP Version = HTTP/1.1
- Status Code = 201
- Reason Phrase = Created

**Headers:**

```text
Content-Type: application/json
```

**Body:**

```json
{
  "message": "User created successfully",
  "id": 101
}
```

## 6. HTTP Methods Kya Hote Hain?

HTTP methods batate hain ki client requested resource par kya action perform karna chahta hai.

Common methods:

| Method  | Purpose                                                |
| ------- | ------------------------------------------------------ |
| GET     | Data retrieve karna                                    |
| POST    | Data submit karna ya resource create karna             |
| PUT     | Resource ko replace/update karna                       |
| PATCH   | Resource ko partially update karna                     |
| DELETE  | Resource delete karna                                  |
| HEAD    | GET jaisi response headers request karna, body ke bina |
| OPTIONS | Communication options discover karna                   |

Example:

```text
GET    /api/users
POST   /api/users
PUT    /api/users/10
PATCH  /api/users/10
DELETE /api/users/10
```

HTTP methods ko Topic 10 mein detail se padhenge.

## 7. HTTP Headers Kya Hote Hain?

Headers request aur response ke saath additional metadata provide karte hain.

### Common Request Headers

| Header        | Purpose                                          |
| ------------- | ------------------------------------------------ |
| Host          | Target host identify karta hai                   |
| Accept        | Client ko kaun-sa response format acceptable hai |
| Content-Type  | Request body ka media type                       |
| Authorization | Authentication credentials/token                 |
| User-Agent    | Client software information                      |
| Cookie        | Browser ke stored cookies send karta hai         |

### Common Response Headers

| Header                      | Purpose                                   |
| --------------------------- | ----------------------------------------- |
| Content-Type                | Response body ka media type               |
| Content-Length              | Body length                               |
| Cache-Control               | Caching rules                             |
| Set-Cookie                  | Client ke liye cookie set karna           |
| Location                    | Redirect ya newly created resource ka URL |
| Access-Control-Allow-Origin | CORS policy mein allowed origin           |

## 8. HTTP Status Codes Kya Hote Hain?

Status codes server ke response ka result indicate karte hain.

Inki five main categories hoti hain.

### 1xx – Informational

Request receive hui aur processing continue ho sakti hai.

Example:

- 100 Continue

### 2xx – Success

Request successfully receive, understand aur process hui.

Examples:

- 200 OK
- 201 Created
- 204 No Content

### 3xx – Redirection

Further action ya redirection required ho sakta hai.

Examples:

- 301 Moved Permanently
- 302 Found
- 304 Not Modified

### 4xx – Client Error

Request mein client-side problem ho sakti hai.

Examples:

- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 429 Too Many Requests

### 5xx – Server Error

Server request process karte waqt fail hua.

Examples:

- 500 Internal Server Error
- 502 Bad Gateway
- 503 Service Unavailable
- 504 Gateway Timeout

Detailed status codes Topic 10 mein cover honge.

## 9. HTTP Versions

HTTP ke different versions hain.

### HTTP/0.9

- Early version.
- Basic GET request support.
- Very limited functionality.

### HTTP/1.0

- Headers introduce hue.
- Different content types support hue.
- Generally each request ke liye separate connection use hota tha.

### HTTP/1.1

- Persistent connections support.
- Better caching.
- Host header required.
- Chunked transfer encoding.

### HTTP/2

- Binary framing.
- Multiplexing.
- Header compression using HPACK.
- Ek connection par multiple streams support.

### HTTP/3

- QUIC transport protocol use karta hai.
- QUIC UDP par operate karta hai.
- Connection setup aur stream handling mein improvements.

### HTTP Versions Comparison

| Feature            | HTTP/1.1                       | HTTP/2 | HTTP/3        |
| ------------------ | ------------------------------ | ------ | ------------- |
| Transport          | TCP                            | TCP    | QUIC over UDP |
| Multiplexing       | Same connection par limitation | Yes    | Yes           |
| Header Compression | No standard header compression | HPACK  | QPACK         |
| Binary Framing     | No                             | Yes    | Yes           |
| Connection         | TCP                            | TCP    | QUIC          |

Important: HTTP/3 UDP use karta hai, lekin iska matlab ye nahi ki HTTP/3 unreliable application protocol hai. QUIC reliability aur congestion control provide karta hai.

## 10. HTTP Stateless Kyu Kaha Jata Hai?

HTTP ko stateless protocol kaha jata hai.

Iska meaning hai ki HTTP protocol mein har request independently understood hoti hai. Protocol khud automatically previous request ki application state remember nahi karta.

Example:

User login karta hai aur next request bhejta hai.

Agar application chahti hai ki server user ko identify kare, to cookies, sessions ya tokens use kiye ja sakte hain.

**Important:** HTTP stateless hone ke bawajood web applications user sessions maintain kar sakti hain.

## 11. HTTP Persistent Connection Kya Hai?

HTTP/1.1 mein persistent connections commonly default behavior hain.

Iska meaning hai ki ek TCP connection ko multiple HTTP requests/responses ke liye reuse kiya ja sakta hai.

Benefit:

- Repeated TCP connection setup avoid ho sakta hai.
- Network overhead reduce hota hai.
- Performance improve ho sakti hai.

HTTP/2 aur HTTP/3 bhi connections ko efficiently reuse karte hain aur multiple streams support karte hain.

## 12. HTTP vs HTTPS

HTTP aur HTTPS dono web communication protocols hain.

HTTPS ka meaning hai HTTP over TLS.

| HTTP                                    | HTTPS                                                |
| --------------------------------------- | ---------------------------------------------------- |
| TLS encryption nahi hoti                | TLS encryption use hoti hai                          |
| Default port 80                         | Default port 443                                     |
| Data confidentiality provide nahi karta | Data confidentiality aur integrity provide karta hai |
| Sensitive data ke liye unsafe           | Secure communication ke liye designed                |

HTTPS ke baare mein Topic 09 mein detail se padhenge.

## 13. HTTP vs WebSocket

HTTP aur WebSocket communication ke different models support karte hain.

### HTTP

Commonly request-response communication use karta hai.

Example:

- User profile fetch karna.
- Product details load karna.
- Login request bhejna.

### WebSocket

WebSocket client aur server ke beech persistent, two-way communication channel provide karta hai.

Example:

- Live chat.
- Real-time notifications.
- Live updates.

| HTTP                          | WebSocket                 |
| ----------------------------- | ------------------------- |
| Request-response model        | Full-duplex communication |
| Commonly independent requests | Persistent connection     |
| Traditional APIs              | Real-time communication   |

## 14. MERN Stack Mein HTTP Ka Role

MERN application mein React frontend aur Express backend HTTP ke through communicate karte hain.

### Architecture

```text
       USER
         |
         v
    REACT FRONTEND
         |
         | HTTP Request
         v
    EXPRESS SERVER
         |
         v
      NODE.JS
         |
         v
      MONGODB
         |
         v
    HTTP RESPONSE
         |
         v
    REACT FRONTEND
```

### React Example

```javascript
async function getUsers() {
  const response = await fetch("http://localhost:5000/api/users");

  const data = await response.json();

  console.log(data);
}

getUsers();
```

### Express Example

```javascript
const express = require("express");

const app = express();

app.get("/api/users", (req, res) => {
  res.status(200).json([{ name: "Rahul" }, { name: "Aman" }]);
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

Yahan:

- React HTTP request bhej raha hai.
- Express request receive kar raha hai.
- Express JSON response return kar raha hai.

## 15. Common HTTP Errors

### 400 Bad Request

Request invalid ya incorrectly formatted hai.

### 401 Unauthorized

Request ke liye valid authentication credentials missing ya invalid hain.

### 403 Forbidden

Server request samajh gaya, lekin access allow nahi kar raha.

### 404 Not Found

Requested resource nahi mila.

### 500 Internal Server Error

Server par unexpected error hua.

### 503 Service Unavailable

Server currently request handle karne ke liye available nahi hai.

## 16. Common Mistakes

1. HTTP ko programming language samajhna.
2. Request aur response mein difference na samajhna.
3. Headers aur body ko same samajhna.
4. GET aur POST ka purpose confuse karna.
5. 401 aur 403 ko same samajhna.
6. HTTP ko automatically secure samajhna.
7. HTTP stateless hone ka matlab session impossible samajhna.
8. HTTP/3 ko TCP-based samajhna.
9. Har HTTP response mein body zaroori samajhna.

## 17. Interview Questions and Answers

**Q1. What is HTTP?**

Ans: HTTP is an application-layer protocol used for communication between clients and servers.

**Q2. What is an HTTP Request?**

Ans: It is a message sent by a client to a server to request a resource or perform an operation.

**Q3. What is an HTTP Response?**

Ans: It is a message returned by a server after processing an HTTP request.

**Q4. What are HTTP Headers?**

Ans: Headers carry metadata about an HTTP request or response.

**Q5. What are HTTP Methods?**

Ans: Methods define the intended action to be performed on a resource, such as GET, POST, PUT, PATCH and DELETE.

**Q6. What are HTTP Status Codes?**

Ans: They indicate the result of processing an HTTP request.

**Q7. Why is HTTP called stateless?**

Ans: Because the protocol does not automatically maintain application state between independent requests.

**Q8. What is a persistent connection?**

Ans: It allows multiple HTTP exchanges to reuse the same underlying connection.

**Q9. What is the difference between HTTP/2 and HTTP/3?**

Ans: HTTP/2 uses TCP, whereas HTTP/3 uses QUIC over UDP.

**Q10. What is the difference between HTTP and WebSocket?**

Ans: HTTP commonly uses request-response communication, whereas WebSocket provides persistent full-duplex communication.

## 18. Practical Tasks

### Task 1: Browser Network Tab

1. Chrome open karo.
2. Kisi website ko open karo.
3. Press `F12`.
4. Network tab select karo.
5. Page refresh karo.
6. Kisi request par click karo.

Observe:

- Request URL.
- Request Method.
- Status Code.
- Request Headers.
- Response Headers.
- Response Body.

### Task 2: Test HTTP Request

CMD mein:

```cmd
curl -i https://example.com
```

Observe:

- HTTP status.
- Response headers.
- Response body.

### Task 3: Test GET Request

```cmd
curl -i https://jsonplaceholder.typicode.com/posts/1
```

Observe returned JSON data.

### Task 4: Test POST Request

```cmd
curl -i -X POST https://jsonplaceholder.typicode.com/posts -H "Content-Type: application/json" -d "{\"title\":\"Hello\",\"body\":\"Testing HTTP\",\"userId\":1}"
```

Observe response status and returned data.

Note: JSONPlaceholder ek testing API hai. POST request ka response simulated ho sakta hai; iska matlab permanent database storage zaroori nahi.

## 19. Quick Revision

- HTTP = Hypertext Transfer Protocol.
- HTTP = Application Layer Protocol.
- Request = Client to Server.
- Response = Server to Client.
- Request Line = Method + Target + HTTP Version.
- Headers = Additional metadata.
- Body = Optional message content.
- GET = Retrieve.
- POST = Submit/Create.
- PUT = Replace.
- PATCH = Partial update.
- DELETE = Delete.
- 2xx = Success.
- 3xx = Redirection.
- 4xx = Client Error.
- 5xx = Server Error.
- HTTP Stateless = Protocol automatically previous request state maintain nahi karta.
- HTTP/2 = Multiplexing over TCP.
- HTTP/3 = QUIC over UDP.
- HTTPS = HTTP over TLS.

## 20. Topic Completion Checklist

- [ ] HTTP Introduction
- [ ] HTTP Working
- [ ] HTTP Request
- [ ] HTTP Response
- [ ] HTTP Methods
- [ ] HTTP Headers
- [ ] HTTP Status Codes
- [ ] HTTP Versions
- [ ] Stateless Protocol
- [ ] Persistent Connections
- [ ] HTTP vs HTTPS
- [ ] HTTP vs WebSocket
- [ ] MERN Connection
- [ ] HTTP Errors
- [ ] Practical Browser/CMD Tasks
