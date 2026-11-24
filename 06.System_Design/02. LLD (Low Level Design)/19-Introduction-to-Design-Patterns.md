# 19. Introduction to Design Patterns

## 1. Design Pattern kya hota hai?

Design Pattern software development mein aane wali common problems ka ek **reusable solution approach** hota hai.

Simple language mein:

Jab developers ko baar-baar ek jaisi problem face hoti hai, to us problem ko solve karne ke liye ek proven design approach use ki ja sakti hai. Isi approach ko Design Pattern kehte hain.

### Real-life Example

Maan lo tum ek ghar bana rahe ho.

Har baar ghar banate samay tumhe sochna pade:

- Room kaise arrange karne hain?
- Doors kahan honge?
- Windows kaise hongi?
- Electricity ka arrangement kaise hoga?

Lekin agar ek achha house design already available hai, to tum us design ko apni requirements ke according reuse kar sakte ho.

Software development mein bhi Design Patterns isi tarah help karte hain.

**Important:** Design Pattern ready-made code nahi hota. Ye ek solution ka structure ya approach hota hai jise developer apne project ke according implement karta hai.

## 2. Design Patterns ki zaroorat kyon padti hai?

Maan lo tum ek MERN E-commerce application bana rahe ho.

Application mein:

- User login
- Product management
- Cart management
- Payment
- Order management
- Notifications

Jaise-jaise application bada hota hai, code complex hone lagta hai.

Agar hum bina proper design ke code likhenge to problems aa sakti hain:

1. Code repeat hone lagega.
2. Code maintain karna difficult hoga.
3. Ek change se multiple parts affect ho sakte hain.
4. Testing difficult ho sakti hai.
5. New features add karna difficult ho sakta hai.
6. Code tightly coupled ho sakta hai.

Design Patterns in problems ko solve karne ke liye reusable approaches provide karte hain.

## 3. Design Patterns ke Benefits

### 1. Code Reusability

Common solution approach ko multiple places par use kar sakte hain.

### 2. Maintainability

Code ko understand aur modify karna easier ho sakta hai.

### 3. Flexibility

Future mein naye features add karna easier ho sakta hai.

### 4. Loose Coupling

Components ko ek-dusre par unnecessarily dependent hone se bachaya ja sakta hai.

### 5. Better Communication

Developers ek common language use kar sakte hain.

Example:

Agar developer kehta hai ki yahan Factory Pattern use karenge, to experienced developers ko ek general idea mil jata hai ki object creation ko kaise organize karna hai.

### 6. Testability

Properly separated components ko independently test karna easier ho sakta hai.

## 4. Design Patterns kab use karne chahiye?

Har problem mein Design Pattern use karna zaroori nahi hai.

Design Pattern tab use karo jab:

- Problem common aur repeatable ho.
- Code mein unnecessary complexity aa rahi ho.
- Existing design maintain karna difficult ho.
- Future changes expected hon.
- Pattern actual problem ko simplify karta ho.

### Kab use nahi karna chahiye?

- Jab simple solution sufficient ho.
- Jab pattern code ko unnecessarily complex bana raha ho.
- Jab sirf interview ke liye pattern forcefully add kar rahe ho.
- Jab problem ki requirement hi pattern demand nahi karti.

**Golden Rule:** Design Pattern ka purpose code ko better banana hai, code ko complicated banana nahi.

## 5. Types of Design Patterns

Gang of Four (GoF) classification ke according commonly known 23 Design Patterns ko 3 main categories mein divide kiya gaya hai.

1. Creational Design Patterns
2. Structural Design Patterns
3. Behavioral Design Patterns

GoF ka full form hai **Gang of Four**.

Ye Erich Gamma, Richard Helm, Ralph Johnson aur John Vlissides ko refer karta hai, jinhone Design Patterns par famous book likhi thi.

## 6. Creational Design Patterns

Creational Patterns ka focus hota hai:

**Objects create kaise kiye jayen?**

