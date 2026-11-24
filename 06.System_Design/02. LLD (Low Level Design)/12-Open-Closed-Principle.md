# Open/Closed Principle (OCP)

## 1. Introduction

OCP ka full form hai:

**Open/Closed Principle**

Ye SOLID principles ka second principle hai.

### Definition

Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.

### Simple language

- **Open for Extension:** Existing code mein naye features add kar sakein.
- **Closed for Modification:** Existing tested code ko baar-baar change karne ki zaroorat na pade.

Example:

Maan lo ek payment system hai. Abhi woh UPI aur Card payment support karta hai.

Future mein Net Banking aur Wallet payment bhi add karna hai.

Agar har baar existing payment class mein naye `if-else` add karne pad rahe hain, toh design improve kiya ja sakta hai.

---

## 2. Real-Life Example

Maan lo ek mobile phone hai.

Initially usmein sirf calling feature hai.

Future mein hum add karna chahte hain:

- Camera
- Music Player
- Internet
- GPS

Achhe design mein naye features add karne ke liye phone ke existing working features ko unnecessarily change nahi karna padega.

Software mein bhi isi idea ko OCP represent karta hai.

---

## 3. OCP Violation – Wrong Example

Maan lo hum ek payment system bana rahe hain.

```javascript
class Payment {
  pay(type, amount) {
    if (type === "UPI") {
      console.log("UPI Payment:", amount);
    } else if (type === "CARD") {
      console.log("Card Payment:", amount);
    }
  }
}

const payment = new Payment();

payment.pay("UPI", 500);
payment.pay("CARD", 1000);
```

### Output

```text
UPI Payment: 500
Card Payment: 1000
```

### Problem kya hai?

Maan lo ab humein Net Banking add karni hai.

Toh Payment class ko modify karna padega.

```javascript
else if (type === "NETBANKING") {
    console.log("Net Banking Payment:", amount);
}
```

Aage Wallet aur Cash payment bhi add karni ho toh baar-baar isi class mein conditions add karni padengi.

Isse:

- Code complicated ho sakta hai.
- Existing functionality break ho sakti hai.
- Testing difficult ho sakti hai.
- Changes ka impact badh sakta hai.

Ye OCP violation ka example hai.

---

## 4. OCP Follow Karne Wala Correct Example

Ab hum polymorphism ka use karenge.

```javascript
class UPIPayment {
  pay(amount) {
    console.log("UPI Payment:", amount);
  }
}

class CardPayment {
  pay(amount) {
    console.log("Card Payment:", amount);
  }
}

class NetBankingPayment {
  pay(amount) {
    console.log("Net Banking Payment:", amount);
  }
}

function checkout(paymentMethod, amount) {
  paymentMethod.pay(amount);
}

checkout(new UPIPayment(), 500);
checkout(new CardPayment(), 1000);
checkout(new NetBankingPayment(), 1500);
```

### Output

```text
UPI Payment: 500
Card Payment: 1000
Net Banking Payment: 1500
```

### Explanation

1. UPI payment ke liye separate class banayi.
2. Card payment ke liye separate class banayi.
3. Net Banking ke liye separate class banayi.
4. Har class mein `pay()` method hai.
5. `checkout()` function kisi specific payment class par depend nahi karta.
6. Naya payment method add karne ke liye nayi class bana sakte hain.

Ab checkout function ko modify karne ki zaroorat nahi hai.

**Yahi Open/Closed Principle hai.**

Note: JavaScript mein ye common contract ko same method name aur expected behavior ke through follow karaya gaya hai. TypeScript mein interface se contract ko explicitly define bhi kar sakte hain.

---

## 5. OCP Using Interface in TypeScript

TypeScript mein interface ka use karke OCP aur clearly implement kar sakte hain.

```typescript
interface PaymentMethod {
  pay(amount: number): void;
}

class UPIPayment implements PaymentMethod {
  pay(amount: number): void {
    console.log("UPI Payment:", amount);
  }
}

class CardPayment implements PaymentMethod {
  pay(amount: number): void {
    console.log("Card Payment:", amount);
  }
}

class WalletPayment implements PaymentMethod {
  pay(amount: number): void {
    console.log("Wallet Payment:", amount);
  }
}

function checkout(payment: PaymentMethod, amount: number): void {
  payment.pay(amount);
}

checkout(new UPIPayment(), 500);
checkout(new CardPayment(), 1000);
checkout(new WalletPayment(), 1500);
```

