# Topic 01: Introduction to LLD (Low Level Design)

## 1. What is LLD?

LLD ka full form **Low Level Design** hai.

LLD software development ka ek important part hai jisme hum decide karte hain ki software ke individual components internally kaise kaam karenge.

Simple language mein:

**LLD batata hai ki software ko code level par kaise implement karna hai.**

Ismein hum define karte hain:

- Classes
- Objects
- Methods
- Functions
- Interfaces
- Relationships
- Data flow
- Design Patterns

### Example

Maan lo tum ek E-commerce application bana rahe ho.

Application mein features hain:

- User Login
- Product Listing
- Add to Cart
- Order Placement
- Payment

LLD mein hum decide karenge:

- User class kaise banegi?
- Product class mein kaun se properties hongi?
- Cart class kaise work karegi?
- Order place karne ke liye kaun se methods honge?
- Payment process kaise implement hoga?

Ye sab LLD ka part hai.

---

## 2. What is the Purpose of LLD?

LLD ka main purpose software ko properly design karna hai, taaki code:

1. Easy to understand ho.
2. Easy to maintain ho.
3. Reusable ho.
4. Easily test ho sake.
5. Future mein easily modify ho sake.
6. Unnecessary complexity se bacha rahe.

### Example

Maan lo tumne poora e-commerce application ek hi file mein likh diya.

```javascript
function ecommerceApp() {
  // Login code
  // Product code
  // Cart code
  // Order code
  // Payment code
}
```

Jaise-jaise application badi hogi, code manage karna difficult ho jayega.

LLD ki help se hum application ko different classes aur components mein divide kar sakte hain.

---

## 3. LLD vs HLD

System Design ke do important parts hain:

1. HLD – High Level Design
2. LLD – Low Level Design

### HLD (High Level Design)

HLD batata hai ki poore system ki architecture kaisi hogi.

Example:

- Frontend
- Backend
- Database
- Cache
- Load Balancer
- Different Services

### LLD (Low Level Design)

LLD batata hai ki individual components internally kaise implement honge.

Example:

- Classes
- Objects
- Methods
- Interfaces
- Class relationships

### Difference Between HLD and LLD

| HLD                                | LLD                                  |
| ---------------------------------- | ------------------------------------ |
| High Level Design                  | Low Level Design                     |
| Overall architecture               | Internal implementation              |
| System components define karta hai | Classes aur methods define karta hai |
| Services aur databases par focus   | Objects aur code structure par focus |
| Big picture deta hai               | Detailed picture deta hai            |

### Simple Example: E-commerce Application

**HLD:**

```text
        E-commerce System
                |
      +---------+---------+
      |         |         |
   Frontend   Backend   Database
```

**LLD:**

```text
       E-commerce Backend
                |
      +---------+---------+
      |         |         |
    User      Product    Order
    Class      Class     Class
      |         |         |
    Login     getData   placeOrder
```

**Yaad rakho:**

HLD = System ka overall structure.

LLD = System ke components ka detailed design.

---

## 4. Real-Life Example of LLD

Maan lo tumhe ek ATM machine ka software banana hai.

ATM mein features honge:

- Card Insert
- PIN Verification
- Check Balance
- Withdraw Money
- Deposit Money

LLD mein hum decide karenge:

### Classes

```text
ATM
Card
Account
Transaction
Bank
```

### Methods

```text
ATM:
- insertCard()
- enterPin()
- withdrawMoney()

Account:
- checkBalance()
- debit()
- credit()

Transaction:
- createTransaction()
- getTransactionDetails()
```

Ab developer ko clear hai ki kis class ki kya responsibility hogi.

Isse coding aur maintenance easy ho jaati hai.

---

## 5. Important Components of LLD

LLD mein kuch important building blocks use hote hain.

### 1. Class

Class ek blueprint hoti hai jiske through objects create kiye jaate hain.

Example:

