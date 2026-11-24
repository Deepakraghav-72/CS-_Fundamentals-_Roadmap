# 21. Factory Pattern

## 1. Factory Pattern kya hota hai?

Factory Pattern ek **Creational Design Pattern** hai.

Iska main purpose object creation ko organize karna hai, taaki client code ko har baar directly `new` use karke objects create na karne padein.

Simple language mein:

**Factory Pattern ek central method ya class provide karta hai jo requirement ke according objects create karke return karti hai.**

### Real-life Example

Maan lo tum ek car showroom mein jaate ho.

Tumhe car chahiye. Tum showroom ko batate ho ki tumhe kaunsi car chahiye.

Showroom tumhari requirement ke according car provide karta hai.

Tumhe car banane ki internal process jaanne ki zaroorat nahi hoti.

Software development mein Factory Pattern bhi isi tarah kaam karta hai.

Tum Factory ko batate ho ki kaunsa object chahiye aur Factory us object ko create karke return karti hai.

## 2. Factory Pattern ki zaroorat kyon padti hai?

Maan lo tum ek E-commerce application bana rahe ho.

Tumhare application mein different payment methods hain:

- UPI Payment
- Card Payment
- Net Banking Payment

Without Factory Pattern:

```javascript
let payment;

if (type === "UPI") {
  payment = new UpiPayment();
} else if (type === "CARD") {
  payment = new CardPayment();
} else if (type === "NETBANKING") {
  payment = new NetBankingPayment();
}
```

Agar tumhare application mein payment methods badhte jayenge, to object creation ka code multiple places par repeat ho sakta hai.

Factory Pattern object creation ko ek central place par organize kar sakta hai.

## 3. Factory Pattern ka Basic Working

Factory Pattern mein generally ye steps hote hain:

1. Client Factory ko request deta hai.
2. Factory requirement check karti hai.
3. Factory required object create karti hai.
4. Factory created object client ko return karti hai.
5. Client returned object use karta hai.

Diagram:

```text
        Client
           |
           | Request
           v
         Factory
           |
      Select Object
        /      \
       v        v
   UPI Object  Card Object
       \        /
        \      /
         Return
           |
           v
         Client
```

## 4. Simple Factory Example in JavaScript

Maan lo humein different types ke payment objects create karne hain.

### Step 1: Payment Classes

```javascript
class UpiPayment {
  pay(amount) {
    console.log(`Paid ${amount} using UPI`);
  }
}

class CardPayment {
  pay(amount) {
    console.log(`Paid ${amount} using Card`);
  }
}

class NetBankingPayment {
  pay(amount) {
    console.log(`Paid ${amount} using Net Banking`);
  }
}
```

Yahan three different classes hain.

Har class ke andar `pay()` method hai.

### Step 2: Create Factory

```javascript
class PaymentFactory {
  static createPayment(type) {
    if (type === "UPI") {
      return new UpiPayment();
    }

    if (type === "CARD") {
      return new CardPayment();
    }

    if (type === "NETBANKING") {
      return new NetBankingPayment();
    }

    throw new Error("Invalid Payment Type");
  }
}
```

Factory decide karti hai ki kaunsa object create karna hai.

### Step 3: Use Factory

```javascript
const payment = PaymentFactory.createPayment("UPI");

payment.pay(500);
```

Output:

```text
Paid 500 using UPI
```

### Step-by-step Explanation

1. `PaymentFactory.createPayment("UPI")` call hota hai.
2. Factory `"UPI"` condition check karti hai.
3. `new UpiPayment()` execute hota hai.
4. UpiPayment object return hota hai.
5. `payment.pay(500)` execute hota hai.

## 5. Factory Pattern ke Main Components

Simple Factory-style implementation mein generally:

### 1. Product

Product wo common object type ya interface hota hai jise client use karta hai.

Example: Payment.

### 2. Concrete Products

Ye actual implementations hoti hain.

Example:

- UpiPayment
- CardPayment
- NetBankingPayment

### 3. Factory

Factory object create karne ka decision leti hai.

Example: PaymentFactory.

### 4. Client

Client Factory se object request karta hai aur returned object use karta hai.

Example: OrderService.

**Note:** Ye simple factory structure hai. Formal GoF Factory Method Pattern mein Creator aur Concrete Creator classes bhi important hoti hain.

## 6. Simple Factory vs Factory Method Pattern

Ye dono concepts related hain, lekin exactly same nahi hain.

### Simple Factory

Simple Factory ek common programming technique hai jahan ek factory method conditions ke basis par objects create karta hai.

Example:

```javascript
class NotificationFactory {
  static create(type) {
    if (type === "EMAIL") {
      return new EmailNotification();
    }

    if (type === "SMS") {
      return new SmsNotification();
    }

    throw new Error("Invalid Type");
  }
}
```