Ye object creation process ko flexible aur manageable banane mein help karte hain.

Common Creational Patterns:

| Pattern          | Purpose                                                                 |
| ---------------- | ----------------------------------------------------------------------- |
| Singleton        | Ek class ka single shared instance                                      |
| Factory Method   | Object creation ko subclasses/creator methods ke through organize karna |
| Abstract Factory | Related objects ki families create karna                                |
| Builder          | Complex objects ko step-by-step construct karna                         |
| Prototype        | Existing object ko clone karke naya object banana                       |

### Simple Example

Maan lo tumhare application mein different types ke payment objects create karne hain:

- UPI Payment
- Card Payment
- Net Banking Payment

Factory approach object creation ko centralize kar sakti hai.

```javascript
function createPayment(type) {
  if (type === "UPI") {
    return { method: "UPI" };
  }

  if (type === "CARD") {
    return { method: "CARD" };
  }

  throw new Error("Invalid payment type");
}

const payment = createPayment("UPI");

console.log(payment);
```

Output:

```text
{ method: 'UPI' }
```

Ye ek simple factory-style example hai, formal GoF Factory Method implementation nahi.

## 7. Structural Design Patterns

Structural Patterns ka focus hota hai:

**Classes aur Objects ko organize aur connect kaise kiya jaye?**

Ye different components ko ek manageable structure mein combine karne mein help karte hain.

Common Structural Patterns:

| Pattern   | Purpose                                                           |
| --------- | ----------------------------------------------------------------- |
| Adapter   | Incompatible interfaces ko compatible banana                      |
| Bridge    | Abstraction ko implementation se separate karna                   |
| Composite | Individual objects aur groups ko tree structure mein treat karna  |
| Decorator | Existing object ko modify kiye bina additional behavior add karna |
| Facade    | Complex subsystem ke liye simple interface provide karna          |
| Flyweight | Shared objects se memory usage reduce karna                       |
| Proxy     | Original object ke access ko control karna                        |

### Simple Example

Maan lo tumhare application mein third-party payment service hai.

Tumhara application ek standard payment interface use karta hai, lekin third-party service ka method alag hai.

Adapter Pattern dono ke beech compatibility provide kar sakta hai.

```javascript
class OldPaymentService {
  makePayment(amount) {
    console.log(`Paid ${amount}`);
  }
}

class PaymentAdapter {
  constructor(oldService) {
    this.oldService = oldService;
  }

  pay(amount) {
    this.oldService.makePayment(amount);
  }
}

const oldService = new OldPaymentService();
const adapter = new PaymentAdapter(oldService);

adapter.pay(500);
```

Output:

```text
Paid 500
```

Ye simplified Adapter example hai.

## 8. Behavioral Design Patterns

Behavioral Patterns ka focus hota hai:

**Objects ek-dusre ke saath communicate aur responsibilities share kaise karenge?**

Ye communication aur behavior ko organize karne mein help karte hain.

Common Behavioral Patterns:

| Pattern                 | Purpose                                                            |
| ----------------------- | ------------------------------------------------------------------ |
| Chain of Responsibility | Request ko handlers ki chain se pass karna                         |
| Command                 | Request ko object ke form mein represent karna                     |
| Interpreter             | Language ya expressions ko interpret karna                         |
| Iterator                | Collection ke elements ko sequentially access karna                |
| Mediator                | Objects ke communication ko centralize karna                       |
| Memento                 | Object ki previous state save aur restore karna                    |
| Observer                | State change hone par subscribers ko notify karna                  |
| State                   | Object ka behavior uski internal state ke according change karna   |
| Strategy                | Different algorithms ko interchangeable banana                     |
| Template Method         | Algorithm ka structure define karna, kuch steps subclasses ko dena |
| Visitor                 | Object structure change kiye bina naye operations add karna        |

### Simple Example

Maan lo tumhari website mein user kisi product ko subscribe karta hai.

Product update hone par subscribed users ko notification send karni hai.

