# Topic 05: Abstraction (OOP)

## 1. Abstraction kya hota hai?

**Abstraction** OOP (Object-Oriented Programming) ka ek important concept hai.

Iska matlab hai:

- User ko sirf zaroori information aur functionality dikhana.
- Internal implementation details ko hide karna.
- User ko ye batana ki koi feature kya karta hai, bina ye bataye ki woh internally kaise kaam karta hai.

Simple language mein:

**Abstraction = What to do dikhana, How it works hide karna.**

### Real-Life Example: ATM

Jab tum ATM se paise withdraw karte ho, toh tumhe sirf ye steps follow karne hote hain:

1. ATM card insert karo.
2. PIN enter karo.
3. Amount enter karo.
4. Cash receive karo.

Tumhe ye jaanne ki zaroorat nahi hoti ki ATM internally:

- Bank server se kaise connect hota hai.
- Account balance kaise check karta hai.
- Transaction database mein kaise save karta hai.
- Cash dispenser kaise operate karta hai.

Ye internal implementation details user se hide rehti hain.

Yahi Abstraction hai.

---

## 2. Programming mein Abstraction kaise hota hai?

Maan lo hum ek car system bana rahe hain.

User ko car start karne ke liye sirf `start()` method call karna hai.

```cpp
car.start();
```

User ko engine ke internal working details jaanne ki zaroorat nahi.

Class ke andar engine start karne ka complete logic ho sakta hai.

```cpp
class Car {
public:
    void start() {
        // Internal engine starting logic
    }
};
```

Yahan user ko `start()` ka use pata hai, lekin internal implementation details jaanne ki zaroorat nahi.

---

## 3. Abstraction achieve karne ke methods

C++ mein Abstraction achieve karne ke do common ways hain:

1. Access Specifiers ke through.
2. Abstract Classes aur Pure Virtual Functions ke through.

### A. Access Specifiers

Access specifiers ki help se hum class ke internal data ko private rakh sakte hain aur required methods ko public bana sakte hain.

Example:

```cpp
#include <iostream>
using namespace std;

class ATM {
private:
    int balance = 5000;

public:
    void checkBalance() {
        cout << "Balance: " << balance;
    }
};

int main() {
    ATM atm;

    atm.checkBalance();

    return 0;
}
```

**Output:**

```text
Balance: 5000
```

Yahan:

- `balance` private hai.
- `checkBalance()` public hai.
- User ko sirf required functionality use karni hai.

**Important:** Access specifiers Encapsulation ke saath Data Hiding bhi provide karte hain. Sirf private variables bana dena complete Abstraction design nahi hota. Abstraction ka focus unnecessary implementation details ko hide karna hai.

---

## 4. Abstract Class kya hoti hai?

**Abstract Class** aisi class hoti hai jisme kam se kam ek pure virtual function hota hai.

C++ mein abstract class ka object directly create nahi kar sakte.

Abstract class ko base class ki tarah use kiya jata hai.

Iska purpose common interface define karna hota hai jise derived classes implement karti hain.

### Pure Virtual Function kya hota hai?

C++ mein jis virtual function ko `= 0` assign kiya jata hai, use Pure Virtual Function kehte hain.

Syntax:

```cpp
virtual void functionName() = 0;
```

Example:

```cpp
class Animal {
public:
    virtual void sound() = 0;
};
```

Yahan `sound()` pure virtual function hai.

Isliye `Animal` abstract class ban gayi.

---

## 5. Abstract Class ka Complete Example

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() = 0;
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks";
    }
};

int main() {
    Dog d1;

    d1.sound();

    return 0;
}
```

**Output:**

```text
Dog barks
```

### Code kaise work karta hai?

1. `Animal` ek abstract class hai.
2. Ismein `sound()` pure virtual function hai.
3. `Dog` class, `Animal` ko inherit karti hai.
4. `Dog` class `sound()` function implement karti hai.
5. Object `d1` ke through `sound()` call hota hai.

**Important:** Agar derived class kisi inherited pure virtual function ko implement nahi karti, toh woh derived class bhi abstract rahegi.

---

## 6. Abstract Class ka Object kyun nahi bana sakte?

Example:

```cpp
class Animal {
public:
    virtual void sound() = 0;
};

int main() {
    Animal a1; // Error
}
```

Ye error dega.

Reason:

Abstract class mein kuch functionality incomplete ho sakti hai.

Compiler aise class ka direct object create karne ki permission nahi deta.

Lekin abstract class ka pointer ya reference bana sakte hain.

Example:

```cpp
Animal* ptr;
```

Pointer declare karna allowed hai, lekin abstract class ka direct object create karna allowed nahi hai.

---

## 7. Real-Life Example: Payment System

Maan lo ek application mein multiple payment methods hain:

- UPI
- Credit Card
- Debit Card

Har payment method ka internal process different ho sakta hai.

Lekin application ke liye common functionality hai:

`pay()`

Iske liye hum abstract class bana sakte hain.

```cpp
#include <iostream>
using namespace std;

