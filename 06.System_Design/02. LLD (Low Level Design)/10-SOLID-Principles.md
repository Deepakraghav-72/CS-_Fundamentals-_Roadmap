# Introduction to SOLID Principles

## 1. What are SOLID Principles?

SOLID five important object-oriented design principles ka collection hai.

In principles ka purpose hai code ko:

- Easy to understand banana.
- Easy to maintain banana.
- Reusable banana.
- Flexible banana.
- Changes ke liye easy banana.
- Unnecessary dependencies se bachana.

SOLID ka use mainly LLD (Low Level Design) mein hota hai.

### SOLID ka full form

| Letter | Principle                       | Simple Meaning                                      |
| ------ | ------------------------------- | --------------------------------------------------- |
| S      | Single Responsibility Principle | Ek class ka ek main responsibility                  |
| O      | Open/Closed Principle           | Extension ke liye open, modification ke liye closed |
| L      | Liskov Substitution Principle   | Child class parent ki jagah kaam kar sake           |
| I      | Interface Segregation Principle | Chhote, specific interfaces                         |
| D      | Dependency Inversion Principle  | High-level code abstractions par depend kare        |

**Important:** SOLID ka matlab ye nahi ki har class mein sirf ek method hona chahiye. Iska matlab hai ki class ki responsibilities logically focused honi chahiye.

---

## 2. Why do we need SOLID Principles?

Maan lo hum ek e-commerce application bana rahe hain.

Initially code simple hota hai:

```javascript
class Order {
  createOrder() {
    console.log("Order created");
  }

  sendEmail() {
    console.log("Email sent");
  }

  generateInvoice() {
    console.log("Invoice generated");
  }
}
```

Is class mein multiple responsibilities hain:

- Order create karna.
- Email bhejna.
- Invoice generate karna.

Aage chal kar agar email system change hota hai, toh Order class bhi modify karni pad sakti hai.

Bade project mein aise code ko maintain karna difficult ho sakta hai.

SOLID principles isi tarah ke design problems ko reduce karne mein help karte hain.

---

## 3. S – Single Responsibility Principle (SRP)

### Definition

A class should have one reason to change.

Simple language:

Ek class ki ek focused responsibility honi chahiye.

### Wrong Example

```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  saveUser() {
    console.log("User saved");
  }

  sendEmail() {
    console.log("Email sent");
  }

  generateReport() {
    console.log("Report generated");
  }
}
```

Problems:

- User data manage karna.
- Database mein save karna.
- Email bhejna.
- Report generate karna.

Sab ek class mein aa gaye.

### Correct Example

```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
}

class UserRepository {
  saveUser(user) {
    console.log("User saved:", user.name);
  }
}

class EmailService {
  sendEmail(user) {
    console.log("Email sent to:", user.email);
  }
}

const user = new User("Rahul", "rahul@example.com");

const repository = new UserRepository();
const emailService = new EmailService();

repository.saveUser(user);
emailService.sendEmail(user);
```

**Output:**

```text
User saved: Rahul
Email sent to: rahul@example.com
```

Ab har class ki responsibility focused hai.

### Benefits

- Code easy to maintain hota hai.
- Testing easy hoti hai.
- Changes ka impact limited rehta hai.
- Classes reusable hoti hain.

### Yaad rakho

SRP = One class, one focused responsibility.

---

## 4. O – Open/Closed Principle (OCP)

### Definition

Software entities should be open for extension but closed for modification.

Simple language:

Existing working code ko baar-baar modify karne ke bajaye naye features add karne ka flexible tareeka hona chahiye.

### Wrong Example

```javascript
class Payment {
  pay(type, amount) {
    if (type === "UPI") {
      console.log("Paid using UPI:", amount);
    } else if (type === "CARD") {
      console.log("Paid using Card:", amount);
    }
  }
}

const payment = new Payment();

payment.pay("UPI", 500);
```

Problem:

Agar future mein Net Banking add karni ho, toh isi class mein naye conditions add karne padenge.

### Correct Example