```cpp
class Car {
public:
    string brand;

    void start() {
        cout << "Car Started";
    }
};
```

### 2. Object

Object class ka instance hota hai.

Example:

```cpp
Car car1;
car1.brand = "BMW";
car1.start();
```

### 3. Methods

Methods class ke andar defined functions hote hain jo object ka behavior represent karte hain.

Example:

```cpp
class Student {
public:
    void study() {
        cout << "Student is studying";
    }
};
```

### 4. Properties

Properties object ka data ya characteristics represent karti hain.

Example:

```cpp
class Student {
public:
    string name;
    int age;
};
```

### 5. Interface

Interface ek contract define karta hai ki implementing class ko kaun se operations provide karne hain.

Java mein interface ka example:

```java
interface Payment {
    void pay();
}
```

JavaScript mein native `interface` keyword nahi hota. Lekin similar contract patterns use kiye ja sakte hain.

### 6. Relationships

Classes ek doosre ke saath different relationships rakh sakti hain.

Examples:

- Association
- Aggregation
- Composition
- Inheritance

In relationships ko hum aage detail mein padhenge.

---

## 6. LLD and OOP

OOP ka full form Object-Oriented Programming hai.

OOP ek programming approach hai jisme software ko objects aur classes ke through organize kiya jata hai.

LLD mein OOP concepts ka bahut important role hota hai.

### Four Pillars of OOP

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

Example:

```text
             OOP
              |
     +--------+--------+
     |        |        |
 Encapsulation Abstraction
     |        |
 Inheritance Polymorphism
```

In chaaron concepts ko hum separately detail mein padhenge.

---

## 7. LLD and Design Patterns

Design Pattern ek commonly used, reusable solution approach hota hai jo recurring software design problems ko solve karne mein help karta hai.

Example:

Maan lo application mein ek hi configuration object ka controlled instance maintain karna hai.

Is situation mein Singleton Pattern useful ho sakta hai.

Kuch popular Design Patterns:

- Singleton Pattern
- Factory Pattern
- Builder Pattern
- Strategy Pattern
- Observer Pattern
- Adapter Pattern

In patterns ko hum aage practical examples ke saath padhenge.

---

## 8. LLD and UML Diagrams

UML ka full form **Unified Modeling Language** hai.

UML diagrams software system ko visually represent karne mein help karte hain.

LLD mein commonly use hone wale diagrams:

1. Class Diagram
2. Sequence Diagram
3. Use Case Diagram
4. Activity Diagram

### Example: Class Diagram

```text
+------------------+
|      User        |
+------------------+
| - name           |
| - email          |
+------------------+
| + login()        |
| + logout()       |
+------------------+
```

Is diagram mein:

- User = Class
- name, email = Attributes
- login(), logout() = Methods

UML diagrams ko hum aage separately detail mein seekhenge.

---

## 9. Advantages of LLD

1. Code organized rehta hai.
2. Code reuse karna easy hota hai.
3. Bugs identify karna easier ho sakta hai.
4. Testing easy hoti hai.
5. Team collaboration improve hota hai.
6. Future changes manage karna easy hota hai.
7. Code maintainability improve hoti hai.

---

## 10. Disadvantages of LLD

1. Initial design mein extra time lag sakta hai.
2. Small applications ke liye unnecessary complexity create ho sakti hai.
3. Overengineering ka risk hota hai.
4. Poor design future mein problems create kar sakta hai.

**Important:** Har small project ke liye complex LLD banana zaroori nahi hai. Design project ki requirements ke according hona chahiye.

---

## 11. When Should We Use LLD?

LLD especially useful hota hai jab:

- Application large ho.
- Multiple developers kaam kar rahe hon.
- Code maintain karna ho.
- Application mein complex business logic ho.
- Future mein features add hone ki possibility ho.
- Software ko testable aur reusable banana ho.

---

## 12. LLD in MERN Stack

Tum MERN Stack use karke bhi LLD concepts implement kar sakte ho.

