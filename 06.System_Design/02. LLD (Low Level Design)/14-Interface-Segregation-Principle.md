# 14. Interface Segregation Principle (ISP)

## 1. ISP Kya Hai?

ISP ka full form hai **Interface Segregation Principle**.

Ye SOLID principles ka fourth principle hai.

Is principle ko Robert C. Martin ne popularize kiya tha.

### Simple Definition

Clients ko aise interfaces par depend nahi karna chahiye jin methods ki unhe zaroorat hi nahi hai.

Simple words mein:

**Kisi class ko aise methods implement karne ke liye force mat karo jinki us class ko zaroorat nahi hai.**

### Example

Maan lo ek interface hai `Worker`.

Isme 3 methods hain:

- `work()`
- `eat()`
- `sleep()`

Ab Human worker ke liye teeno methods useful hain.

Lekin Robot ke liye:

- `work()` useful hai.
- `eat()` ki zaroorat nahi.
- `sleep()` ki zaroorat nahi.

Agar Robot ko bhi teeno methods implement karne pad rahe hain, toh interface unnecessarily bada hai.

Yahi problem ISP solve karta hai.

---

## 2. ISP Violation Example (JavaScript)

JavaScript mein interfaces built-in nahi hote, lekin classes ke through interface jaisa contract demonstrate kar sakte hain.

### Wrong Design

```javascript
class Worker {
  work() {
    throw new Error("Implement work()");
  }

  eat() {
    throw new Error("Implement eat()");
  }

  sleep() {
    throw new Error("Implement sleep()");
  }
}

class HumanWorker extends Worker {
  work() {
    console.log("Human is working");
  }

  eat() {
    console.log("Human is eating");
  }

  sleep() {
    console.log("Human is sleeping");
  }
}

class RobotWorker extends Worker {
  work() {
    console.log("Robot is working");
  }

  eat() {
    throw new Error("Robot does not eat");
  }

  sleep() {
    throw new Error("Robot does not sleep");
  }
}
```

Problem:

Robot ko `eat()` aur `sleep()` methods implement karne pad rahe hain, jabki unki zaroorat hi nahi hai.

Ye unnecessary implementation hai aur design ko confusing banata hai.

---

## 3. ISP Follow Karne Ka Correct Way

Bade interface ko chhote, specific interfaces mein divide kar do.

### Better Design

```javascript
class Workable {
  work() {
    throw new Error("Implement work()");
  }
}

class Eatable {
  eat() {
    throw new Error("Implement eat()");
  }
}

class Sleepable {
  sleep() {
    throw new Error("Implement sleep()");
  }
}
```

Ab Human aur Robot sirf required capabilities use karenge.

```javascript
class HumanWorker extends Workable {
  work() {
    console.log("Human is working");
  }
}

class RobotWorker extends Workable {
  work() {
    console.log("Robot is working");
  }
}
```

Human ke liye additional capabilities:

```javascript
class Human extends Workable {
  work() {
    console.log("Human is working");
  }

  eat() {
    console.log("Human is eating");
  }

  sleep() {
    console.log("Human is sleeping");
  }
}
```

Is example mein JavaScript classes ko interface-like contracts demonstrate karne ke liye use kiya gaya hai. Real JavaScript mein TypeScript jaisi formal interface declaration nahi hoti.

**Main point:** Har class ko sirf wahi capabilities implement karni chahiye jo uske kaam ki hain.

---

## 4. ISP in TypeScript

TypeScript mein `interface` keyword available hai.

Isliye ISP ko clearly implement kar sakte hain.

### Wrong Design

```typescript
interface Worker {
  work(): void;
  eat(): void;
  sleep(): void;
}

class Robot implements Worker {
  work() {
    console.log("Robot is working");
  }

  eat() {
    // Not required
  }

  sleep() {
    // Not required
  }
}
```

Robot ko unnecessary methods implement karne pad rahe hain.

### Correct Design

```typescript
interface Workable {
  work(): void;
}

interface Eatable {
  eat(): void;
}

interface Sleepable {
  sleep(): void;
}

class Human implements Workable, Eatable, Sleepable {
  work() {
    console.log("Human is working");
  }

  eat() {
    console.log("Human is eating");
  }

  sleep() {
    console.log("Human is sleeping");
  }
}

class Robot implements Workable {
  work() {
    console.log("Robot is working");
  }
}
```

Ab:

