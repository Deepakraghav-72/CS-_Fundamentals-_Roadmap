# Topic 12: API Design & Versioning

## 1. API Design kya hota hai?

API Design ka matlab hai API ko plan aur structure karna, taaki frontend aur backend ke beech communication simple, consistent, secure aur easy to maintain rahe.

**Example:**

Maan lo hum ek MERN-based E-commerce application bana rahe hain.

Frontend ko products chahiye. Backend mein API banayenge:

```http
GET /api/v1/products
```

Frontend is endpoint ko call karega aur backend products ka data return karega.

Achhi API Design se:

- Developer ko API samajhne mein aasani hoti hai.
- Frontend aur backend integration easy hota hai.
- Future mein API update karna easy hota hai.
- Errors aur bugs kam hote hain.
- API maintain karna easy hota hai.

---

## 2. Good API Design ki Important Qualities

Ek achhi API mein ye qualities honi chahiye:

| Quality         | Meaning                                 |
| --------------- | --------------------------------------- |
| Simple          | API samajhne mein easy ho               |
| Consistent      | Sabhi endpoints ka structure similar ho |
| Secure          | Unauthorized access na ho               |
| Scalable        | Traffic badhne par bhi kaam kare        |
| Reliable        | Expected result de                      |
| Maintainable    | Future changes easy hon                 |
| Well-documented | API ki proper documentation ho          |

---

## 3. API Endpoint Naming Best Practices

Endpoint ka naam decide karna API Design ka important part hai.

### Rule 1: Nouns use karo, verbs nahi

Resources ko represent karne ke liye nouns use karte hain.

**Wrong:**

```http
GET /getUsers
POST /createUser
GET /deleteProduct
```

**Correct:**

```http
GET /users
POST /users
GET /products
DELETE /products/101
```

HTTP method khud action batata hai, isliye endpoint mein action likhne ki zarurat nahi hoti.

### Rule 2: Plural Nouns use karo

Collection ke liye generally plural nouns use karte hain.

```http
/users
/products
/orders
```

### Rule 3: Lowercase URLs use karo

Recommended:

```http
/api/v1/products
/api/v1/user-profiles
```

Avoid:

```http
/API/V1/Products
/API/V1/UserProfiles
```

### Rule 4: Words ko separate karne ke liye hyphen use karo

Recommended:

```http
/user-profiles
/order-details
```

### Rule 5: Unnecessary nested routes avoid karo

Recommended:

```http
GET /users/10/orders
```

Bahut deeply nested route avoid karo:

```http
GET /companies/1/departments/2/teams/3/users/10/orders
```

Jab zarurat ho, tabhi nested routes use karo.

---

## 4. API URI Structure

URI ka matlab Uniform Resource Identifier hai. API mein URI resource ko identify karta hai.

Example:

```http
https://example.com/api/v1/users/101
```

Iske parts:

| Part          | Meaning          |
| ------------- | ---------------- |
| `https`       | Protocol         |
| `example.com` | Domain           |
| `/api`        | API base path    |
| `/v1`         | API version      |
| `/users`      | Resource         |
| `/101`        | Specific user ID |

**Remember:** Endpoint URI ka woh path hota hai jiske through hum API resource ko access karte hain.

---

## 5. Path Parameters

Path parameter kisi specific resource ko identify karta hai.

Example:

```http
GET /users/101
```

Yahan `101` user ID hai.

Express.js example:

```javascript
app.get("/users/:id", (req, res) => {
  const userId = req.params.id;

  res.json({
    message: "User fetched",
    userId: userId,
  });
});
```

Request:

```http
GET /users/101
```

Response:

```json
{
  "message": "User fetched",
  "userId": "101"
}
```

**Use:** Jab kisi specific resource ko access karna ho.

---

## 6. Query Parameters

Query parameters ka use data ko filter, sort, search aur paginate karne ke liye hota hai.

Example:

```http
GET /products?category=mobile&sort=price
```

Yahan:

- `category=mobile` filtering ke liye hai.
- `sort=price` sorting ke liye hai.

Express.js:

```javascript
app.get("/products", (req, res) => {
  const category = req.query.category;
  const sort = req.query.sort;

  res.json({
    category,
    sort,
  });
});
```

### Common Query Parameters

| Parameter  | Use                  |
| ---------- | -------------------- |
| `search`   | Search karne ke liye |
| `category` | Category filter      |
| `sort`     | Sorting              |
| `page`     | Page number          |
| `limit`    | Records ki limit     |
| `minPrice` | Minimum price        |
| `maxPrice` | Maximum price        |