class Payment {
public:
    virtual void pay(double amount) = 0;
};

class UPI : public Payment {
public:
    void pay(double amount) override {
        cout << "Paid Rs. " << amount << " using UPI" << endl;
    }
};

class CreditCard : public Payment {
public:
    void pay(double amount) override {
        cout << "Paid Rs. " << amount << " using Credit Card" << endl;
    }
};

int main() {
    UPI upi;
    CreditCard card;

    upi.pay(500);
    card.pay(1000);

    return 0;
}
```

**Output:**

```text
Paid Rs. 500 using UPI
Paid Rs. 1000 using Credit Card
```

### Is example mein Abstraction kahan hai?

- `Payment` common interface provide karta hai.
- Har payment method ko `pay()` implement karna hota hai.
- Internal payment implementation har class apne according handle karti hai.
- User ko common operation ka interface milta hai.

---

## 8. Abstraction aur Polymorphism ka Connection

Dono concepts ek saath bhi kaam kar sakte hain.

Example:

```cpp
#include <iostream>
using namespace std;

class Payment {
public:
    virtual void pay() = 0;
};

class UPI : public Payment {
public:
    void pay() override {
        cout << "UPI Payment" << endl;
    }
};

class Card : public Payment {
public:
    void pay() override {
        cout << "Card Payment" << endl;
    }
};

int main() {
    UPI upi;
    Card card;

    Payment* ptr;

    ptr = &upi;
    ptr->pay();

    ptr = &card;
    ptr->pay();

    return 0;
}
```

**Output:**

```text
UPI Payment
Card Payment
```

Yahan:

- Abstraction: `Payment` common interface provide karta hai.
- Polymorphism: Same `pay()` call different classes ke according different behavior deta hai.
- `virtual` function runtime par correct implementation call karne mein help karta hai.

---

## 9. JavaScript mein Abstraction

JavaScript mein C++ ki tarah built-in `abstract class` keyword nahi hota.

Lekin hum classes aur methods ke through abstraction ka concept implement kar sakte hain.

Example:

```javascript
class Payment {
  pay(amount) {
    throw new Error("pay() method must be implemented");
  }
}

class UPI extends Payment {
  pay(amount) {
    console.log(`Paid Rs. ${amount} using UPI`);
  }
}

class Card extends Payment {
  pay(amount) {
    console.log(`Paid Rs. ${amount} using Card`);
  }
}

const payment = new UPI();

payment.pay(500);
```

**Output:**

```text
Paid Rs. 500 using UPI
```

Yahan:

- `Payment` common structure define kar raha hai.
- `UPI` apna `pay()` implementation provide karta hai.
- `Card` apna alag implementation provide kar sakta hai.

**Important:** JavaScript mein ye convention-based approach hai. `Payment` ko directly instantiate karne se JavaScript automatically nahi rokta. Error tab aayega jab base class ka `pay()` call hoga.

---

## 10. MERN Stack mein Abstraction

MERN Stack mein Abstraction ka use multiple places par samajh sakte hain.

### A. Frontend – React Components

React components internal logic ko hide karke reusable interface provide kar sakte hain.

Example:

```jsx
function LoginButton() {
  function handleLogin() {
    // Login related logic
  }

  return <button onClick={handleLogin}>Login</button>;
}
```

User ko sirf Login button dikhai deta hai.

Internal logic component ke andar handle hota hai.

### B. Backend – Service Layer

Backend mein controller aur service layer separate rakhna Abstraction ko support karta hai.

Example:

```text
Client
  |
  v
Controller
  |
  v
User Service
  |
  v
