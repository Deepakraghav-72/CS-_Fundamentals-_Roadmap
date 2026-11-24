# 15. Dependency Inversion Principle (DIP)

## 1. DIP Kya Hai?

DIP ka full form hai **Dependency Inversion Principle**.

Ye SOLID principles ka fifth aur last principle hai.

Is principle ko Robert C. Martin ne popularize kiya tha.

### Simple Definition

High-level modules aur low-level modules dono ko abstractions par depend karna chahiye, na ki high-level modules ko directly low-level modules par.

Simple words mein:

**Ek class ko doosri class ki concrete implementation par directly dependent nahi hona chahiye. Dono ko ek common abstraction par depend karna chahiye.**

### Pehle 3 Terms Samjho

#### 1. High-Level Module

Jo application ka main business logic ya important work handle karta hai.

Example:

- OrderService
- PaymentService
- UserService

#### 2. Low-Level Module

Jo actual implementation ya technical work karta hai.

Example:

- MongoDB database connection
- Email service
- Payment gateway
- File storage

#### 3. Abstraction

Abstraction ek common contract hota hai jo batata hai ki kya functionality available honi chahiye, bina ye bataye ki uska implementation kaise hoga.

Example:

- PaymentGateway
- NotificationService
- UserRepository

---

## 2. DIP Ko Simple Example Se Samjho

Maan lo ek E-commerce application hai.

Customer order place karta hai aur payment hoti hai.

Humare paas do classes hain:

- OrderService
- RazorpayPayment

### Wrong Design

```javascript
class RazorpayPayment {
  pay(amount) {
    console.log(`Paid ${amount} using Razorpay`);
  }
}

class OrderService {
  constructor() {
    this.payment = new RazorpayPayment();
  }

  placeOrder(amount) {
    this.payment.pay(amount);
  }
}

const order = new OrderService();

order.placeOrder(500);
```

Output:

```text
Paid 500 using Razorpay
```

Code kaam kar raha hai, lekin problem kya hai?

`OrderService` directly `RazorpayPayment` par dependent hai.

Agar future mein Stripe use karna ho, toh OrderService ke code mein changes karne pad sakte hain.

Yani high-level business logic ek specific payment implementation par dependent hai.

Ye tight coupling hai.

---

## 3. DIP Follow Karne Ka Correct Way

Hum ek common abstraction banayenge.

Ab OrderService ko ye nahi pata hoga ki payment Razorpay se ho rahi hai ya Stripe se.

Usse sirf itna pata hoga ki payment object mein `pay()` method available hai.

### Correct Design

```javascript
class RazorpayPayment {
  pay(amount) {
    console.log(`Paid ${amount} using Razorpay`);
  }
}

class StripePayment {
  pay(amount) {
    console.log(`Paid ${amount} using Stripe`);
  }
}

class OrderService {
  constructor(payment) {
    this.payment = payment;
  }

  placeOrder(amount) {
    this.payment.pay(amount);
  }
}

const razorpay = new RazorpayPayment();

const order = new OrderService(razorpay);

order.placeOrder(500);
```

Output:

```text
Paid 500 using Razorpay
```

Ab Stripe use karna ho:

```javascript
const stripe = new StripePayment();

const order = new OrderService(stripe);

order.placeOrder(500);
```

Output:

```text
Paid 500 using Stripe
```

Ab OrderService ke andar Razorpay ya Stripe ka object create nahi ho raha.

Payment dependency bahar se inject ho rahi hai.

Isse OrderService ki flexibility badh gayi.

**Important:** JavaScript example mein common contract ko method convention se represent kiya gaya hai. TypeScript mein formal interface define karke is contract ko aur clearly enforce kar sakte hain.

---

## 4. DIP Ka Main Rule

DIP ke do important rules hain:

### Rule 1

High-level modules should not depend on low-level modules. Both should depend on abstractions.

Meaning:

High-level module ko directly low-level implementation par depend nahi hona chahiye.

Dono ko abstraction par depend karna chahiye.

### Rule 2

