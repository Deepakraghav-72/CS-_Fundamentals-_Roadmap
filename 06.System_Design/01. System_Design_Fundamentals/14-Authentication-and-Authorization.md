# Topic 14: Authentication & Authorization

## 1. Authentication kya hota hai?

Authentication ka matlab hai kisi user ki identity verify karna.

Simple language mein:

**Authentication = Tum kaun ho?**

Example:

Maan lo tum kisi website par login karte ho.

Tum enter karte ho:

- Email
- Password

Server database mein stored user information ke saath credentials verify karta hai.

Agar credentials correct hain, toh server confirm karta hai ki tum wahi user ho jiska account hai.

Is process ko Authentication kehte hain.

### Real-life Examples

- Gmail login
- Instagram login
- Banking application login
- Amazon account login

In sab mein Authentication use hota hai.

---

## 2. Authorization kya hota hai?

Authorization ka matlab hai authenticated user ko kisi resource ya action ki permission dena ya deny karna.

Simple language mein:

**Authorization = Tum kya kar sakte ho?**

Example:

Maan lo ek website par do users hain:

1. Admin
2. Normal User

Admin:

- Users dekh sakta hai.
- Users delete kar sakta hai.
- Products add kar sakta hai.
- Products update kar sakta hai.

Normal User:

- Products dekh sakta hai.
- Products purchase kar sakta hai.
- Apna profile update kar sakta hai.

Admin aur normal user ki permissions different hain.

Ye Authorization hai.

---

## 3. Authentication vs Authorization

| Authentication            | Authorization                                             |
| ------------------------- | --------------------------------------------------------- |
| Identity verify karta hai | Permissions check karta hai                               |
| User kaun hai?            | User kya kar sakta hai?                                   |
| Login se related          | Access control se related                                 |
| Generally pehle hota hai  | Identity establish hone ke baad permission check hoti hai |
| Example: Password verify  | Example: Admin permission check                           |

### Easy Example

Maan lo tum ek office mein jaate ho.

- Security guard tumhara ID card check karta hai = Authentication.
- Guard check karta hai ki tumhe server room mein jaane ki permission hai ya nahi = Authorization.

**Important:** Authentication successful hone ka matlab ye nahi ki user ko har resource access karne ki permission mil gayi.

---

## 4. Authentication ke Types

Authentication ke multiple methods hote hain.

### A. Password-Based Authentication

User email/username aur password ke through login karta hai.

Example:

```text
Email: user@example.com
Password: ********
```

Server password verify karta hai.

### B. OTP-Based Authentication

OTP ka full form One-Time Password hai.

User ke registered phone number ya email par OTP send kiya jata hai.

Example:

```text
Enter your OTP: 123456
```

Correct aur valid OTP enter karne par identity verify hoti hai.

OTP ko short expiry aur attempt limits ke saath implement karna chahiye.

### C. Multi-Factor Authentication (MFA)

MFA mein identity verify karne ke liye ek se zyada independent authentication factors use hote hain.

Common factors:

| Factor             | Example                       |
| ------------------ | ----------------------------- |
| Something you know | Password, PIN                 |
| Something you have | Phone, security key           |
| Something you are  | Fingerprint, face recognition |

Example:

1. User password enter karta hai.
2. User authenticator app ka code enter karta hai.

Ye MFA hai.

**Note:** Two-Factor Authentication (2FA), MFA ka ek specific form hai jisme exactly do factors use hote hain.

### D. Biometric Authentication

Biometric authentication mein physical ya behavioral characteristics ke through identity verify hoti hai.

Examples:

- Fingerprint
- Face Recognition
- Iris Recognition

### E. Token-Based Authentication

Login successful hone par server user ko token issue kar sakta hai.

Client future requests mein token bhejta hai.

Server token verify karke user identify karta hai.

Example:

```http
Authorization: Bearer <access_token>
```

JWT iska ek popular example hai.

---

## 5. Authentication ka Complete Flow

Ek normal email-password login flow:

```text
        User
         |
         | 1. Email + Password
         v
    React Frontend
         |
         | 2. Login API Request
         v
    Express Backend
         |
         | 3. Find User
         v
      MongoDB
         |
         | 4. User Data
         v
    Express Backend
         |
         | 5. Verify Password
         v
   Password Hash Check
         |
         | 6. Credentials Correct
         v
   Create Session / Token
         |
         | 7. Send Login Response
         v
    React Frontend
```

Agar credentials incorrect hain, toh server login reject karega.

---

## 6. Signup and Login

### A. Signup

Signup ka matlab hai application mein naya account create karna.