Database
```

Controller ko database ke har internal operation ko manage karne ki zaroorat nahi hoti.

Woh service ka method call kar sakta hai:

```javascript
const user = await userService.getUserById(id);
```

Service internally database query handle kar sakti hai.

### C. Database Abstraction

Application database ke saath Mongoose jaise ODM ke through interact kar sakti hai.

Example:

```javascript
const user = await User.findById(userId);
```

Developer ko har baar raw database protocol aur low-level query handling likhne ki zaroorat nahi hoti.

Mongoose ye complexity simplify karta hai.

**Note:** Ye Abstraction ke practical examples hain; har component ya service automatically perfect abstraction nahi hota. Achhi abstraction ke liye clear responsibilities aur interfaces zaroori hain.

---

## 11. Advantages of Abstraction

1. **Reduced Complexity:** Unnecessary implementation details hide hoti hain.
2. **Easy Maintenance:** Internal code change karna relatively easy hota hai.
3. **Code Reusability:** Common interfaces ko multiple classes implement kar sakti hain.
4. **Better Organization:** Common functionality define karna easy hota hai.
5. **Flexibility:** Different implementations ko same interface ke through use kar sakte hain.
6. **Loose Coupling:** Achhi abstraction components ki direct dependency kam karne mein help karti hai.

## 12. Disadvantages of Abstraction

1. Design karna beginners ke liye difficult ho sakta hai.
2. Unnecessary abstraction code ko complex bana sakti hai.
3. Extra classes aur interfaces create karne pad sakte hain.
4. Bahut zyada abstraction se code samajhna difficult ho sakta hai.

**Best Practice:** Abstraction wahi use karo jahan common behavior ya implementation details ko hide karna genuinely useful ho.

---

## 13. Encapsulation vs Abstraction

Dono OOP ke important concepts hain, lekin dono ka focus different hai.

| Encapsulation                            | Abstraction                                       |
| ---------------------------------------- | ------------------------------------------------- |
| Data aur methods ko bundle karta hai     | Unnecessary implementation details hide karta hai |
| Controlled access par focus karta hai    | Essential functionality expose karta hai          |
| Data protection mein help karta hai      | Complexity reduce karta hai                       |
| Private, Public, Protected use hote hain | Abstract classes aur interfaces use ho sakte hain |
| Example: Private bank balance            | Example: ATM ka withdraw operation                |

### Easy Trick

**Encapsulation = How to protect data?**

**Abstraction = What to show and what to hide?**

---

## 14. Common Mistakes

1. Encapsulation aur Abstraction ko same samajhna.
2. Abstract class ka direct object create karne ki koshish karna.
3. Pure virtual function ka syntax galat likhna.
4. Derived class mein required pure virtual functions implement na karna.
5. Har class ko abstract banane ki koshish karna.
6. JavaScript mein `throw new Error()` wali approach ko built-in abstract class feature samajhna.
7. Unnecessary abstraction create karna.

---

## 15. Interview Questions and Answers

### Q1. What is Abstraction?

Abstraction is an OOP concept that hides unnecessary implementation details and exposes only essential functionality.

### Q2. What is an Abstract Class?

A class containing at least one pure virtual function in C++ is called an abstract class.

### Q3. What is a Pure Virtual Function?

A virtual function declared with `= 0` in C++ is called a pure virtual function.

### Q4. Can we create an object of an abstract class?

No, we cannot create a direct object of an abstract class in C++.

### Q5. Can we create a pointer of an abstract class?

Yes, we can create pointers and references of an abstract class.

### Q6. How can we achieve Abstraction in C++?

Commonly through access control and abstract classes with pure virtual functions.

### Q7. Does JavaScript support abstract classes directly?

No. JavaScript does not have a built-in `abstract` class keyword, but similar behavior can be implemented using classes and methods.

### Q8. What is the difference between Encapsulation and Abstraction?

Encapsulation focuses on bundling data and methods with controlled access, whereas Abstraction focuses on hiding unnecessary implementation details.

---

## 16. Practice Tasks

### Task 1: Shape Class

Ek abstract class `Shape` banao.

- Pure virtual function: `area()`
- Derived class: `Circle`
- Derived class: `Rectangle`
- Dono classes mein area calculate karo.

### Task 2: Payment System

Ek abstract class `Payment` banao.

- Pure virtual function: `pay()`
- Derived classes: `UPI`, `Card`, `Cash`
- Har class mein alag payment message print karo.

### Task 3: Vehicle System

Ek abstract class `Vehicle` banao.

- Pure virtual function: `start()`
- Derived classes: `Car`, `Bike`
- Dono apna start behavior implement karein.

### Task 4: JavaScript

JavaScript mein `Notification` base class banao.

- `send()` method define karo.
- `EmailNotification` aur `SMSNotification` classes banao.
- Dono apna `send()` method implement karein.

---

## 17. Quick Revision

| Concept                 | Meaning                                               |
| ----------------------- | ----------------------------------------------------- |
| Abstraction             | Unnecessary details hide karna                        |
| Abstract Class          | C++ class jisme at least one pure virtual function ho |
| Pure Virtual Function   | `virtual void show() = 0;`                            |
| Interface-like behavior | Common functionality ka contract provide karna        |
| `override`              | Base class virtual function ko override karna         |
| C++ Abstract Object     | Direct object create nahi kar sakte                   |
| Abstract Pointer        | Allowed                                               |
| JavaScript Abstraction  | Classes aur methods se implement kar sakte hain       |

### One-Line Revision

**Abstraction ka purpose user ko sirf required functionality dikhana aur unnecessary internal implementation details hide karna hai.**

---

## 18. Completion Checklist

- [ ] Abstraction ka meaning samajh liya.
- [ ] Real-life ATM example samajh liya.
- [ ] Access specifiers ka role samajh liya.
- [ ] Abstract class samajh li.
- [ ] Pure virtual function samajh liya.
- [ ] Abstract class ka object kyun nahi banta, samajh liya.
- [ ] Payment System example samajh liya.
- [ ] Polymorphism ke saath connection samajh liya.
- [ ] JavaScript aur MERN examples samajh liye.
- [ ] Encapsulation vs Abstraction ka difference samajh liya.
- [ ] Practice tasks complete kar liye.

**Topic 05 – Abstraction Complete.**
