# Topic 13: Cookies & Sessions

## 1. Cookies kya hoti hain?

Cookie ek chhota sa data hota hai jo website browser mein store karti hai.

Jab user kisi website ko visit karta hai, toh server browser ko cookie bhej sakta hai. Browser us cookie ko store kar leta hai aur suitable future requests ke saath server ko wapas bhejta hai.

**Example:**

Maan lo tum Amazon par login karte ho.

Login karne ke baad website tumhe baar-baar login karne ke liye nahi bolti.

Browser mein cookie store ho sakti hai, jiske through website tumhari login state identify kar sakti hai.

### Cookie mein kya store ho sakta hai?

- Session identifier
- User preferences
- Language preference
- Theme preference
- Tracking identifier

**Important:** Sensitive information jaise password ko cookie mein directly store nahi karna chahiye.

---

## 2. Cookies ki zarurat kyun hoti hai?

HTTP ek stateless protocol hai.

Stateless ka matlab hai ki HTTP apne aap previous request ki information yaad nahi rakhta.

Example:

```text
Request 1: User Login
Request 2: User Profile
Request 3: User Orders
```

HTTP apne aap nahi jaanta ki teeno requests ek hi logged-in user ki hain.

Is problem ko solve karne ke liye Cookies aur Sessions jaise mechanisms use kiye jaate hain.

Cookies browser ko kuch information store karne aur future requests mein bhejne ki facility deti hain.

---

## 3. Cookie kaise kaam karti hai?

Cookie ka basic flow:

```text
        Browser
           |
           | 1. Login Request
           v
        Server
           |
           | 2. Login Successful
           | Set-Cookie Header
           v
        Browser
           |
           | 3. Cookie Store
           |
           | 4. Next Request
           | Cookie Header
           v
        Server
           |
           | 5. Cookie Verify
           v
        Response
```

### Step-by-step

1. User login request bhejta hai.
2. Server credentials verify karta hai.
3. Login successful hone par server `Set-Cookie` header bhej sakta hai.
4. Browser cookie store karta hai.
5. Future matching requests ke saath browser cookie bhejta hai.
6. Server cookie ko verify karke user ki identity ya session identify karta hai.

---

## 4. Set-Cookie aur Cookie Headers

Cookies HTTP headers ke through transfer hoti hain.

### A. Set-Cookie Header

Server browser ko cookie set karne ke liye ye header bhejta hai.

Example:

```http
HTTP/1.1 200 OK
Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Lax
```

Meaning:

- `sessionId=abc123` = Cookie ka name aur value.
- `HttpOnly` = JavaScript se cookie access nahi ki ja sakti.
- `Secure` = Cookie HTTPS connection par hi bheji jayegi.
- `SameSite=Lax` = Cross-site requests mein cookie bhejne par restrictions apply hoti hain.

### B. Cookie Header

Browser future request ke saath cookie bhejta hai.

```http
GET /profile
Cookie: sessionId=abc123
```

Server is cookie ko read karke corresponding session identify kar sakta hai.

**Remember:**

- `Set-Cookie` server se browser ko jaata hai.
- `Cookie` browser se server ko jaata hai.

---

## 5. Cookie ke Important Attributes

### 1. HttpOnly

Is attribute ka use cookie ko JavaScript ke through access hone se rokne ke liye hota hai.

Example:

```http
Set-Cookie: sessionId=abc123; HttpOnly
```

Agar HttpOnly cookie hai, toh browser JavaScript ke `document.cookie` se us cookie ko read nahi karne deta.

Ye XSS attack ke through cookie theft ka risk reduce karta hai.

### 2. Secure

Secure attribute ka matlab hai cookie sirf secure HTTPS connection par send hogi.

Example:

```http
Set-Cookie: sessionId=abc123; Secure
```

Production authentication cookies ke liye generally Secure use karna chahiye.

### 3. SameSite

SameSite attribute control karta hai ki cross-site requests ke saath cookie kab send hogi.

Iske common values hain:

| Value  | Meaning                                                                 |
| ------ | ----------------------------------------------------------------------- |
| Strict | Cross-site requests mein cookie generally send nahi hoti                |
| Lax    | Kuch top-level cross-site navigations mein cookie send ho sakti hai     |
| None   | Cross-site requests mein cookie allow hoti hai; Secure bhi required hai |

Example:

```http
Set-Cookie: sessionId=abc123; SameSite=Lax
```