Signup flow:

1. User name, email aur password enter karta hai.
2. Frontend backend ko request bhejta hai.
3. Backend input validate karta hai.
4. Check karta hai ki email already registered toh nahi.
5. Password hash karta hai.
6. User record database mein save karta hai.
7. Success response return karta hai.

Example request:

```http
POST /api/v1/auth/register
Content-Type: application/json
```

```json
{
  "name": "Rahul",
  "email": "rahul@example.com",
  "password": "MyPassword123"
}
```

### B. Login

Login ka matlab existing account mein authenticate hona.

Login flow:

1. User email aur password enter karta hai.
2. Backend user ko database mein find karta hai.
3. Password hash verify karta hai.
4. Credentials correct hone par session ya token create karta hai.
5. User ko successful response deta hai.

Example:

```http
POST /api/v1/auth/login
```

```json
{
  "email": "rahul@example.com",
  "password": "MyPassword123"
}
```

---

## 7. Password Hashing

Password Hashing ka matlab password ko one-way cryptographic hash mein convert karna hai.

**Password ko database mein plain text format mein kabhi store nahi karna chahiye.**

Wrong database example:

```json
{
  "email": "rahul@example.com",
  "password": "MyPassword123"
}
```

Correct approach:

```json
{
  "email": "rahul@example.com",
  "passwordHash": "$2b$12$exampleHashValue..."
}
```

### Hashing vs Encryption

| Hashing                                   | Encryption                            |
| ----------------------------------------- | ------------------------------------- |
| One-way process                           | Reversible process with key           |
| Original value normally recover nahi hoti | Correct key se decrypt kar sakte hain |
| Password storage ke liye suitable         | Data confidentiality ke liye suitable |

### Password Hashing Algorithms

Common password hashing algorithms:

- Argon2id
- bcrypt
- scrypt

Passwords ko plain SHA-256 hash karke store karna suitable password-storage practice nahi hai. Password-specific algorithms use karo.

### bcrypt Example

Install:

```bash
npm install bcrypt
```

Password hash:

```javascript
const bcrypt = require("bcrypt");

const password = "MyPassword123";

const saltRounds = 12;

const hashedPassword = await bcrypt.hash(password, saltRounds);

console.log(hashedPassword);
```

Password verify:

```javascript
const isMatch = await bcrypt.compare("MyPassword123", hashedPassword);

console.log(isMatch);
```

Output:

```text
true
```

**Important:** Hashing ke liye password aur hash compare karne ke liye bcrypt ka `compare()` use karte hain. Password ko decrypt nahi karte.

---

## 8. JWT (JSON Web Token)

JWT ka full form JSON Web Token hai.

JWT ek compact token format hai jo claims ko securely represent karne ke liye use hota hai.

Authentication mein server JWT issue kar sakta hai aur future requests mein us token ko verify kar sakta hai.

Example:

```text
xxxxx.yyyyy.zzzzz
```

JWT ke three parts hote hain:

```text
Header.Payload.Signature
```

### A. Header

Header mein token type aur signing algorithm ki information hoti hai.

Example:

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

### B. Payload

Payload mein claims hoti hain, jaise user ID aur token expiry.

Example:

```json
{
  "userId": "101",
  "role": "user",
  "exp": 1790000000
}
```

### C. Signature

Signature token ki integrity verify karne mein help karti hai.

Signing secret ya private key ka use algorithm ke according hota hai.

### JWT Important Security Point

JWT ka payload generally Base64URL encoded hota hai, encrypted nahi.

Isliye sensitive data jaise password, bank details ya secret keys JWT payload mein store nahi karni chahiye.

---

## 9. JWT Authentication Flow

```text
        User
         |
         | Login Credentials
         v
    Express Backend
         |
         | Verify Credentials
         v
       MongoDB
         |
         | User Verified
         v
    Generate JWT
         |
         | Send Token
         v
    React Frontend
         |
         | Future API Request
         | Authorization Header
         v
    Express Backend
         |
         | Verify JWT Signature
         v
    Identify User
         |
         | Check Permission
         v
      API Response
```

### Step-by-step

1. User login request bhejta hai.
2. Backend credentials verify karta hai.
3. Backend JWT generate karta hai.
4. Client token receive karta hai.
5. Client protected API request bhejte waqt token send karta hai.
6. Backend token verify karta hai.
7. Backend user ki identity identify karta hai.
8. Authorization check ke baad resource return karta hai.

---

## 10. Access Token and Refresh Token

Token-based authentication mein commonly do types ke tokens use hote hain.

### A. Access Token

Access token protected resources access karne ke liye use hota hai.