### Factory Method Pattern

Factory Method ek formal GoF Creational Pattern hai.

Ismein ek Creator class factory method declare karti hai, aur subclasses us method ko override karke decide karti hain ki kaunsa concrete product create hoga.

### Example

```javascript
class Notification {
  send(message) {
    throw new Error("send() must be implemented");
  }
}

class EmailNotification extends Notification {
  send(message) {
    console.log(`Email: ${message}`);
  }
}

class SmsNotification extends Notification {
  send(message) {
    console.log(`SMS: ${message}`);
  }
}

class NotificationCreator {
  createNotification() {
    throw new Error("Must be implemented");
  }

  notify(message) {
    const notification = this.createNotification();
    notification.send(message);
  }
}

class EmailCreator extends NotificationCreator {
  createNotification() {
    return new EmailNotification();
  }
}

class SmsCreator extends NotificationCreator {
  createNotification() {
    return new SmsNotification();
  }
}

const creator = new EmailCreator();

creator.notify("Welcome!");
```

Output:

```text
Email: Welcome!
```

### Difference

| Simple Factory                                      | Factory Method                            |
| --------------------------------------------------- | ----------------------------------------- |
| Common creation method                              | Creator hierarchy with factory method     |
| Conditions se object select ho sakta hai            | Subclasses decide karti hain product      |
| GoF ke 23 patterns mein separate named pattern nahi | GoF Creational Pattern hai                |
| Simple object creation ke liye useful               | Extensible object creation ke liye useful |

## 7. Factory Pattern vs Constructor

| Factory                                         | Constructor                                         |
| ----------------------------------------------- | --------------------------------------------------- |
| Object creation ko centralize kar sakta hai     | Class ka instance create karta hai                  |
| Different types ke objects return kar sakta hai | Usually apni class ka instance initialize karta hai |
| Internal creation details hide kar sakta hai    | Object initialization handle karta hai              |
| Example: PaymentFactory                         | Example: new User()                                 |

## 8. Factory Pattern ke Advantages

### 1. Centralized Object Creation

Object creation ek central place par manage hota hai.

### 2. Loose Coupling

Client code concrete classes par directly depend karne se bach sakta hai.

### 3. Easy Maintenance

Object creation mein changes ek central location par manage kar sakte hain.

### 4. Flexibility

Requirement ke according different objects create kar sakte hain.

### 5. Code Reusability

Same factory ko multiple parts mein reuse kar sakte hain.

### 6. Better Testing

Factory aur products ko separately test karna easier ho sakta hai.

## 9. Factory Pattern ke Disadvantages

### 1. Extra Classes

Factory ke liye additional classes ya methods banane pad sakte hain.

### 2. Complexity

Simple object creation ke liye Factory Pattern unnecessary complexity create kar sakta hai.

### 3. Maintenance

Bahut saare conditions hone par simple factory ka code large ho sakta hai.

### 4. New Product Support

Simple factory mein naya product add karne ke liye factory code modify karna pad sakta hai.

Factory Method jaise approaches is problem ko different tarike se handle kar sakte hain.

## 10. MERN Stack mein Factory Pattern

MERN Stack mein Factory Pattern ka use different objects ya services create karne ke liye kar sakte hain.

### Example 1: Payment Factory

```javascript
class UpiPayment {
  process(amount) {
    console.log("UPI payment:", amount);
  }
}

class CardPayment {
  process(amount) {
    console.log("Card payment:", amount);
  }
}

function createPayment(type) {
  switch (type) {
    case "UPI":
      return new UpiPayment();

    case "CARD":
      return new CardPayment();

    default:
      throw new Error("Unsupported payment method");
  }
}

const payment = createPayment("CARD");

payment.process(1000);
```

Output:

```text
Card payment: 1000
```

### Example 2: Notification Factory

```javascript
class EmailNotification {
  send(message) {
    console.log("Email:", message);
  }
}

class SmsNotification {
  send(message) {
    console.log("SMS:", message);
  }
}

function createNotification(type) {
  if (type === "EMAIL") {
    return new EmailNotification();
  }

  if (type === "SMS") {
    return new SmsNotification();
  }

  throw new Error("Invalid notification type");
}

const notification = createNotification("EMAIL");

notification.send("Your order is confirmed");
```

Output:

```text
Email: Your order is confirmed
```

### Example 3: Database Adapter Factory

Maan lo application different database providers ke saath work kar sakta hai.

Factory requirement ke according database adapter create kar sakti hai.

```javascript
function createDatabase(type) {
  if (type === "MONGODB") {
    return new MongoDatabase();
  }

  if (type === "POSTGRESQL") {
    return new PostgresDatabase();
  }

  throw new Error("Unsupported database");
}
```