SameSite CSRF risk reduce karne mein help karta hai, lekin har situation mein complete CSRF protection nahi hai.

### 4. Expires

Cookie ki expiry date set karta hai.

Example:

```http
Set-Cookie: theme=dark; Expires=Wed, 11 Nov 2026 10:00:00 GMT
```

### 5. Max-Age

Cookie kitne seconds tak valid rahegi, ye specify karta hai.

Example:

```http
Set-Cookie: theme=dark; Max-Age=3600
```

Cookie approximately 3600 seconds (1 hour) tak valid rahegi.

### 6. Domain

Specify karta hai ki cookie kin domains ke liye available hogi.

Example:

```http
Set-Cookie: theme=dark; Domain=example.com
```

### 7. Path

Specify karta hai ki cookie kin URL paths par send ho sakti hai.

Example:

```http
Set-Cookie: theme=dark; Path=/admin
```

Cookie `/admin` path aur uske applicable subpaths par send hogi.

---

## 6. Types of Cookies

### A. Session Cookies

Ye cookies generally browser session tak rehti hain.

Inmein usually persistent expiry set nahi hoti.

Browser session end hone par ye delete ho sakti hain.

Example:

```http
Set-Cookie: sessionId=abc123; HttpOnly
```

### B. Persistent Cookies

In cookies ki expiry ya Max-Age set hoti hai.

Ye browser close hone ke baad bhi expiry tak store reh sakti hain.

Example:

```http
Set-Cookie: theme=dark; Max-Age=86400
```

### Comparison

| Session Cookie                    | Persistent Cookie         |
| --------------------------------- | ------------------------- |
| Usually browser session tak       | Expiry tak store          |
| Persistent expiry set nahi hoti   | Expires/Max-Age hota hai  |
| Temporary preferences/session use | Remember preferences etc. |

**Note:** Session cookie aur server-side Session alag concepts hain. Session cookie mein aksar sirf session ID hoti hai.

---

## 7. Session kya hota hai?

Session server-side stored information hoti hai jo kisi user ki activity ya login state ko multiple requests ke beech maintain karne mein help karti hai.

Example:

Maan lo user login karta hai.

Server:

1. User ka login verify karta hai.
2. Ek unique session ID generate karta hai.
3. Session data server-side store karta hai.
4. Session ID browser ko cookie mein bhejta hai.

Browser future requests mein session ID send karta hai.

Server us ID se session data find kar leta hai.

### Example

Server-side session data:

```javascript
{
  sessionId: "abc123",
  userId: "101",
  role: "admin"
}
```

Browser cookie:

```http
Cookie: sessionId=abc123
```

Browser ke paas session ID hai, jabki actual session information server-side store hai.

---

## 8. Session Working Flow

```text
       Browser
          |
          | 1. Email + Password
          v
        Server
          |
          | 2. Verify Credentials
          v
       Database
          |
          | 3. User Found
          v
        Server
          |
          | 4. Create Session
          v
    Session Store
          |
          | 5. Session ID
          v
       Browser
          |
          | 6. Store Session ID
          | in Cookie
          |
          | 7. Future Request
          | with Cookie
          v
        Server
          |
          | 8. Find Session
          v
    Session Store
          |
          v
     User Identified
```

---

## 9. Cookie vs Session

Ye dono related hain, lekin same nahi hain.

| Cookie                                   | Session                                      |
| ---------------------------------------- | -------------------------------------------- |
| Browser mein store hoti hai              | Generally server-side store hota hai         |
| Client-side storage mechanism            | Server-side state management                 |
| Data ya identifier store kar sakti hai   | User-related session data maintain karta hai |
| Expiry attributes ho sakte hain          | Server-side expiry/timeout ho sakta hai      |
| Browser requests ke saath bhej sakta hai | Session ID ke through identify hota hai      |

### Simple Example

**Cookie:**

```text
sessionId = abc123
```

**Server-side Session:**

```text
abc123 → userId: 101
```

Matlab cookie mein session ID hai aur server us ID se user ki session information find karta hai.

---

## 10. Session Storage Kahan Hoti Hai?

Server-side sessions ko store karne ke multiple options hain.

### A. In-Memory Storage

Session server ke RAM mein store hota hai.

Advantages:

- Fast access.
- Development ke liye simple.

Disadvantages:

- Server restart hone par sessions lose ho sakte hain.
- Multiple server instances ke beech sessions automatically share nahi hote.