Example:

```http
Authorization: Bearer access_token_here
```

Iski lifetime generally short rakhi jaati hai.

### B. Refresh Token

Refresh token ka use new access token obtain karne ke liye hota hai.

Jab access token expire ho jata hai, client refresh token ke through new access token request kar sakta hai.

### Flow

```text
User Login
    |
    v
Access Token + Refresh Token
    |
    v
Access Token Used
    |
    v
Access Token Expires
    |
    v
Refresh Token Sent
    |
    v
Refresh Token Verified
    |
    v
New Access Token
```

### Comparison

| Access Token                    | Refresh Token                                        |
| ------------------------------- | ---------------------------------------------------- |
| API access ke liye              | New access token lene ke liye                        |
| Short lifetime                  | Generally longer lifetime                            |
| Frequently sent to APIs         | Normally only refresh endpoint par                   |
| Expiry ke baad refresh required | Expiry/revocation ke baad re-authentication required |

**Security:** Refresh tokens ko carefully protect, rotate aur revoke karna chahiye. Logout par refresh token/session ko invalidate karne ka mechanism hona chahiye.

---

## 11. Authentication Storage: Cookies vs LocalStorage

Client-side token storage ke common options hain.

### A. LocalStorage

LocalStorage browser mein data store karta hai.

Example:

```javascript
localStorage.setItem("token", "abc123");
```

Read:

```javascript
const token = localStorage.getItem("token");
```

Problem:

Agar website mein XSS vulnerability hai, toh malicious JavaScript LocalStorage se token read kar sakti hai.

### B. HttpOnly Cookie

Server authentication cookie set karta hai.

Example:

```http
Set-Cookie: accessToken=abc123; HttpOnly; Secure; SameSite=Lax
```

JavaScript is cookie ko directly read nahi kar sakti.

Lekin cookie-based authentication mein CSRF protection aur correct SameSite/CORS configuration bhi important hai.

### Comparison

| LocalStorage                                  | HttpOnly Cookie                                         |
| --------------------------------------------- | ------------------------------------------------------- |
| JavaScript access kar sakti hai               | JavaScript access nahi kar sakti                        |
| XSS mein token theft ka risk                  | Cookie theft risk reduce hota hai                       |
| Request mein token manually bhejna hota hai   | Browser suitable requests mein automatically bhejta hai |
| Automatically CSRF cookie jaisa behavior nahi | CSRF protection consider karni hoti hai                 |

**Important:** Koi storage option har situation mein automatically secure nahi hota. Overall security implementation par depend karti hai.

---

## 12. Authorization ke Types

Authorization ke multiple models hain.

### A. Role-Based Access Control (RBAC)

RBAC ka full form Role-Based Access Control hai.

Ismein permissions user ke role ke basis par decide hoti hain.

Example:

| Role    | Permissions                |
| ------- | -------------------------- |
| Admin   | Manage users and products  |
| Manager | Manage products and orders |
| User    | View and purchase products |

Example user data:

```json
{
  "id": "101",
  "name": "Rahul",
  "role": "admin"
}
```

Backend role check karega aur uske according access allow karega.

### B. Attribute-Based Access Control (ABAC)

ABAC ka full form Attribute-Based Access Control hai.

Ismein access multiple attributes aur policies ke basis par decide hota hai.

Example:

- User department = HR
- Resource department = HR
- Time = Office hours

Policy ke according access allow ho sakta hai.

### C. Resource Ownership-Based Authorization

Ismein user ko sirf apne resources access karne ki permission di jaati hai.

Example:

User 101 sirf apna profile edit kar sakta hai.

User 101 ko User 102 ka profile edit karne ki permission nahi honi chahiye.

**Important:** URL mein user ID change karke kisi doosre user ka data access kar pana authorization vulnerability hai. Is type ki problem ko Broken Object Level Authorization (BOLA) bhi kehte hain.

---

## 13. Authentication Middleware

Middleware request aur response ke beech execute hone wala function hai.

Authentication middleware protected route access karne se pehle user ki identity verify karta hai.

Express example:

```javascript
const jwt = require("jsonwebtoken");

function authenticateToken(req, res, next) {
  const authHeader = req.headers.authorization;

  const token = authHeader?.split(" ")[1];

  if (!token) {
    return res.status(401).json({
      message: "Access token required",
    });
  }

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);

    req.user = decoded;

    next();
  } catch (error) {
    return res.status(401).json({
      message: "Invalid or expired token",
    });
  }
}
```

Protected route:

```javascript
app.get("/api/v1/profile", authenticateToken, (req, res) => {
  res.json({
    message: "Profile fetched",
    user: req.user,
  });
});
```