### Output

```text
UPI Payment: 500
Card Payment: 1000
Wallet Payment: 1500
```

### Ismein OCP kaise follow hua?

- `PaymentMethod` interface common contract provide karta hai.
- Har payment class apna implementation provide karti hai.
- Checkout function interface par depend karta hai.
- Naya payment method add karne par checkout function change nahi karna padta.

---

## 6. OCP and Polymorphism

Polymorphism OCP implement karne mein bahut useful hota hai.

### Polymorphism kya karta hai?

Different objects ko same method ke through different behavior provide karne deta hai.

Example:

```javascript
class Dog {
  sound() {
    console.log("Bark");
  }
}

class Cat {
  sound() {
    console.log("Meow");
  }
}

function makeSound(animal) {
  animal.sound();
}

makeSound(new Dog());
makeSound(new Cat());
```

**Output:**

```text
Bark
Meow
```

Ab agar naya animal add karna ho, toh ek nayi class bana sakte hain.

Existing `makeSound()` function change karne ki zaroorat nahi.

### Important relationship

- Polymorphism = Different objects, same interface/method, different behavior.
- OCP = New behavior add karne ke liye existing stable code ko unnecessarily modify na karna.

Polymorphism OCP follow karne ka ek common technique hai, lekin OCP sirf polymorphism tak limited nahi hai.

---

## 7. OCP in C++

C++ mein virtual functions aur inheritance ke through OCP implement kar sakte hain.

### Example

```cpp
#include <iostream>
using namespace std;

class Payment {
public:
    virtual void pay(int amount) = 0;

    virtual ~Payment() = default;
};

class UPIPayment : public Payment {
public:
    void pay(int amount) override {
        cout << "UPI Payment: " << amount << endl;
    }
};

class CardPayment : public Payment {
public:
    void pay(int amount) override {
        cout << "Card Payment: " << amount << endl;
    }
};

class WalletPayment : public Payment {
public:
    void pay(int amount) override {
        cout << "Wallet Payment: " << amount << endl;
    }
};

int main() {
    UPIPayment upi;
    CardPayment card;
    WalletPayment wallet;

    upi.pay(500);
    card.pay(1000);
    wallet.pay(1500);

    return 0;
}
```

### Output

```text
UPI Payment: 500
Card Payment: 1000
Wallet Payment: 1500
```

Yahan Payment abstract class common contract provide karti hai.

Naye payment method ke liye nayi derived class create kar sakte hain.

---

## 8. OCP in MERN Stack

MERN application mein OCP ka use multiple places par kar sakte hain.

### Example: Notification System

Maan lo application mein notifications send karni hain.

Initially:

- Email notification

Future mein:

- SMS notification
- Push notification
- WhatsApp notification

### Suggested structure

```text
backend/
│
├── notifications/
│   ├── EmailNotification.js
│   ├── SMSNotification.js
│   ├── PushNotification.js
│   └── NotificationService.js
│
└── server.js
```

### JavaScript example

```javascript
class EmailNotification {
  send(message) {
    console.log("Email:", message);
  }
}

class SMSNotification {
  send(message) {
    console.log("SMS:", message);
  }
}

class PushNotification {
  send(message) {
    console.log("Push:", message);
  }
}

class NotificationService {
  constructor(provider) {
    this.provider = provider;
  }

  notify(message) {
    this.provider.send(message);
  }
}

const email = new NotificationService(new EmailNotification());

const sms = new NotificationService(new SMSNotification());

email.notify("Welcome!");
sms.notify("Your order is shipped!");
```

**Output:**

```text
Email: Welcome!
SMS: Your order is shipped!
```

Naya notification provider add karne ke liye nayi class create kar sakte hain.

NotificationService ko change karne ki zaroorat nahi, jab tak naya provider same expected contract follow karta hai.

---

## 9. Advantages of OCP

### 1. Easy Extension

Naye features add karna easy hota hai.

### 2. Existing Code Safe

Tested code mein unnecessary changes kam hote hain.

### 3. Less Risk

Existing functionality break hone ka risk reduce ho sakta hai.

### 4. Better Maintainability

Code ko maintain karna easy hota hai.