### B. Database Storage

Sessions ko database mein store kar sakte hain.

Advantages:

- Persistent storage possible.
- Centralized session data.

Disadvantages:

- Database queries ka overhead.
- Session expiry aur cleanup manage karna padta hai.

### C. Redis

Redis ek in-memory data store hai jise distributed session storage ke liye commonly use kiya ja sakta hai.

Advantages:

- Fast access.
- Multiple application servers sessions share kar sakte hain.
- Expiry support.

Example:

```text
Server 1 ──┐
           |
Server 2 ──┼── Redis Session Store
           |
Server 3 ──┘
```

---

## 11. Session Expiration and Logout

Session ko hamesha ke liye active nahi rakhna chahiye.

Session expire hone ke common reasons:

1. Fixed expiration time complete hona.
2. Inactivity timeout.
3. User logout karna.
4. Admin session revoke karna.
5. Security event ke baad session invalidate karna.

### Logout Flow

1. User logout button click karta hai.
2. Frontend logout API call karta hai.
3. Backend session destroy karta hai.
4. Browser ki session cookie expire/delete karta hai.
5. User logged out ho jata hai.

Example:

```http
POST /api/logout
```

Backend server-side session ko invalidate karna important hai. Sirf browser cookie delete karna enough nahi ho sakta.

---

## 12. Express.js mein Cookie Set Karna

Express.js mein cookie set karne ke liye `res.cookie()` use kar sakte hain.

Example:

```javascript
const express = require("express");

const app = express();

app.get("/set-cookie", (req, res) => {
  res.cookie("theme", "dark", {
    httpOnly: true,
    secure: true,
    sameSite: "lax",
    maxAge: 60 * 60 * 1000,
  });

  res.json({
    message: "Cookie set successfully",
  });
});

app.listen(5000);
```

**Note:** `secure: true` ke saath local development mein HTTPS configuration zaroori ho sakti hai. Production mein HTTPS use karo.

---

## 13. Express.js mein Cookie Read Karna

Cookie read karne ke liye `cookie-parser` middleware use kar sakte hain.

Install:

```bash
npm install cookie-parser
```

Code:

```javascript
const express = require("express");
const cookieParser = require("cookie-parser");

const app = express();

app.use(cookieParser());

app.get("/read-cookie", (req, res) => {
  const theme = req.cookies.theme;

  res.json({
    theme: theme,
  });
});

app.listen(5000);
```

`cookie-parser` incoming Cookie header ko parse karke `req.cookies` provide karta hai.

**Important:** Cookie read kar lena authentication prove nahi karta. Authentication ke liye cookie ya session ki authenticity verify karni hoti hai.

---

## 14. Express.js mein Session Implement Karna

Express mein `express-session` package use kar sakte hain.

Install:

```bash
npm install express-session
```

Basic example:

```javascript
const express = require("express");
const session = require("express-session");

const app = express();

app.use(express.json());

app.use(
  session({
    secret: process.env.SESSION_SECRET,
    resave: false,
    saveUninitialized: false,
    cookie: {
      httpOnly: true,
      secure: process.env.NODE_ENV === "production",
      sameSite: "lax",
      maxAge: 60 * 60 * 1000,
    },
  }),
);

app.post("/login", (req, res) => {
  // Demo only: production mein database se
  // credentials verify karne honge.

  req.session.userId = "101";

  res.json({
    message: "Login successful",
  });
});

app.get("/profile", (req, res) => {
  if (!req.session.userId) {
    return res.status(401).json({
      message: "Please login first",
    });
  }

  res.json({
    userId: req.session.userId,
  });
});

app.post("/logout", (req, res, next) => {
  req.session.destroy((err) => {
    if (err) {
      return next(err);
    }

    res.clearCookie("connect.sid");

    res.json({
      message: "Logout successful",
    });
  });
});

app.listen(5000);
```

### Important Production Notes

- `SESSION_SECRET` ko environment variable mein rakho.
- Default MemoryStore production ke liye suitable nahi hai.
- Production mein Redis ya suitable persistent session store use karo.
- Reverse proxy ke peeche HTTPS use karte waqt Express ki `trust proxy` configuration sahi rakho.
- Cookie ka `path` aur `domain` clear karte waqt original cookie configuration se match karna chahiye.
- Login ke baad session ID regenerate karna session fixation risk ko reduce karta hai.
- Real application mein login credentials verify karna compulsory hai.