Abstractions should not depend on details. Details should depend on abstractions.

Meaning:

Common abstraction ko kisi particular implementation ke according design nahi karna chahiye.

Instead, actual implementations ko abstraction ke according design karna chahiye.

### Diagram

Wrong Design:

```text
OrderService
     |
     v
RazorpayPayment
```

Correct Design:

```text
      OrderService
            |
            v
      PaymentGateway
            ^
            |
     ----------------
     |              |
  Razorpay        Stripe
```

Yahan:

- OrderService abstraction use karta hai.
- Razorpay abstraction implement karta hai.
- Stripe abstraction implement karta hai.

---

## 5. Dependency Injection Kya Hai?

DIP samajhne ke liye Dependency Injection (DI) samajhna bahut zaroori hai.

### Simple Definition

Dependency Injection ek technique hai jisme kisi class ki required dependency uske andar create karne ke bajaye bahar se provide ki jaati hai.

Example:

Wrong:

```javascript
class OrderService {
  constructor() {
    this.payment = new RazorpayPayment();
  }
}
```

Correct:

```javascript
class OrderService {
  constructor(payment) {
    this.payment = payment;
  }
}

const payment = new RazorpayPayment();

const order = new OrderService(payment);
```

Yahan `payment` dependency constructor ke through inject ho rahi hai.

### Dependency Injection Ke Common Types

#### 1. Constructor Injection

Dependency constructor ke through provide hoti hai.

```javascript
class UserService {
  constructor(database) {
    this.database = database;
  }
}
```

#### 2. Setter Injection

Dependency ko setter method ke through provide kiya jata hai.

```javascript
class UserService {
  setDatabase(database) {
    this.database = database;
  }
}

const userService = new UserService();

userService.setDatabase(database);
```

#### 3. Method Injection

Dependency kisi particular method ko argument ke roop mein provide hoti hai.

```javascript
class NotificationService {
  send(message, emailProvider) {
    emailProvider.send(message);
  }
}
```

---

## 6. DIP vs Dependency Injection

Dono related hain, lekin same nahi hain.

| DIP                                                                    | Dependency Injection                            |
| ---------------------------------------------------------------------- | ----------------------------------------------- |
| SOLID design principle hai.                                            | Design technique/pattern hai.                   |
| Dependencies ko abstractions par depend karne ke liye guide karta hai. | Dependencies bahar se provide karti hai.        |
| Architecture aur design ka rule hai.                                   | Us design ko implement karne ka ek tareeka hai. |
| Dependency direction ko control karta hai.                             | Dependency provide karne ka mechanism deta hai. |

**Yaad rakho:** Dependency Injection use karne se automatically DIP follow nahi hota. Dependency ko abstraction ke through design karna bhi zaroori hai.

---

## 7. DIP in TypeScript

TypeScript mein interfaces ke through DIP clearly implement kar sakte hain.

### Step 1: Interface Banao

```typescript
interface PaymentGateway {
  pay(amount: number): void;
}
```

### Step 2: Implementations Banao

```typescript
class RazorpayPayment implements PaymentGateway {
  pay(amount: number): void {
    console.log(`Paid ${amount} using Razorpay`);
  }
}

class StripePayment implements PaymentGateway {
  pay(amount: number): void {
    console.log(`Paid ${amount} using Stripe`);
  }
}
```

### Step 3: High-Level Module Banao

```typescript
class OrderService {
  constructor(private payment: PaymentGateway) {}

  placeOrder(amount: number): void {
    this.payment.pay(amount);
  }
}
```

### Step 4: Dependency Inject Karo

```typescript
const payment = new RazorpayPayment();

const order = new OrderService(payment);

order.placeOrder(500);
```

Output:

```text
Paid 500 using Razorpay
```

Agar Stripe use karna hai:

```typescript
const payment = new StripePayment();

const order = new OrderService(payment);

order.placeOrder(500);
```

OrderService ko change karne ki zaroorat nahi hai.

---

## 8. DIP in C++

C++ mein abstract class aur constructor injection se DIP implement kar sakte hain.