```javascript
class UPI {
  pay(amount) {
    console.log("UPI payment:", amount);
  }
}

class Card {
  pay(amount) {
    console.log("Card payment:", amount);
  }
}

class NetBanking {
  pay(amount) {
    console.log("Net Banking payment:", amount);
  }
}

function checkout(paymentMethod, amount) {
  paymentMethod.pay(amount);
}

checkout(new UPI(), 500);
checkout(new Card(), 1000);
checkout(new NetBanking(), 1500);
```

**Output:**

```text
UPI payment: 500
Card payment: 1000
Net Banking payment: 1500
```

Ab naya payment method add karne ke liye existing checkout function modify nahi karna pada.

### Benefits

- New features add karna easy.
- Existing code mein changes kam.
- Bugs introduce hone ka risk kam ho sakta hai.
- Code flexible hota hai.

### Yaad rakho

OCP = Extend behavior without unnecessarily modifying stable existing code.

---

## 5. L – Liskov Substitution Principle (LSP)

### Definition

Objects of a parent class should be replaceable with objects of its child classes without breaking the expected behavior of the program.

Simple language:

Agar child class parent class ko inherit karti hai, toh child object ko parent ki jagah use karne par program ka expected behavior break nahi hona chahiye.

### Wrong Example

```javascript
class Bird {
  fly() {
    console.log("Bird is flying");
  }
}

class Sparrow extends Bird {
  fly() {
    console.log("Sparrow is flying");
  }
}

class Penguin extends Bird {
  fly() {
    throw new Error("Penguin cannot fly");
  }
}
```

Problem:

Penguin ek Bird hai, lekin woh fly nahi kar sakta.

Agar program har Bird se fly karne ki expectation rakhega, toh Penguin ke case mein error aa jayega.

### Better Design

```javascript
class Bird {
  eat() {
    console.log("Bird is eating");
  }
}

class FlyingBird extends Bird {
  fly() {
    console.log("Bird is flying");
  }
}

class Sparrow extends FlyingBird {}

class Penguin extends Bird {}

const sparrow = new Sparrow();
const penguin = new Penguin();

sparrow.fly();
penguin.eat();
```

**Output:**

```text
Bird is flying
Bird is eating
```

Ab sirf flying birds ko `fly()` behavior diya gaya hai.

### Benefits

- Inheritance ka correct use hota hai.
- Unexpected errors reduce hote hain.
- Parent-child relationship meaningful hoti hai.
- Code reliable banta hai.

### Yaad rakho

LSP = Child class ko parent ki jagah use karne par expected behavior nahi tootna chahiye.

---

## 6. I – Interface Segregation Principle (ISP)

### Definition

Clients should not be forced to depend on methods they do not use.

Simple language:

Kisi class ko aise methods implement karne ke liye force mat karo jinki usse zaroorat hi nahi hai.

### Wrong Example

```javascript
class Machine {
  print() {}
  scan() {}
  fax() {}
}

class SimplePrinter extends Machine {
  print() {
    console.log("Printing...");
  }

  scan() {
    throw new Error("Scan not supported");
  }

  fax() {
    throw new Error("Fax not supported");
  }
}
```

Problem:

SimplePrinter ko scan aur fax methods implement karne pad rahe hain, jabki usmein ye features hain hi nahi.

### Correct Example

```javascript
class Printer {
  print() {
    console.log("Printing...");
  }
}

class Scanner {
  scan() {
    console.log("Scanning...");
  }
}

class AllInOnePrinter {
  constructor() {
    this.printer = new Printer();
    this.scanner = new Scanner();
  }

  print() {
    this.printer.print();
  }

  scan() {
    this.scanner.scan();
  }
}

const printer = new Printer();
const allInOne = new AllInOnePrinter();

printer.print();
allInOne.scan();
```

**Output:**

```text
Printing...
Scanning...
```

Ab simple printer ko scanning ya faxing ka unnecessary code nahi chahiye.

### Benefits

- Small aur focused contracts.
- Unnecessary methods avoid hote hain.
- Code maintain karna easy.
- Classes apni required functionality hi use karti hain.