### 5. Reusability

Common contracts aur implementations reuse kiye ja sakte hain.

### 6. Scalability of Code

Application mein new functionality add karna easier ho sakta hai.

---

## 10. Disadvantages / Limitations

1. Extra classes aur abstractions create ho sakti hain.
2. Initial design thoda complex ho sakta hai.
3. Har feature ke liye extension point banana zaroori nahi.
4. Overengineering ka risk hota hai.
5. Poor abstraction se future changes aur difficult ho sakte hain.

**Remember:** OCP ka matlab existing code ko kabhi modify nahi karna nahi hai. Jab actual requirements change hon, toh existing code modify karna valid ho sakta hai. Principle unnecessary modification ko reduce karne par focus karta hai.

---

## 11. Common Mistakes

1. OCP ka matlab code kabhi change nahi hona samajhna.
2. Har jagah unnecessary interfaces banana.
3. Har new feature ke liye existing classes mein `if-else` add karte rehna.
4. Polymorphism ka use na karna jab woh suitable ho.
5. Existing code ko completely freeze kar dena.
6. Extension points bina actual need ke create karna.

---

## 12. Interview Questions and Answers

**Q1. What is OCP?**

Open/Closed Principle ke according software entities extension ke liye open aur modification ke liye closed honi chahiye.

**Q2. What is the full form of OCP?**

Open/Closed Principle.

**Q3. What does Open for Extension mean?**

Existing system mein naye features add kar sakna.

**Q4. What does Closed for Modification mean?**

Naye features add karne ke liye existing stable code ko unnecessarily modify na karna.

**Q5. How can we implement OCP?**

Interfaces, abstraction, composition aur polymorphism jaise techniques se.

**Q6. What is the relationship between OCP and polymorphism?**

Polymorphism different implementations ko common contract ke through use karne deta hai, jo OCP follow karne mein help karta hai.

**Q7. Is OCP only applicable to classes?**

No. Ye classes, functions aur modules par bhi apply ho sakta hai.

**Q8. What is an example of OCP violation?**

Ek payment class mein har naye payment method ke liye naye `if-else` conditions add karna.

**Q9. What is the biggest benefit of OCP?**

Existing tested code mein unnecessary changes kam karna aur system ko extendable banana.

**Q10. Does OCP mean existing code should never be modified?**

No. Requirement ke according modification kabhi-kabhi necessary hota hai.

---

## 13. Practice Tasks

### Task 1 – Payment System

Payment system banao:

- UPI
- Card
- Net Banking
- Wallet

Naye payment methods add karne par checkout function modify nahi hona chahiye.

### Task 2 – Notification System

Classes banao:

- EmailNotification
- SMSNotification
- PushNotification

Sab mein same `send()` method rakho.

### Task 3 – Shape System

Shape ke liye common contract banao.

Implementations:

- Circle
- Rectangle
- Triangle

Har class ka apna `calculateArea()` method ho.

### Task 4 – MERN Practical Design

Ek notification service design karo jisme future mein new notification provider easily add ho sake.

---

## 14. Quick Revision

| Point                   | Meaning                                               |
| ----------------------- | ----------------------------------------------------- |
| Full Form               | Open/Closed Principle                                 |
| SOLID Position          | Second principle                                      |
| Open for Extension      | New features add karna                                |
| Closed for Modification | Existing stable code ko unnecessarily change na karna |
| Common Technique        | Abstraction and Polymorphism                          |
| Main Benefit            | Flexible and maintainable code                        |

### One-line Revision

**OCP = Naye features add karo, lekin existing stable code ko baar-baar unnecessarily modify mat karo.**

---

## 15. Topic Completion Checklist

- [ ] OCP ka meaning samajh liya.
- [ ] Open for Extension samajh liya.
- [ ] Closed for Modification samajh liya.
- [ ] Wrong example samajh liya.
- [ ] Correct example samajh liya.
- [ ] Interface ke through OCP samajh liya.
- [ ] Polymorphism ka connection samajh liya.
- [ ] C++ example practice kar liya.
- [ ] JavaScript example practice kar liya.
- [ ] MERN example samajh liya.
- [ ] Interview questions revise kar liye.
- [ ] Practice tasks complete kar liye.

**Topic 12 Complete: Open/Closed Principle (OCP)**