```cpp
#include <iostream>
using namespace std;

class PaymentGateway {
public:
    virtual void pay(double amount) = 0;

    virtual ~PaymentGateway() = default;
};

class RazorpayPayment : public PaymentGateway {
public:
    void pay(double amount) override {
        cout << "Paid " << amount << " using Razorpay" << endl;
    }
};

class StripePayment : public PaymentGateway {
public:
    void pay(double amount) override {
        cout << "Paid " << amount << " using Stripe" << endl;
    }
};

class OrderService {
private:
    PaymentGateway& payment;

public:
    OrderService(PaymentGateway& p) : payment(p) {}

    void placeOrder(double amount) {
        payment.pay(amount);
    }
};

int main() {
    RazorpayPayment razorpay;

    OrderService order(razorpay);

    order.placeOrder(500);

    return 0;
}
```

Output:

```text
Paid 500 using Razorpay
```

### Explanation

- PaymentGateway abstract class hai.
- RazorpayPayment uska implementation hai.
- OrderService PaymentGateway par depend karta hai.
- Constructor ke through payment dependency inject hoti hai.
- OrderService ko specific payment provider ki knowledge nahi hai.

---

## 9. DIP in MERN Stack

MERN applications mein DIP ka use bahut practical hai.

Example: MongoDB database.

Maan lo ek UserService hai jo users ko database mein save karta hai.

### Wrong Design

```javascript
class MongoUserRepository {
  async save(user) {
    console.log("User saved in MongoDB");
  }
}

class UserService {
  constructor() {
    this.repository = new MongoUserRepository();
  }

  async createUser(user) {
    await this.repository.save(user);
  }
}
```

Problem:

UserService directly MongoUserRepository par dependent hai.

Agar future mein PostgreSQL ya kisi doosre database par switch karna ho, toh UserService ko modify karna pad sakta hai.

### Better Design

Pehle repository contract define karo:

```typescript
interface UserRepository {
  save(user: { name: string }): Promise<void>;
}
```

MongoDB implementation:

```typescript
class MongoUserRepository implements UserRepository {
  async save(user: { name: string }): Promise<void> {
    console.log("User saved in MongoDB");
  }
}
```

PostgreSQL implementation:

```typescript
class PostgresUserRepository implements UserRepository {
  async save(user: { name: string }): Promise<void> {
    console.log("User saved in PostgreSQL");
  }
}
```

High-level service:

```typescript
class UserService {
  constructor(private repository: UserRepository) {}

  async createUser(user: { name: string }): Promise<void> {
    await this.repository.save(user);
  }
}
```

Dependency injection:

```typescript
const repository = new MongoUserRepository();

const userService = new UserService(repository);

userService.createUser({ name: "Rahul" });
```

Ab database implementation change karne ke liye:

```typescript
const repository = new PostgresUserRepository();

const userService = new UserService(repository);

userService.createUser({ name: "Rahul" });
```

UserService same rahegi.

**Real MERN project mein:** Repository, service aur controller layers ko properly separate karke DIP ka benefit le sakte ho.

---

## 10. DIP Ke Advantages

1. Tight coupling kam hoti hai.
2. Code flexible banta hai.
3. Testing easy hoti hai.
4. Implementations replace karna easy hota hai.
5. Code maintainable banta hai.
6. Business logic technical implementation se independent rehta hai.
7. Mock dependencies use karke unit testing kar sakte hain.

## 11. DIP Follow Na Karne Ke Disadvantages

1. High-level classes specific implementations par dependent ho jaati hain.
2. Technology change karna difficult ho sakta hai.
3. Testing mein real dependencies ki zaroorat pad sakti hai.
4. Code tightly coupled ho sakta hai.
5. Reusability kam ho sakti hai.

---

## 12. Common Mistakes