- Human required interfaces implement karta hai.
- Robot sirf Workable implement karta hai.
- Koi unnecessary method implement nahi karna padta.

---

## 5. Interface Segregation Ka Meaning

Segregation ka matlab hota hai **divide karna ya alag-alag karna**.

Interface Segregation ka matlab hai:

Ek bade interface ko chhote aur focused interfaces mein divide karna.

### Example

Wrong:

```text
              Machine
                 |
       ---------------------
       |        |          |
     print()  scan()     fax()
```

Har machine ko print, scan aur fax implement karna padega.

Lekin har printer fax ya scan nahi kar sakta.

Correct:

```text
       Printable
           |
       Printer

         Scannable
             |
          Scanner

           Faxable
              |
           FaxMachine
```

Ab class sirf required interface implement karegi.

---

## 6. ISP in C++

C++ mein abstract classes ka use karke ISP implement kar sakte hain.

### Example

```cpp
#include <iostream>
using namespace std;

class Printable {
public:
    virtual void print() = 0;
    virtual ~Printable() = default;
};

class Scannable {
public:
    virtual void scan() = 0;
    virtual ~Scannable() = default;
};

class SimplePrinter : public Printable {
public:
    void print() override {
        cout << "Printing document" << endl;
    }
};

class MultiFunctionPrinter : public Printable, public Scannable {
public:
    void print() override {
        cout << "Printing document" << endl;
    }

    void scan() override {
        cout << "Scanning document" << endl;
    }
};

int main() {
    SimplePrinter printer;
    MultiFunctionPrinter machine;

    printer.print();

    machine.print();
    machine.scan();

    return 0;
}
```

Output:

```text
Printing document
Printing document
Scanning document
```

### Explanation

- `Printable` sirf printing ka contract define karta hai.
- `Scannable` sirf scanning ka contract define karta hai.
- SimplePrinter sirf Printable implement karta hai.
- MultiFunctionPrinter dono implement karta hai.

Yahan koi class unnecessary method implement karne ke liye forced nahi hai.

---

## 7. ISP in MERN Stack

MERN projects mein bhi ISP ka use hota hai.

Maan lo ek e-commerce application hai.

Usme alag-alag services hain:

- User service
- Product service
- Order service
- Payment service

Agar ek hi interface mein sabhi methods rakh diye jaayen, toh har service ko unnecessary methods ka dependency lena padega.

### Wrong Design

```typescript
interface ApplicationService {
  createUser(): void;
  deleteUser(): void;

  addProduct(): void;
  deleteProduct(): void;

  createOrder(): void;
  cancelOrder(): void;

  processPayment(): void;
}
```

Problem:

Payment service ko user delete karne ya product add karne ki zaroorat nahi hai.

### Correct Design

```typescript
interface UserService {
  createUser(): void;
  deleteUser(): void;
}

interface ProductService {
  addProduct(): void;
  deleteProduct(): void;
}

interface OrderService {
  createOrder(): void;
  cancelOrder(): void;
}

interface PaymentService {
  processPayment(): void;
}
```

Ab har service apne required methods par depend karegi.

**MERN connection:**

- Node.js aur Express.js mein service layers ko focused rakh sakte ho.
- TypeScript use karte waqt small interfaces define kar sakte ho.
- React components ko bhi sirf required props aur callbacks dene chahiye.

---

## 8. ISP Ke Advantages

1. Code simple aur clean hota hai.
2. Unnecessary methods implement nahi karne padte.
3. Classes ke beech coupling kam hoti hai.
4. Code maintain karna easy hota hai.
5. Testing easy hoti hai.
6. Reusability improve hoti hai.
7. Changes ka impact limited rehta hai.

---

## 9. ISP Follow Na Karne Ke Disadvantages

1. Interfaces unnecessarily large ho jaate hain.
2. Classes ko unwanted methods implement karne padte hain.
3. Code confusing ho sakta hai.
4. Unnecessary dependencies badhti hain.
5. Changes karne par multiple classes affect ho sakti hain.
6. Testing difficult ho sakti hai.

---

## 10. ISP vs SRP

SRP aur ISP dono code ko focused rakhne mein help karte hain, lekin dono ka focus alag hai.