Example:

```http
GET /products?search=iphone&minPrice=10000&maxPrice=50000
```

---

## 7. Filtering, Sorting and Searching

### A. Filtering

Filtering ka matlab hai conditions ke according data return karna.

Example:

```http
GET /products?category=mobile
```

Sirf mobile category ke products return honge.

### B. Sorting

Sorting ka matlab hai data ko kisi order mein arrange karna.

Example:

```http
GET /products?sort=price
```

Price ke according ascending order mein products aa sakte hain.

Descending order ke liye:

```http
GET /products?sort=-price
```

API ko clearly document karna chahiye ki sorting ka format kya hai.

### C. Searching

Searching ka matlab hai kisi keyword ke basis par data find karna.

Example:

```http
GET /products?search=samsung
```

Backend Samsung se related products return karega.

---

## 8. Pagination

Pagination ka matlab hai bade data ko chhote-chhote parts ya pages mein divide karna.

**Example:**

Maan lo database mein 10,000 products hain.

Agar ek saath saare products bhej denge, toh:

- Server par load badhega.
- Network par zyada data transfer hoga.
- Frontend slow ho sakta hai.

Isliye pagination use karte hain.

### Offset-based Pagination

Example:

```http
GET /products?page=1&limit=10
```

- `page=1` means first page.
- `limit=10` means 10 products.

Second page:

```http
GET /products?page=2&limit=10
```

Backend calculation:

```javascript
const page = Number(req.query.page) || 1;
const limit = Number(req.query.limit) || 10;

const skip = (page - 1) * limit;
```

MongoDB example:

```javascript
const products = await Product.find().skip(skip).limit(limit);
```

### Cursor-based Pagination

Cursor-based pagination mein next records ko find karne ke liye kisi record ki position ya unique identifier ko cursor ke roop mein use kiya jata hai.

Example:

```http
GET /products?limit=10&cursor=product_105
```

Response:

```json
{
  "data": [
    {
      "id": "product_106",
      "name": "Mobile"
    }
  ],
  "nextCursor": "product_106"
}
```

### Offset vs Cursor Pagination

| Offset Pagination                                       | Cursor Pagination                            |
| ------------------------------------------------------- | -------------------------------------------- |
| Page number use karta hai                               | Cursor use karta hai                         |
| Simple implementation                                   | Thoda complex                                |
| Large offset slow ho sakta hai                          | Large datasets ke liye useful                |
| Data insert/delete hone par records shift ho sakte hain | Changing datasets mein generally more stable |

**Important:** Small applications ke liye offset pagination simple hai. Large aur frequently changing datasets ke liye cursor pagination useful ho sakti hai.

---

## 9. Consistent Request and Response Structure

API Design mein request aur response ka structure consistent hona chahiye.

### Example: User Create Request

```http
POST /api/v1/users
Content-Type: application/json
```

Request Body:

```json
{
  "name": "Rahul",
  "email": "rahul@example.com",
  "password": "secret123"
}
```

### Successful Response

```json
{
  "success": true,
  "message": "User created successfully",
  "data": {
    "id": "101",
    "name": "Rahul",
    "email": "rahul@example.com"
  }
}
```

Notice:

- `success` batata hai request successful hui ya nahi.
- `message` readable information deta hai.
- `data` actual result contain karta hai.

**Security:** Password ko response mein kabhi return nahi karna chahiye.

---

## 10. API Error Response Design

API mein error responses ka format bhi consistent hona chahiye.