Ye conceptual example hai. Actual classes aur database connection logic separately implement karna hoga.

## 11. Factory Pattern kab use karna chahiye?

Factory Pattern use karo jab:

1. Different types ke objects create karne hon.
2. Object creation logic complex ho.
3. Client ko concrete classes ki details hide karni hon.
4. Future mein new product types add hone ki possibility ho.
5. Centralized object creation useful ho.

### Kab avoid karna chahiye?

1. Jab sirf ek simple object create karna ho.
2. Jab factory unnecessary complexity create kare.
3. Jab object creation logic already simple aur manageable ho.

## 12. Common Mistakes

1. Simple Factory aur Factory Method ko exactly same samajhna.
2. Har object ke liye Factory create kar dena.
3. Factory ko business logic ka complete replacement samajhna.
4. Invalid input handle na karna.
5. Concrete product classes ko unnecessary expose karna.
6. Factory Pattern ko Singleton Pattern samajhna.

## 13. Factory vs Singleton

| Factory                                        | Singleton                                 |
| ---------------------------------------------- | ----------------------------------------- |
| Object creation organize karta hai             | Single shared instance maintain karta hai |
| Multiple types ke objects create kar sakta hai | Same instance return karta hai            |
| Creational Pattern                             | Creational Pattern                        |
| Example: PaymentFactory                        | Example: ConfigManager                    |

## 14. Interview Questions & Answers

### Q1. What is Factory Pattern?

Factory Pattern ek Creational Design Pattern hai jo object creation ko organize karta hai aur client ko creation details se decouple kar sakta hai.

### Q2. Why do we use Factory Pattern?

Different objects ko centrally create karne aur client code ko concrete creation logic se separate rakhne ke liye.

### Q3. Is Factory a Creational Pattern?

Yes, Factory Method Creational Design Pattern hai.

### Q4. What is a Simple Factory?

Simple Factory ek method ya function hota hai jo input ke according different object types create karke return karta hai.

### Q5. What is Factory Method Pattern?

Factory Method mein Creator ek factory method define karta hai aur subclasses decide karti hain ki kaunsa concrete object create karna hai.

### Q6. What is the difference between Factory and Singleton?

Factory ka focus object creation organize karna hai, jabki Singleton ka focus single shared instance maintain karna hai.

### Q7. Can Factory create multiple object types?

Yes. Factory requirement ke according different concrete object types create kar sakti hai.

### Q8. What is the main advantage of Factory?

Object creation ko centralize karke client aur concrete classes ke beech coupling reduce karna.

### Q9. Is Factory Pattern always necessary?

No. Simple requirements ke liye direct object creation sufficient ho sakta hai.

### Q10. Give a real-world example of Factory Pattern.

Payment Factory jo UPI, Card aur Net Banking payment objects create karti hai.

## 15. Practical Tasks

### Task 1: Shape Factory

Three classes banao:

- Circle
- Rectangle
- Square

Ek `ShapeFactory` banao jo input ke according object return kare.

Example:

```javascript
const shape = ShapeFactory.create("CIRCLE");
```

Expected output:

```text
Circle object created
```

### Task 2: Notification Factory

Notification factory banao jo:

- EMAIL
- SMS
- PUSH

ke according notification object return kare.

Har object mein `send()` method hona chahiye.

### Task 3: Payment Factory

UPI aur Card Payment classes banao.

Factory input ke according object return kare.

Invalid payment type par proper error throw karo.

## 16. Quick Revision

| Term             | Meaning                            |
| ---------------- | ---------------------------------- |
| Factory Pattern  | Object creation organize karna     |
| Category         | Creational                         |
| Factory          | Object create karne wala component |
| Product          | Common object type                 |
| Concrete Product | Actual implementation              |
| Client           | Factory se object use karne wala   |
| Simple Factory   | Central conditional creation       |
| Factory Method   | Subclasses decide product creation |

### Remember These Points

- Factory Pattern ek Creational Pattern hai.
- Object creation logic ko centralize karta hai.
- Client ko concrete object creation details se separate kar sakta hai.
- Simple Factory aur Factory Method same nahi hain.
- Factory Method GoF ke 23 patterns mein included hai.
- Har jagah Factory use karna zaroori nahi hai.

## 17. Topic Completion Checklist

- [ ] Factory Pattern ka meaning samajh liya.
- [ ] Factory ki need samajh li.
- [ ] Factory ka working flow samajh liya.
- [ ] Simple Factory ka code samajh liya.
- [ ] Factory Method Pattern samajh liya.
- [ ] Simple Factory vs Factory Method samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Advantages aur disadvantages samajh liye.
- [ ] Singleton vs Factory difference samajh liya.
- [ ] Interview questions revise kar liye.
- [ ] Practical tasks complete kar liye.

**Topic 21 Complete: Factory Pattern**