---

## 15. Cookie Security

Cookies mein authentication-related information ho sakti hai, isliye security important hai.

### 1. HttpOnly

JavaScript se authentication cookie access hone ka risk reduce karta hai.

### 2. Secure

Cookie ko HTTPS par hi send karne deta hai.

### 3. SameSite

Cross-site request situations mein cookie sending control karta hai aur CSRF risk reduce kar sakta hai.

### 4. Short Expiry

Authentication cookies ko unnecessary long time tak valid mat rakho.

### 5. Sensitive Data Store Mat Karo

Password aur sensitive personal information ko cookie mein directly store mat karo.

### 6. CSRF Protection

CSRF ka full form Cross-Site Request Forgery hai.

Is attack mein attacker user ke browser se kisi website par unwanted request karwane ki koshish karta hai.

Agar browser automatically authentication cookies send karta hai, toh CSRF ka risk ho sakta hai.

Protection ke liye:

- SameSite cookies.
- CSRF tokens.
- Origin/Referer validation where appropriate.
- Sensitive state-changing requests ki proper protection.

---

## 16. XSS and Cookies

XSS ka full form Cross-Site Scripting hai.

Is attack mein attacker website ke page par malicious JavaScript execute karwane ki koshish karta hai.

Agar authentication cookie JavaScript se accessible hai, toh attacker us cookie ko steal karne ki koshish kar sakta hai.

Example:

```javascript
document.cookie;
```

HttpOnly cookie ko JavaScript se read nahi kiya ja sakta.

**Important:** HttpOnly XSS ko completely prevent nahi karta. Ye mainly JavaScript ke through cookie theft ko difficult banata hai. Input handling, output encoding aur Content Security Policy jaise protections bhi important hain.

---

## 17. Cookie-Based Authentication vs Token-Based Authentication

Authentication implement karne ke different approaches hote hain.

### Cookie-Based Session Authentication

```text
Browser
   |
   | Session Cookie
   v
Server
   |
   | Session ID Verify
   v
Session Store
```

Server-side session store mein login state maintain hoti hai.

### Token-Based Authentication

```text
Browser
   |
   | Authentication Token
   v
Server
   |
   | Token Verify
   v
User Identified
```

Token mein claims ho sakte hain, jinhe server verify karta hai.

### Comparison

| Cookie + Session                                       | Token-Based                                                                 |
| ------------------------------------------------------ | --------------------------------------------------------------------------- |
| Session state server-side hoti hai                     | Token claims client ke paas ho sakte hain                                   |
| Session store required                                 | Token verification required                                                 |
| Session revoke karna comparatively direct ho sakta hai | Stateless tokens ko revoke karne ke liye additional mechanism lag sakta hai |
| Browser cookie automatically send kar sakta hai        | Token header ya cookie mein bheja ja sakta hai                              |

**Important:** Cookie aur token ek doosre ke alternatives nahi hain. JWT token bhi cookie mein store kiya ja sakta hai.

---

## 18. MERN Application mein Cookies and Sessions

MERN stack:

- MongoDB = Database
- Express.js = Backend framework
- React.js = Frontend
- Node.js = Runtime

Example login flow:

```text
React Login Form
       |
       | Email + Password
       v
Express Login API
       |
       v
MongoDB User Verification
       |
       v
Create Server Session
       |
       v
Set HttpOnly Cookie
       |
       v
Browser Stores Cookie
       |
       v
React Calls Profile API
       |
       v
Browser Sends Cookie
       |
       v
Express Verifies Session
       |
       v
Profile Response
```

### Cross-Origin Important Point

Agar React aur Express alag origins par hain, toh cookie-based authentication ke liye:

- Frontend request mein `credentials: "include"` use karna pad sakta hai.
- Backend CORS mein exact allowed origin specify karna hota hai.
- Backend mein `credentials: true` enable karna hota hai.
- Cookie ke `SameSite` aur `Secure` attributes deployment ke according set karne hote hain.
- Cross-site cookie requests mein generally `SameSite=None; Secure` required hota hai.

React example:

```javascript
fetch("https://api.example.com/profile", {
  method: "GET",
  credentials: "include",
});
```

Express CORS example:

```javascript
const cors = require("cors");

app.use(
  cors({
    origin: "https://frontend.example.com",
    credentials: true,
  }),
);
```