Example:

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    {
      "field": "email",
      "message": "Invalid email address"
    }
  ]
}
```

### Common Error Status Codes

| Status Code | Meaning               |
| ----------- | --------------------- |
| 400         | Bad Request           |
| 401         | Unauthorized          |
| 403         | Forbidden             |
| 404         | Resource Not Found    |
| 409         | Conflict              |
| 422         | Validation Error      |
| 429         | Too Many Requests     |
| 500         | Internal Server Error |

### Important Rules

1. Error message understandable hona chahiye.
2. Internal database details expose nahi karni chahiye.
3. Password, secret keys aur tokens error response mein nahi bhejne chahiye.
4. Correct HTTP status code use karna chahiye.

Example:

```javascript
res.status(404).json({
  success: false,
  message: "User not found",
});
```

---

## 11. API Validation

Validation ka matlab hai user se aane wale data ko check karna ki woh correct hai ya nahi.

Example:

- Name empty nahi hona chahiye.
- Email valid hona chahiye.
- Password minimum length follow kare.
- Age valid number ho.

Express example:

```javascript
app.post("/users", (req, res) => {
  const { name, email } = req.body;

  if (!name || !email) {
    return res.status(400).json({
      success: false,
      message: "Name and email are required",
    });
  }

  res.status(201).json({
    success: true,
    message: "User data is valid",
  });
});
```

Production applications mein Zod, Joi ya express-validator jaise validation tools use kar sakte hain.

**Important:** Frontend validation ke saath backend validation bhi compulsory hai. Frontend validation ko bypass kiya ja sakta hai.

---

## 12. API Documentation

API Documentation ka matlab hai API ke endpoints aur unke usage ki proper information dena.

Documentation mein ye details honi chahiye:

- Endpoint URL
- HTTP method
- Required parameters
- Request body
- Response body
- Status codes
- Authentication requirements
- Error responses

### Swagger / OpenAPI

Swagger aur OpenAPI API documentation ke liye commonly used tools/specification hain.

OpenAPI ek standard specification hai jisme API ka structure describe kiya jata hai.

Swagger UI OpenAPI documentation ko interactive format mein show kar sakta hai.

Example documentation:

```yaml
paths:
  /users:
    get:
      summary: Get all users
      responses:
        "200":
          description: Users fetched successfully
```

Benefits:

- Frontend developers ko API samajhne mein help.
- Backend developers ko API structure clear.
- API testing aur collaboration easy.

---

## 13. API Versioning kya hoti hai?

API Versioning ka matlab hai API ke different versions maintain karna.

Maan lo tumhari application ka API hai:

```http
GET /api/v1/users
```

Ab tum API mein aisa change karna chahte ho jisse purana frontend break ho sakta hai.

Agar directly purani API change kar doge, toh existing application mein problems aa sakti hain.

Isliye naya version create karte hain:

```http
GET /api/v2/users
```

Ab:

- Old frontend `v1` use kar sakta hai.
- New frontend `v2` use kar sakta hai.

### API Versioning ki Need

1. Existing clients ko support karna.
2. Breaking changes safely introduce karna.
3. API ko gradually upgrade karna.
4. Different clients ko different versions provide karna.

---

## 14. API Versioning Strategies

API versioning ke multiple methods hote hain.

### A. URI / URL Versioning

Version URL ke andar mention hota hai.

```http
/api/v1/users
/api/v2/users
```

**Advantages:**

- Easy to understand.
- Version clearly visible.
- Testing aur debugging easy.

**Disadvantages:**

- Multiple routes maintain karne pad sakte hain.
- URL version-specific ho jata hai.

Ye commonly used approach hai.

### B. Query Parameter Versioning

Version query parameter ke through bhejte hain.

```http
/api/users?version=1
/api/users?version=2
```

**Advantages:**

- URL path same rehta hai.
- Implement karna simple ho sakta hai.

**Disadvantages:**

- Version URL mein kam visible hota hai.
- Caching configuration carefully manage karni pad sakti hai.

### C. Header Versioning

Version HTTP header ke through bhejte hain.

```http
GET /api/users
API-Version: 2
```

**Advantages:**

- URL clean rehta hai.
- Version URL ke bajay request metadata mein hota hai.

**Disadvantages:**

- Version URL se easily visible nahi hota.
- Client ko correct header bhejna padta hai.

### D. Media Type Versioning

Version Accept header ke media type mein specify kar sakte hain.

```http
Accept: application/vnd.example.v2+json
```

Ye content negotiation based approach hai.

### Comparison

| Strategy              | Version Kahan Hota Hai? |
| --------------------- | ----------------------- |
| URI Versioning        | URL path                |
| Query Versioning      | Query parameter         |
| Header Versioning     | HTTP header             |
| Media Type Versioning | Accept header           |

**Important:** Koi ek strategy har application ke liye compulsory nahi hai. Project requirements ke according choose karte hain.

---

## 15. Backward Compatibility

Backward Compatibility ka matlab hai naye changes ke baad bhi purane clients ka kaam karte rehna.

Example:

Old API response:

```json
{
  "id": 101,
  "name": "Rahul"
}
```

New API response:

```json
{
  "id": 101,
  "name": "Rahul",
  "city": "Delhi"
}
```

Agar `city` ek optional additional field hai, toh existing clients generally kaam kar sakte hain.

Ye backward-compatible change ho sakta hai.

### Breaking Changes

Aise changes jo existing clients ka code tod sakte hain.

Example:

Old:

```json
{
  "id": 101,
  "name": "Rahul"
}
```

New:

```json
{
  "id": 101,
  "fullName": "Rahul"
}
```

Yahan `name` ko remove karke `fullName` kar diya. Purana frontend `name` read karega toh problem ho sakti hai.

### Common Breaking Changes

- Existing field remove karna.
- Field ka naam change karna.
- Field ka data type change karna.
- Existing endpoint remove karna.
- Required field add karna jise purane clients send nahi karte.
- Existing behavior ka meaning change karna.

---

## 16. Semantic Versioning vs API Versioning

Dono related concepts hain, lekin same nahi hain.

### Semantic Versioning (SemVer)

Software releases ko version number dene ka ek convention hai.

Format:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
2.4.1
```