### Middleware ka Flow

```text
Client Request
      |
      v
Authentication Middleware
      |
      |-- No/Invalid Token --> 401 Response
      |
      |-- Valid Token
              |
              v
          next()
              |
              v
          Controller
              |
              v
          Response
```

---

## 14. Authorization Middleware

Authentication middleware user ko identify karta hai.

Authorization middleware check karta hai ki user ke paas required permission hai ya nahi.

Example:

```javascript
function authorizeRole(...allowedRoles) {
  return (req, res, next) => {
    if (!req.user || !allowedRoles.includes(req.user.role)) {
      return res.status(403).json({
        message: "Access forbidden",
      });
    }

    next();
  };
}
```

Route:

```javascript
app.delete(
  "/api/v1/users/:id",
  authenticateToken,
  authorizeRole("admin"),
  deleteUser,
);
```

Is route mein:

1. Pehle token verify hoga.
2. Phir role check hoga.
3. Sirf admin delete operation kar sakta hai.

### 401 vs 403

| Status           | Meaning                                                   |
| ---------------- | --------------------------------------------------------- |
| 401 Unauthorized | Valid authentication credentials missing ya invalid hain  |
| 403 Forbidden    | Request samajh aa gayi, lekin user ko permission nahi hai |

Easy way:

- 401 = Identity verify nahi hui.
- 403 = Identity known hai, permission nahi hai.

---

## 15. Authentication and Authorization in MERN

MERN application mein complete login flow:

```text
             React
               |
               | Login Form
               v
         Express API
               |
               | Validate Input
               v
           MongoDB
               |
               | Find User
               v
         Verify Password
               |
               | Correct?
               v
       Create Session/JWT
               |
               v
       Send Secure Response
               |
               v
             React
               |
               | Protected Request
               v
       Authentication Middleware
               |
               v
       Authorization Middleware
               |
               v
           Controller
               |
               v
           MongoDB
               |
               v
            Response
```

### Important MERN Files Structure

```text
backend/
  models/
    User.js

  routes/
    authRoutes.js
    userRoutes.js

  controllers/
    authController.js

  middleware/
    authMiddleware.js
    roleMiddleware.js

  server.js
```

Ye ek possible structure hai. Project ke according folders aur files different ho sakti hain.

---

## 16. Common Authentication Security Risks

### 1. Brute Force Attack

Attacker multiple password combinations try karta hai.

Protection:

- Rate limiting.
- Login attempt restrictions.
- Suspicious activity monitoring.
- MFA.

### 2. Credential Stuffing

Attacker leaked username/password combinations ko other websites par try karta hai.

Protection:

- MFA.
- Rate limiting.
- Compromised password checks.
- Suspicious login detection.

### 3. Session Hijacking

Attacker kisi valid session ko steal karke use karne ki koshish karta hai.

Protection:

- HTTPS.
- Secure and HttpOnly cookies.
- Session rotation.
- Session expiration.
- Suspicious session revocation.

### 4. XSS

Malicious JavaScript website mein execute hoti hai.

Protection:

- Input/output handling.
- Content Security Policy.
- Safe rendering.
- HttpOnly cookies for sensitive session identifiers.

### 5. CSRF

Attacker user ke browser se unwanted authenticated request karwane ki koshish karta hai.

Protection:

- CSRF tokens.
- SameSite cookies.
- Origin validation.

### 6. Broken Authorization

User ko doosre user ke data ya restricted functionality ka access mil jata hai.

Protection:

- Every sensitive request par permission check.
- Resource ownership verify.
- Server-side role/permission validation.

---

## 17. Authentication Best Practices

1. Passwords ko bcrypt ya Argon2id se hash karo.
2. HTTPS compulsory use karo.
3. JWT secret ko environment variables mein rakho.
4. Access tokens ki lifetime short rakho.
5. Refresh tokens ko securely store aur rotate karo.
6. Login par rate limiting lagao.
7. MFA support provide karo.
8. Login errors mein unnecessary account details expose mat karo.
9. Logout par sessions/tokens invalidate karne ka mechanism rakho.
10. Sensitive routes par authentication middleware lagao.

## 18. Authorization Best Practices

1. Default access deny rakho.
2. Har protected resource par authorization check karo.
3. Sirf frontend par role check karke security assume mat karo.
4. Resource ownership verify karo.
5. Minimum required permissions do.
6. Admin routes ko properly protect karo.
7. User ke role ko client ke request body se blindly trust mat karo.
8. Authorization failures ko log aur monitor karo.