Wildcard origin `*` ko credentials ke saath use nahi kar sakte.

---

## 19. Common Mistakes

1. Password ko cookie mein store karna.
2. Production mein Secure attribute use na karna.
3. Authentication cookie ko unnecessary JavaScript-accessible rakhna.
4. Session expire hone ke baad bhi usse valid rakhna.
5. Logout par server-side session destroy na karna.
6. Production mein default MemoryStore use karna.
7. Cookie-based authentication mein CSRF protection ignore karna.
8. Cross-origin requests mein CORS credentials configuration miss karna.
9. Session secret ko code mein hardcode karna.
10. Cookie aur Session ko same concept samajhna.

---

## 20. Interview Questions and Answers

### Q1. Cookie kya hoti hai?

Cookie ek small piece of data hai jo browser store karta hai aur matching future HTTP requests ke saath server ko bhej sakta hai.

### Q2. HTTP Stateless kyun hai?

HTTP protocol apne aap previous requests ki user state remember nahi karta.

### Q3. Session kya hota hai?

Session server-side information hoti hai jo user ki login state aur related data maintain karti hai.

### Q4. Cookie aur Session mein kya difference hai?

Cookie browser mein store hoti hai, jabki server-side session data server ya session store mein maintain hota hai.

### Q5. HttpOnly kya hai?

Cookie attribute jo JavaScript se cookie access hone ko prevent karta hai.

### Q6. Secure attribute kya karta hai?

Cookie ko HTTPS connection par hi send karne deta hai.

### Q7. SameSite kya hai?

Cookie attribute jo cross-site requests ke saath cookie bhejne par control lagata hai.

### Q8. Session ID kya hai?

Ek unique identifier jiske through server corresponding session information find karta hai.

### Q9. Redis ka session management mein kya use hai?

Redis multiple application servers ke beech session data share karne ke liye fast centralized store provide kar sakta hai.

### Q10. CSRF kya hai?

Aisa attack jisme attacker logged-in user ke browser se unwanted request karwane ki koshish karta hai.

### Q11. XSS kya hai?

Aisa attack jisme malicious script website ke context mein execute hoti hai.

### Q12. Logout ke time kya karna chahiye?

Server-side session invalidate/destroy karna chahiye aur browser ki session cookie clear karni chahiye.

---

## 21. Practical Tasks

### Task 1: Cookie Create Karo

Express.js mein `/set-cookie` endpoint banao jo `theme=dark` cookie set kare.

### Task 2: Cookie Read Karo

`cookie-parser` use karke `/read-cookie` endpoint banao.

### Task 3: Session Create Karo

`express-session` use karke login endpoint banao jo session mein user ID store kare.

### Task 4: Protected Route Banao

`/profile` endpoint ko session authentication se protect karo.

### Task 5: Logout Implement Karo

Logout endpoint banao jo server-side session destroy kare aur cookie clear kare.

---

## 22. Quick Revision

- Cookie = Browser mein stored small data.
- HTTP = Stateless protocol.
- Set-Cookie = Server se browser ko cookie set karne ka header.
- Cookie = Browser se server ko bheja jane wala header.
- HttpOnly = JavaScript cookie access ko block karta hai.
- Secure = HTTPS par cookie send hoti hai.
- SameSite = Cross-site cookie behavior control karta hai.
- Session = Server-side user state.
- Session ID = Session identify karne wala unique identifier.
- Redis = Distributed session storage ke liye useful.
- CSRF = Cross-Site Request Forgery.
- XSS = Cross-Site Scripting.
- Logout = Session invalidate + cookie clear.
- Cookie aur Session = Related but different concepts.

---

## 23. Topic Completion Checklist

- [ ] Cookies samajh li.
- [ ] Cookies ki need samajh li.
- [ ] Set-Cookie aur Cookie headers samajh liye.
- [ ] Cookie attributes samajh liye.
- [ ] Session Cookies aur Persistent Cookies samajh li.
- [ ] Sessions samajh liye.
- [ ] Session storage options samajh liye.
- [ ] Session expiration aur logout samajh liya.
- [ ] Express.js mein cookies implement karna seekh liya.
- [ ] Express.js mein sessions implement karna seekh liya.
- [ ] Cookie security samajh li.
- [ ] CSRF aur XSS samajh liye.
- [ ] MERN authentication flow samajh liya.

**Topic 13 Complete – Cookies & Sessions.**