Observer Pattern is tarah ke notification mechanism mein useful ho sakta hai.

```javascript
class Product {
  constructor() {
    this.subscribers = [];
  }

  subscribe(user) {
    this.subscribers.push(user);
  }

  update() {
    this.subscribers.forEach((user) => {
      user.notify("Product updated!");
    });
  }
}

class User {
  notify(message) {
    console.log(message);
  }
}

const product = new Product();
const user = new User();

product.subscribe(user);
product.update();
```

Output:

```text
Product updated!
```

## 9. Three Categories ka Difference

| Creational                  | Structural                   | Behavioral                      |
| --------------------------- | ---------------------------- | ------------------------------- |
| Object creation             | Object/class organization    | Object communication            |
| Objects kaise create honge? | Objects kaise connect honge? | Objects kaise interact karenge? |
| Example: Factory            | Example: Adapter             | Example: Observer               |

Easy trick:

- Creational = Create
- Structural = Structure
- Behavioral = Behavior

## 10. Design Patterns aur SOLID Principles

SOLID aur Design Patterns dono software design ko improve karne mein help karte hain, lekin dono same cheez nahi hain.

### SOLID Principles

SOLID five design principles ka group hai.

- S – Single Responsibility Principle
- O – Open/Closed Principle
- L – Liskov Substitution Principle
- I – Interface Segregation Principle
- D – Dependency Inversion Principle

### Design Patterns

Design Patterns common software problems ke reusable solution approaches hain.

| SOLID                                 | Design Patterns                                   |
| ------------------------------------- | ------------------------------------------------- |
| Design principles hain                | Reusable solution approaches hain                 |
| Good design ke rules guide karte hain | Specific problems ke solutions suggest karte hain |
| Example: SRP                          | Example: Strategy Pattern                         |

Design Patterns implement karte waqt SOLID principles follow karna helpful ho sakta hai.

## 11. Design Pattern vs Algorithm

Dono ko confuse nahi karna chahiye.

| Design Pattern                                  | Algorithm                              |
| ----------------------------------------------- | -------------------------------------- |
| Software design approach                        | Step-by-step computational procedure   |
| Code structure aur object interaction par focus | Problem solve karne ke steps par focus |
| Example: Observer Pattern                       | Example: Binary Search                 |
| Reusable design solution                        | Reusable computational method          |

## 12. Design Patterns ka MERN Stack mein use

MERN application mein bhi Design Patterns ka use hota hai.

### 1. Singleton

Shared database connection manager ya configuration service ke liye useful ho sakta hai.

Note: Node.js module caching aur application architecture ke through bhi shared instance manage kiya ja sakta hai.

### 2. Factory

Different types ke objects ya services create karne ke liye.

Example:

- UPI Payment
- Card Payment
- Net Banking Payment

### 3. Builder

Complex objects ya configuration objects construct karne ke liye.

### 4. Strategy

Different algorithms ko interchangeable banane ke liye.

Example:

- Discount calculation
- Shipping cost calculation
- Payment processing strategies

### 5. Observer

Event-based notification system ke liye.

Example:

- Product update notification
- Order status notification

### 6. Adapter

Third-party APIs ko apne application ke interface ke saath compatible banane ke liye.

### 7. Facade

Complex services ko ek simple interface ke through expose karne ke liye.

**Important:** Express middleware, React hooks, MVC architecture aur Design Patterns related concepts hain, lekin har middleware ya hook automatically GoF Design Pattern nahi hota.

## 13. Design Patterns ke baare mein important facts

1. Design Pattern ready-made code nahi hota.
2. Same pattern different programming languages mein implement ho sakta hai.
3. Pattern ko problem ke according choose karna chahiye.
4. Har project mein sabhi patterns use karna zaroori nahi hai.
5. Design Patterns maintainability improve kar sakte hain.
6. Wrong pattern use karne se unnecessary complexity aa sakti hai.
7. Design Patterns aur SOLID Principles complementary hain.