---

## 19. Common Mistakes

1. Authentication aur Authorization ko same samajhna.
2. Plain text password database mein store karna.
3. JWT payload ko encrypted samajhna.
4. Expired token accept karna.
5. Frontend par hi authorization check karna.
6. Har logged-in user ko admin permissions de dena.
7. User ID ke basis par data return karna, ownership check na karna.
8. Logout par session invalidate na karna.
9. Refresh token ko insecurely store karna.
10. 401 aur 403 ka wrong use karna.

---

## 20. Interview Questions and Answers

### Q1. Authentication kya hai?

User ki identity verify karna Authentication hai.

### Q2. Authorization kya hai?

Authenticated user ko resource ya action ki permission check karna Authorization hai.

### Q3. Authentication aur Authorization mein difference?

Authentication identity verify karta hai; Authorization permissions check karta hai.

### Q4. JWT kya hai?

JWT ek compact token format hai jo claims ko represent aur digitally verify karne ke liye use hota hai.

### Q5. JWT ke kitne parts hote hain?

Three parts: Header, Payload, Signature.

### Q6. Password Hashing kya hai?

Password ko one-way hash format mein convert karna, taaki plain password database mein store na ho.

### Q7. bcrypt kya hai?

bcrypt password hashing algorithm hai jo passwords ko securely hash karne ke liye use hota hai.

### Q8. Access Token aur Refresh Token mein difference?

Access token APIs access karne ke liye hota hai; refresh token new access token obtain karne ke liye.

### Q9. RBAC kya hai?

Role-Based Access Control mein permissions user ke role ke basis par assign hoti hain.

### Q10. ABAC kya hai?

Attribute-Based Access Control mein permissions user, resource, environment aur policy attributes ke basis par decide hoti hain.

### Q11. 401 aur 403 mein difference?

401 authentication failure/missing credentials indicate karta hai; 403 permission denied indicate karta hai.

### Q12. MFA kya hai?

Multiple independent authentication factors ke through identity verify karna MFA hai.

### Q13. JWT payload mein password store kar sakte hain?

Nahi. JWT payload generally encoded hota hai, encrypted nahi.

### Q14. BOLA kya hai?

Broken Object Level Authorization mein user kisi doosre user ke object/resource ko unauthorized access kar leta hai.

---

## 21. Practical Tasks

### Task 1: Signup API

Express mein signup API banao jo:

- Name aur email validate kare.
- Duplicate email check kare.
- Password bcrypt se hash kare.
- User ko MongoDB mein save kare.

### Task 2: Login API

Login API banao jo:

- Email se user find kare.
- bcrypt se password compare kare.
- Successful login par session ya JWT issue kare.

### Task 3: Authentication Middleware

JWT verify karne wala middleware banao.

### Task 4: Admin Authorization

Aisa middleware banao jo sirf admin ko user delete karne de.

### Task 5: Ownership Check

Aisa endpoint banao jahan user sirf apna profile update kar sake.

---

## 22. Quick Revision

- Authentication = User kaun hai?
- Authorization = User kya kar sakta hai?
- Signup = New account create karna.
- Login = Existing user verify karna.
- Hashing = One-way password transformation.
- bcrypt/Argon2id = Password hashing algorithms.
- JWT = JSON Web Token.
- JWT Parts = Header, Payload, Signature.
- Access Token = Protected API access.
- Refresh Token = New access token obtain karna.
- MFA = Multiple authentication factors.
- RBAC = Role-based permissions.
- ABAC = Attribute-based permissions.
- Middleware = Request processing ke beech execute hone wala function.
- 401 = Authentication missing/invalid.
- 403 = Permission denied.
- BOLA = Unauthorized object/resource access.

---

## 23. Topic Completion Checklist

- [ ] Authentication samajh liya.
- [ ] Authorization samajh liya.
- [ ] Dono ka difference samajh liya.
- [ ] Authentication ke types samajh liye.
- [ ] Signup/Login flow samajh liya.
- [ ] Password Hashing samajh li.
- [ ] Hashing vs Encryption samajh liya.
- [ ] JWT aur uske three parts samajh liye.
- [ ] Access Token and Refresh Token samajh liye.
- [ ] Cookie vs LocalStorage samajh liya.
- [ ] RBAC and ABAC samajh liya.
- [ ] Authentication Middleware samajh liya.
- [ ] Authorization Middleware samajh liya.
- [ ] 401 vs 403 samajh liya.
- [ ] MERN Authentication Flow samajh liya.
- [ ] Common security risks samajh liye.

**Topic 14 Complete – Authentication & Authorization.**