Meaning:

| Part  | Meaning                          |
| ----- | -------------------------------- |
| MAJOR | Breaking changes                 |
| MINOR | Backward-compatible new features |
| PATCH | Backward-compatible bug fixes    |

Example:

```text
1.0.0 → 2.0.0
```

Major version change.

```text
1.0.0 → 1.1.0
```

New backward-compatible feature.

```text
1.0.0 → 1.0.1
```

Bug fix.

### API Versioning vs SemVer

| API Versioning                                          | Semantic Versioning                       |
| ------------------------------------------------------- | ----------------------------------------- |
| API clients ko different API versions provide karta hai | Software release numbers define karta hai |
| Example: `/api/v1/users`                                | Example: `2.4.1`                          |
| Routing aur compatibility se related                    | Release numbering convention              |

Dono concepts ko ek project mein saath use kiya ja sakta hai.

---

## 17. API Deprecation and Sunset

Deprecation ka matlab hai kisi old API version ko future mein remove karne ka decision announce karna.

Example:

```text
/api/v1/users
```

Company decide karti hai ki future mein `v1` band hoga aur clients ko `v2` par migrate karna hoga.

### Deprecation Process

1. New API version release karo.
2. Old version ko deprecated announce karo.
3. Developers ko migration instructions do.
4. Clients ko migrate karne ka time do.
5. Planned date par old version retire karo.

**Sunset** ka matlab hai old API ke support ya availability ko end karna.

API consumers ko clear notice dena chahiye, aur applicable cases mein `Deprecation` aur `Sunset` HTTP headers ka use bhi kiya ja sakta hai.

---

## 18. Idempotency Key in API Design

Idempotency ka basic meaning hai same request ko multiple times perform karne par final effect same rehna.

Example:

Maan lo user payment karta hai.

Network problem ke karan frontend ko response nahi milta aur woh same payment request dobara bhej deta hai.

Agar backend duplicate payment create kar de, toh problem hogi.

Isliye payment API mein Idempotency Key use ki ja sakti hai.

Example:

```http
POST /api/v1/payments
Idempotency-Key: payment-unique-123
```

Backend:

1. Key check karega.
2. Agar key pehle process ho chuki hai, toh stored result return karega.
3. Agar key new hai, toh payment process karke result save karega.

**Important:** Sirf header bhejne se idempotency automatically implement nahi hoti. Backend ko key store karke duplicate requests handle karni hoti hain.

---

## 19. API Security Best Practices

API design karte waqt security ka dhyan rakhna important hai.

1. HTTPS use karo.
2. Authentication implement karo.
3. Authorization check karo.
4. Request data validate karo.
5. Sensitive information expose mat karo.
6. Rate limiting implement karo.
7. Database queries ko safely handle karo.
8. Secrets ko environment variables mein rakho.

Example:

Agar user `101` apna profile access kar raha hai, toh backend ko verify karna chahiye ki logged-in user ko us profile ko access karne ki permission hai.

Sirf URL mein user ID hona authorization ka proof nahi hai.

---

## 20. MERN Stack Practical Example: Versioned API

Express.js mein versioned routes ka example:

```javascript
const express = require("express");

const app = express();

app.use(express.json());

// API Version 1
app.get("/api/v1/users", (req, res) => {
  res.json({
    version: "v1",
    users: [
      {
        id: 1,
        name: "Rahul",
      },
    ],
  });
});

// API Version 2
app.get("/api/v2/users", (req, res) => {
  res.json({
    version: "v2",
    data: [
      {
        id: 1,
        fullName: "Rahul",
        city: "Delhi",
      },
    ],
  });
});

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

Ab dono endpoints available hain:

```http
GET http://localhost:5000/api/v1/users
GET http://localhost:5000/api/v2/users
```

### MERN Architecture mein API Flow

```text
React Frontend
      |
      | API Request
      v