Example: E-commerce application.

### Backend Structure

```text
backend/
|
|-- models/
|    |-- User.js
|    |-- Product.js
|    |-- Order.js
|
|-- controllers/
|    |-- userController.js
|    |-- productController.js
|    |-- orderController.js
|
|-- services/
|    |-- userService.js
|    |-- paymentService.js
|
|-- routes/
|    |-- userRoutes.js
|    |-- productRoutes.js
|    |-- orderRoutes.js
|
|-- server.js
```

Ye ek possible layered project structure hai.

### Iska purpose

- Models: Data structure define karna.
- Controllers: HTTP requests aur responses handle karna.
- Services: Business logic manage karna.
- Routes: API endpoints define karna.

**Important:** Ye structure LLD ke principles ko apply karne ka ek example hai. MERN project mein har jagah OOP classes use karna compulsory nahi hai. Functional modules aur services ke through bhi clean design banaya ja sakta hai.

---

## 13. Common Mistakes

1. HLD aur LLD ko same samajhna.
2. LLD ko sirf coding samajhna.
3. Har project mein unnecessary design patterns use karna.
4. Class ki responsibility clearly define na karna.
5. Code ko unnecessarily complex banana.
6. OOP concepts ko ignore karna.
7. Future maintainability ke baare mein na sochna.

---

## 14. Interview Questions

### Q1. What is LLD?

LLD stands for Low Level Design. It defines the detailed internal structure and implementation of software components.

### Q2. What is the difference between HLD and LLD?

HLD defines overall system architecture, whereas LLD defines the detailed design of individual components.

### Q3. What are the main components of LLD?

Classes, objects, methods, attributes, interfaces and relationships.

### Q4. What is OOP?

Object-Oriented Programming is a programming paradigm based on classes and objects.

### Q5. What are the four pillars of OOP?

- Encapsulation
- Abstraction
- Inheritance
- Polymorphism

### Q6. What is a Design Pattern?

A reusable solution approach to a commonly occurring software design problem.

### Q7. What is UML?

Unified Modeling Language is used to visually represent software designs.

### Q8. Why is LLD important?

It helps create maintainable, reusable, testable and organized software.

---

## 15. Practical Tasks

1. ATM application ke liye 5 possible classes ke naam likho.
2. Student Management System ke liye classes aur methods identify karo.
3. HLD aur LLD ke beech 5 differences likho.
4. E-commerce application ka basic class diagram draw karo.
5. Apne MERN project ke models, controllers aur services identify karo.

---

## 16. Quick Revision

| Term            | Meaning                                   |
| --------------- | ----------------------------------------- |
| LLD             | Detailed software design                  |
| HLD             | Overall system architecture               |
| Class           | Object ka blueprint                       |
| Object          | Class ka instance                         |
| Method          | Class ke andar function                   |
| Property        | Object ka data                            |
| Interface       | Operations ka contract                    |
| OOP             | Object-Oriented Programming               |
| Design Pattern  | Reusable design solution                  |
| UML             | Unified Modeling Language                 |
| Class Diagram   | Classes aur relationships ka diagram      |
| Maintainability | Code ko modify aur maintain karne ki ease |

---

## 17. Topic Completion Checklist

- [ ] LLD ka meaning samajh liya.
- [ ] LLD ka purpose samajh liya.
- [ ] HLD vs LLD difference samajh liya.
- [ ] Real-life ATM example samajh liya.
- [ ] Class aur Object ka basic meaning samajh liya.
- [ ] Methods aur Properties samajh li.
- [ ] Interfaces aur Relationships ka basic idea samajh liya.
- [ ] OOP ka connection samajh liya.
- [ ] Design Patterns ka introduction samajh liya.
- [ ] UML diagrams ka introduction samajh liya.
- [ ] MERN Stack mein LLD ka use samajh liya.

**Topic 01 Complete – Introduction to LLD**