| SRP                                              | ISP                                                          |
| ------------------------------------------------ | ------------------------------------------------------------ |
| Single Responsibility Principle                  | Interface Segregation Principle                              |
| Class ki responsibilities par focus karta hai.   | Interfaces ke size aur dependencies par focus karta hai.     |
| Ek class ke paas ek responsibility honi chahiye. | Client ko unnecessary methods par depend nahi karna chahiye. |
| Class design improve karta hai.                  | Interface design improve karta hai.                          |

### Example

SRP: Payment class payment process kare, email send karne ki responsibility alag class ki ho.

ISP: Payment interface mein sirf payment-related methods hon, unrelated methods nahi.

---

## 11. ISP vs LSP

| LSP                                         | ISP                                            |
| ------------------------------------------- | ---------------------------------------------- |
| Liskov Substitution Principle               | Interface Segregation Principle                |
| Child class ke behaviour par focus.         | Interface ke design par focus.                 |
| Parent ki jagah child safely use ho.        | Unnecessary methods implement na karne padein. |
| Behavioural compatibility ensure karta hai. | Focused interfaces encourage karta hai.        |

---

## 12. Common Mistakes

| Mistake                                       | Correct Approach                          |
| --------------------------------------------- | ----------------------------------------- |
| Ek hi huge interface banana                   | Small focused interfaces banao            |
| Har class ko sabhi methods implement karwana  | Required capabilities hi implement karwao |
| Empty methods likhna                          | Interface ko properly divide karo         |
| Unrelated methods ko ek interface mein rakhna | Related methods ko group karo             |
| Bahut zyada tiny interfaces banana            | Meaningful aur useful interfaces banao    |

**Important:** ISP ka matlab ye nahi ki har method ke liye alag interface bana do. Interfaces ko logically related responsibilities ke according divide karna chahiye.

---

## 13. Interview Questions and Answers

### Q1. What is ISP?

Clients should not be forced to depend on interfaces they do not use.

### Q2. What is the full form of ISP?

Interface Segregation Principle.

### Q3. ISP SOLID ka kaunsa principle hai?

Fourth principle.

### Q4. Who popularized ISP?

Robert C. Martin.

### Q5. Why do we use ISP?

Unnecessary dependencies aur unwanted methods ko avoid karne ke liye.

### Q6. What is a fat interface?

Aisa interface jisme bahut saare unrelated ya unnecessary methods hon.

### Q7. How can we follow ISP?

Large interfaces ko smaller, focused interfaces mein divide karke.

### Q8. Can a class implement multiple interfaces?

Haan. Agar class ko multiple capabilities chahiye, toh woh multiple interfaces implement kar sakti hai.

### Q9. Is ISP useful in MERN?

Haan. Services, repositories, TypeScript interfaces aur component contracts ko focused rakhne mein useful hai.

### Q10. Does ISP mean one interface per method?

Nahi. Related methods ko meaningful groups mein rakhna chahiye.

---

## 14. Practice Tasks

### Task 1: Worker System

- Workable interface banao.
- Eatable interface banao.
- Sleepable interface banao.
- Human aur Robot classes banao.
- Ensure karo Robot unnecessary methods implement na kare.

### Task 2: Printer System

- Printable interface banao.
- Scannable interface banao.
- Faxable interface banao.
- SimplePrinter aur MultiFunctionPrinter classes banao.

### Task 3: E-commerce System

TypeScript mein separate interfaces banao:

- UserService
- ProductService
- OrderService
- PaymentService

Har interface mein sirf relevant methods rakho.

---

## 15. Quick Revision

- ISP = Interface Segregation Principle.
- SOLID ka fourth principle.
- Robert C. Martin ne popularize kiya.
- Clients ko unnecessary methods par depend nahi karna chahiye.
- Large interfaces ko smaller focused interfaces mein divide karo.
- Har class ko required capabilities hi implement karni chahiye.
- ISP coupling kam karne mein help karta hai.
- TypeScript mein interfaces ke through ISP implement kar sakte hain.
- ISP ka matlab one interface per method nahi hai.

---

## 16. Topic Completion Checklist

- [ ] ISP ka meaning samajh aa gaya.
- [ ] Worker example samajh aa gaya.
- [ ] Wrong vs Correct design samajh aa gaya.
- [ ] TypeScript interfaces samajh aa gaye.
- [ ] C++ example samajh aa gaya.
- [ ] MERN example samajh aa gaya.
- [ ] SRP aur ISP ka difference samajh aa gaya.
- [ ] Practice tasks complete kar liye.

**Topic 14 Complete: Interface Segregation Principle (ISP).**