Express.js Routes
      |
      v
Validation & Authentication
      |
      v
Controller
      |
      v
MongoDB / Mongoose
      |
      v
JSON Response
      |
      v
React Frontend
```

Is tarah React frontend Express API ke through MongoDB se data access karta hai.

---

## 21. Common Mistakes

1. Endpoints mein unnecessary verbs use karna.
2. Har endpoint ka response format alag rakhna.
3. Backend validation na karna.
4. Sensitive data response mein bhejna.
5. API versioning ka plan na banana.
6. Breaking changes ko bina notice introduce karna.
7. Large datasets ko bina pagination return karna.
8. Internal server errors ki details expose karna.
9. API documentation maintain na karna.
10. Authorization checks miss karna.

---

## 22. Interview Questions and Answers

### Q1. API Design kya hai?

API endpoints, request, response aur communication rules ko plan aur structure karna API Design hai.

### Q2. API endpoints mein nouns kyun use karte hain?

Resource ko represent karne ke liye nouns use karte hain. HTTP method action define karta hai.

### Q3. Pagination kya hai?

Large data ko small pages ya chunks mein divide karna pagination hai.

### Q4. Offset aur Cursor Pagination mein kya difference hai?

Offset pagination page/offset use karti hai, jabki cursor pagination next records identify karne ke liye cursor use karti hai.

### Q5. API Versioning kya hai?

API ke different versions maintain karna API Versioning hai.

### Q6. API Versioning ki zarurat kyun hoti hai?

Existing clients ko break kiye bina API mein changes introduce karne ke liye.

### Q7. Backward Compatibility kya hai?

Naye changes ke baad bhi old clients ka properly work karte rehna backward compatibility hai.

### Q8. Breaking Change kya hai?

Aisa API change jo existing clients ke code ko break kar sakta hai.

### Q9. Swagger kya hai?

Swagger tools OpenAPI specification ke through API documentation ko create aur interactively explore karne mein help karte hain.

### Q10. Idempotency Key kya hai?

Ek unique key jiske through backend repeated requests ko identify karke duplicate operations se bach sakta hai.

---

## 23. Practical Tasks

### Task 1: User API Design

In endpoints ko design karo:

- All users fetch
- Single user fetch
- New user create
- User update
- User delete

### Task 2: Product Filtering

Aisa endpoint design karo:

```http
GET /api/v1/products?category=mobile&sort=price&page=1&limit=10
```

### Task 3: API Versioning

Express.js mein do endpoints banao:

```http
/api/v1/products
/api/v2/products
```

Dono ka response structure alag rakho.

### Task 4: Error Response

Ek consistent error response format design karo jisme `success`, `message` aur `errors` fields hon.

---

## 24. Quick Revision

- API Design = API ka structure aur rules plan karna.
- Endpoint = API resource ka access path.
- Nouns = Resource naming ke liye use hote hain.
- Path Parameters = Specific resource identify karte hain.
- Query Parameters = Filtering, sorting, searching aur pagination.
- Pagination = Large data ko small parts mein divide karna.
- Offset Pagination = Page/offset based.
- Cursor Pagination = Cursor based.
- API Documentation = API usage ki complete information.
- OpenAPI = API documentation ki standard specification.
- API Versioning = Different API versions maintain karna.
- Backward Compatibility = Old clients ka working rehna.
- Breaking Change = Existing clients ko break karne wala change.
- Deprecation = Old API ko retire karne ka announcement.
- Idempotency Key = Duplicate operations ko handle karne mein help.

---

## 25. Topic Completion Checklist

- [ ] API Design samajh liya.
- [ ] Endpoint Naming Rules samajh liye.
- [ ] URI Structure samajh liya.
- [ ] Path aur Query Parameters samajh liye.
- [ ] Filtering, Sorting aur Searching samajh li.
- [ ] Pagination samajh li.
- [ ] Request/Response Design samajh li.
- [ ] Error Handling aur Validation samajh li.
- [ ] Swagger/OpenAPI samajh liya.
- [ ] API Versioning Strategies samajh li.
- [ ] Backward Compatibility aur Breaking Changes samajh liye.
- [ ] Semantic Versioning samajh li.
- [ ] Deprecation aur Idempotency samajh li.
- [ ] MERN Practical Example samajh liya.

**Topic 12 Complete – API Design & Versioning.**