### Yaad rakho

ISP = Large interface ke bajaye small, specific interfaces.

---

## 7. D – Dependency Inversion Principle (DIP)

### Definition

High-level modules should not depend on low-level modules. Both should depend on abstractions.

Simple language:

Main business logic ko kisi ek specific implementation par tightly depend nahi hona chahiye. Dono ko ek common abstraction ke through connect karna chahiye.

### Important terms

**High-level module:** Business logic perform karta hai.

Example: OrderService.

**Low-level module:** Specific technical implementation provide karta hai.

Example: EmailService, SMSService.

**Abstraction:** Common contract ya interface.

### Wrong Example

```javascript
class EmailService {
  send(message) {
    console.log("Email:", message);
  }
}

class Notification {
  constructor() {
    this.emailService = new EmailService();
  }

  notify(message) {
    this.emailService.send(message);
  }
}
```

Problem:

Notification directly EmailService par depend kar raha hai.

Agar SMS notification add karna ho, toh Notification class modify karni padegi.

### Better Example

```javascript
class EmailService {
  send(message) {
    console.log("Email:", message);
  }
}

class SMSService {
  send(message) {
    console.log("SMS:", message);
  }
}

class Notification {
  constructor(service) {
    this.service = service;
  }

  notify(message) {
    this.service.send(message);
  }
}

const email = new Notification(new EmailService());
const sms = new Notification(new SMSService());

email.notify("Order placed");
sms.notify("Order shipped");
```

**Output:**

```text
Email: Order placed
SMS: Order shipped
```

Ab Notification ko constructor ke through service milti hai.

Is technique ko Dependency Injection (DI) kehte hain.

**Important difference:**

- DIP = Design principle.
- DI = Dependency provide karne ki technique.

### Benefits

- Loose coupling.
- Testing easy.
- Implementation change karna easy.
- Code flexible hota hai.

### Yaad rakho

DIP = Depend on abstractions, not concrete implementations.

---

## 8. All Five SOLID Principles – Comparison

| Principle | Main Idea                               | Problem Solved            |
| --------- | --------------------------------------- | ------------------------- |
| SRP       | One focused responsibility              | Too many responsibilities |
| OCP       | Extend without unnecessary modification | Repeated code changes     |
| LSP       | Child should work in place of parent    | Incorrect inheritance     |
| ISP       | Small specific interfaces               | Unnecessary methods       |
| DIP       | Depend on abstractions                  | Tight coupling            |

---

## 9. SOLID Principles in MERN Stack

MERN Stack mein SOLID principles ka practical use:

### SRP

- UserController: Request handle kare.
- UserService: Business logic handle kare.
- UserRepository: Database operations handle kare.

### OCP

Payment ke naye methods add karna without changing stable checkout logic.

### LSP

Child classes parent class ke expected behavior ko break na karein.

### ISP

Bade contracts ko chhote specific contracts mein divide karna, especially TypeScript projects mein.

### DIP

Service ko database ya notification implementation directly create karne ke bajaye dependency inject karna.

Example:

```javascript
class UserService {
  constructor(userRepository) {
    this.userRepository = userRepository;
  }

  getUsers() {
    return this.userRepository.findAll();
  }
}

class MongoUserRepository {
  findAll() {
    return ["Rahul", "Amit"];
  }
}

const repository = new MongoUserRepository();
const service = new UserService(repository);

console.log(service.getUsers());
```

**Output:**

```text
[ 'Rahul', 'Amit' ]
```

Yahan UserService ko repository constructor se di gayi hai. Isse testing ke time fake repository bhi pass kar sakte hain.

---

## 10. Advantages of SOLID

1. Maintainable code.
2. Reusable components.
3. Loose coupling.
4. Easy testing.
5. Flexible architecture.
6. Changes ka limited impact.
7. Large projects ko manage karna easy.

## 11. Disadvantages / Limitations