## 14. Common Mistakes

1. Design Pattern ko framework samajhna.
2. Design Pattern ko library samajhna.
3. Har jagah Singleton use karna.
4. Problem samjhe bina pattern apply karna.
5. SOLID aur Design Patterns ko same samajhna.
6. Creational, Structural aur Behavioral categories confuse karna.
7. Ye sochna ki Design Pattern use karne se code automatically perfect ho jayega.

## 15. Interview Questions & Answers

### Q1. What is a Design Pattern?

Design Pattern ek reusable software design approach hai jo common software design problems ko solve karne mein help karta hai.

### Q2. How many GoF Design Patterns are there?

Gang of Four classification mein 23 commonly recognized Design Patterns hain.

### Q3. What are the three categories of Design Patterns?

1. Creational
2. Structural
3. Behavioral

### Q4. What are Creational Design Patterns?

Ye object creation process ko organize aur manage karte hain.

### Q5. What are Structural Design Patterns?

Ye classes aur objects ko organize aur connect karte hain.

### Q6. What are Behavioral Design Patterns?

Ye objects ke communication aur responsibilities ko organize karte hain.

### Q7. What is the difference between SOLID and Design Patterns?

SOLID design principles hain, jabki Design Patterns common problems ke reusable solution approaches hain.

### Q8. Is Design Pattern language-specific?

Nahi. Same design approach Java, C++, JavaScript aur other programming languages mein implement ki ja sakti hai.

### Q9. Should we use Design Patterns everywhere?

Nahi. Sirf tab use karo jab pattern actual problem solve karta ho aur code ko improve karta ho.

### Q10. What is GoF?

GoF ka full form Gang of Four hai. Ye Design Patterns ki famous book ke four authors ko refer karta hai.

## 16. Practical Tasks

### Task 1: Categories Identify Karo

Neeche diye gaye patterns ki category identify karo:

1. Singleton
2. Factory Method
3. Adapter
4. Observer
5. Strategy
6. Builder
7. Decorator
8. Facade

### Task 2: MERN Examples

Socho tum E-commerce application bana rahe ho.

Identify karo:

1. Database connection ko manage karne ke liye kaunsa pattern useful ho sakta hai?
2. Different payment methods create karne ke liye kaunsa pattern use kar sakte ho?
3. Product update notifications ke liye kaunsa pattern useful hai?
4. Different discount calculation methods ke liye kaunsa pattern useful hai?

### Task 3: Code Practice

Factory-style function create karo jo payment type ke according payment object return kare.

Input:

```javascript
"UPI";
```

Expected output:

```javascript
{
  method: "UPI";
}
```

Invalid payment type par error throw karo.

## 17. Quick Revision

| Topic          | Remember                      |
| -------------- | ----------------------------- |
| Design Pattern | Reusable design approach      |
| GoF            | Gang of Four                  |
| GoF Patterns   | 23                            |
| Creational     | Object creation               |
| Structural     | Object/class organization     |
| Behavioral     | Object communication          |
| Singleton      | Single shared instance        |
| Factory Method | Object creation approach      |
| Adapter        | Interface compatibility       |
| Observer       | Notification on state changes |
| Strategy       | Interchangeable algorithms    |

### Three Golden Rules

- Creational = Object kaise banega?
- Structural = Objects kaise organize honge?
- Behavioral = Objects kaise communicate karenge?

## 18. Topic Completion Checklist

- [ ] Design Pattern ka meaning samajh liya.
- [ ] Design Patterns ki zaroorat samajh li.
- [ ] Benefits aur limitations samajh li.
- [ ] GoF classification samajh li.
- [ ] Creational Patterns samajh liye.
- [ ] Structural Patterns samajh liye.
- [ ] Behavioral Patterns samajh liye.
- [ ] SOLID aur Design Patterns ka difference samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Practical tasks complete kar liye.
- [ ] Interview questions revise kar liye.

**Topic 19 Complete: Introduction to Design Patterns**