| Mistake                                                | Correct Approach                       |
| ------------------------------------------------------ | -------------------------------------- |
| Class ke andar concrete dependency create karna        | Dependency inject karo                 |
| High-level module ko specific database se couple karna | Repository abstraction use karo        |
| DIP aur DI ko same samajhna                            | Dono ka difference samjho              |
| Har jagah interfaces banana                            | Meaningful abstractions banao          |
| Dependency injection ko hi complete DIP samajhna       | Dependency direction bhi correct rakho |
| Abstraction ko implementation-specific banana          | General contract define karo           |

---

## 13. SOLID Principles – Complete Revision

Ab humne SOLID ke saare 5 principles complete kar liye hain.

| Principle | Full Form                       | Main Rule                                           |
| --------- | ------------------------------- | --------------------------------------------------- |
| S         | Single Responsibility Principle | Class ki ek responsibility honi chahiye             |
| O         | Open/Closed Principle           | Extension ke liye open, modification ke liye closed |
| L         | Liskov Substitution Principle   | Child parent ki jagah safely use ho                 |
| I         | Interface Segregation Principle | Unnecessary methods par depend na karo              |
| D         | Dependency Inversion Principle  | Abstractions par depend karo                        |

### Easy Memory Trick

- S = Single Responsibility
- O = Open for extension
- L = Liskov Substitution
- I = Interface Segregation
- D = Dependency Inversion

---

## 14. Interview Questions and Answers

### Q1. What is DIP?

High-level aur low-level modules dono abstractions par depend karne chahiye, concrete implementations par nahi.

### Q2. DIP SOLID ka kaunsa principle hai?

Fifth aur last principle.

### Q3. What is a high-level module?

Jo main business logic handle karta hai, jaise OrderService.

### Q4. What is a low-level module?

Jo actual technical implementation deta hai, jaise MongoDB repository ya payment provider.

### Q5. What is an abstraction?

Ek common contract jo functionality define karta hai, implementation details nahi.

### Q6. What is Dependency Injection?

Kisi class ko required dependency bahar se provide karna.

### Q7. Are DIP and DI the same?

Nahi. DIP ek design principle hai aur DI ek technique hai.

### Q8. How does DIP help in testing?

Mock ya fake dependency inject karke class ko independently test kar sakte hain.

### Q9. How is DIP useful in MERN?

Database repositories, payment services, email services aur other integrations ko loosely coupled rakhne mein.

### Q10. What is tight coupling?

Jab ek class doosri specific class ya implementation par strongly dependent ho.

---

## 15. Practice Tasks

### Task 1: Payment System

- PaymentGateway abstraction banao.
- RazorpayPayment implementation banao.
- StripePayment implementation banao.
- OrderService banao.
- Constructor injection use karo.

### Task 2: Database System

- UserRepository interface banao.
- MongoUserRepository banao.
- PostgresUserRepository banao.
- UserService ko repository inject karo.

### Task 3: Notification System

- NotificationProvider abstraction banao.
- EmailNotification banao.
- SMSNotification banao.
- NotificationService ko dependency inject karo.

---

## 16. Quick Revision

- DIP = Dependency Inversion Principle.
- SOLID ka fifth principle.
- High-level aur low-level modules abstractions par depend karte hain.
- Concrete implementation par direct dependency avoid karo.
- Dependency Injection ek technique hai.
- Constructor Injection commonly use hoti hai.
- DIP tight coupling kam karta hai.
- Testing aur maintenance easy hoti hai.
- MERN mein repositories aur services ke through apply kar sakte ho.

---

## 17. Topic Completion Checklist

- [ ] DIP ka meaning samajh aa gaya.
- [ ] High-level aur low-level modules samajh aa gaye.
- [ ] Abstraction samajh aa gayi.
- [ ] Wrong vs Correct design samajh aa gaya.
- [ ] Dependency Injection samajh aa gayi.
- [ ] DIP vs DI ka difference samajh aa gaya.
- [ ] TypeScript example samajh aa gaya.
- [ ] C++ example samajh aa gaya.
- [ ] MERN example samajh aa gaya.
- [ ] SOLID ke saare 5 principles revise kar liye.

**Topic 15 Complete: Dependency Inversion Principle (DIP).**