1. Shuru mein code zyada likhna pad sakta hai.
2. Beginners ke liye concepts difficult ho sakte hain.
3. Unnecessary abstractions se complexity badh sakti hai.
4. Har chhote project mein five principles ko forcefully apply karna zaroori nahi.
5. Overengineering se bachna chahiye.

**Important:** SOLID guidelines hain, strict rules nahi. Project ki actual requirements ke according apply karo.

---

## 12. Common Mistakes

1. SRP ka matlab ek class mein ek hi method samajhna.
2. OCP ka matlab kabhi existing code modify hi nahi karna samajhna.
3. LSP ko sirf inheritance syntax samajhna.
4. ISP mein ek hi bada interface bana dena.
5. DIP aur Dependency Injection ko same samajhna.
6. Har jagah unnecessary interfaces banana.
7. SOLID follow karne ke naam par simple code ko complicated banana.

---

## 13. Interview Questions and Answers

**Q1. What are SOLID principles?**

SOLID five OOP design principles hain jo maintainable, flexible aur reusable code design karne mein help karte hain.

**Q2. What is the full form of SOLID?**

- S: Single Responsibility Principle
- O: Open/Closed Principle
- L: Liskov Substitution Principle
- I: Interface Segregation Principle
- D: Dependency Inversion Principle

**Q3. What is SRP?**

Ek class ki ek focused responsibility honi chahiye.

**Q4. What is OCP?**

Code extension ke liye open aur unnecessary modification ke liye closed hona chahiye.

**Q5. What is LSP?**

Child class ko parent class ki jagah use karne par expected behavior break nahi hona chahiye.

**Q6. What is ISP?**

Classes ko unnecessary methods implement karne ke liye force nahi karna chahiye.

**Q7. What is DIP?**

High-level aur low-level modules ko abstractions par depend karna chahiye.

**Q8. What is the difference between DIP and DI?**

DIP ek design principle hai, jabki DI dependency provide karne ki technique hai.

**Q9. Which SOLID principle helps reduce tight coupling?**

DIP.

**Q10. Which principle focuses on small interfaces?**

ISP.

---

## 14. Practice Tasks

### Task 1 – SRP

Ek class banao jo user data, database saving aur email sending sab karti ho.

Usse 3 separate classes mein divide karo.

### Task 2 – OCP

Payment system banao jisme:

- UPI
- Card
- Net Banking

Naya payment type add karne par checkout function change na karna pade.

### Task 3 – LSP

Bird example implement karo:

- Bird
- FlyingBird
- Sparrow
- Penguin

Ensure karo ki Penguin ko fly karne ke liye force na kiya jaye.

### Task 4 – ISP

Machine example implement karo:

- Printer
- Scanner
- Fax

Alag-alag functionality ke small contracts banao.

### Task 5 – DIP

Notification system banao jo:

- Email
- SMS

Dono ko support kare aur notification class directly kisi ek service ko create na kare.

---

## 15. Quick Revision

| Letter | Full Form             | Remember                           |
| ------ | --------------------- | ---------------------------------- |
| S      | Single Responsibility | One focused responsibility         |
| O      | Open/Closed           | Extend, don't unnecessarily modify |
| L      | Liskov Substitution   | Child should replace parent        |
| I      | Interface Segregation | Small interfaces                   |
| D      | Dependency Inversion  | Depend on abstractions             |

### Easy Trick

**S – One job**

**O – Easy extension**

**L – Safe substitution**

**I – Small interfaces**

**D – Loose dependency**

---

## 16. Topic Completion Checklist

- [ ] SOLID ka meaning samajh liya.
- [ ] SRP samajh liya.
- [ ] OCP samajh liya.
- [ ] LSP samajh liya.
- [ ] ISP samajh liya.
- [ ] DIP samajh liya.
- [ ] DIP aur DI ka difference samajh liya.
- [ ] JavaScript examples practice kar liye.
- [ ] MERN connection samajh liya.
- [ ] Interview questions revise kar liye.
- [ ] Practice tasks complete kar liye.

**Topic 10 Complete: Introduction to SOLID Principles**
