# Interfaces & Abstract Classes

## 1. Introduction

OOP mein kabhi-kabhi humein aisi classes banani hoti hain jinka purpose sirf objects create karna nahi, balki doosri classes ke liye rules ya common structure define karna hota hai.

Iske liye do important concepts hain:

1. Abstract Class
2. Interface

**Simple language:**

- Abstract Class: Aisi incomplete class jise directly object banane ke liye use nahi kar sakte.
- Interface: Aisa contract jo batata hai ki kisi class mein kaun-kaun se methods hone chahiye.

Example:

Maan lo hum ek payment system bana rahe hain.

Payment ke multiple methods hain:

- Credit Card Payment
- UPI Payment
- Net Banking Payment

Teeno payment methods ka kaam alag hai, lekin teeno mein payment karne ka method hona chahiye.

Hum common structure define kar sakte hain.

---

## 2. Abstract Class

### Definition

Abstract Class ek aisi class hoti hai jisme abstract methods aur normal methods dono ho sakte hain.

Abstract class ka directly object create nahi kar sakte.

Iska use generally doosri classes ko common structure aur functionality provide karne ke liye hota hai.

### Simple example

```text
        Payment (Abstract Class)
                 |
          ---------------
          |             |
      UPI Payment   Card Payment
```

Payment ek abstract class hai.

UPI Payment aur Card Payment usse inherit karte hain.

### Abstract Class in C++

C++ mein abstract class banane ke liye at least ek pure virtual function hona zaroori hai.

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
        cout << "Payment through UPI";
    }
};

int main() {
    UPI p1;
    p1.pay();

    return 0;
}
```

**Output:**

```text
Payment through UPI
```

### Explanation

1. `Payment` naam ki abstract class banayi.
2. Uske andar `virtual void pay() = 0;` likha.
3. `= 0` function ko pure virtual banata hai.
4. Is wajah se Payment abstract class ban gayi.
5. UPI class ne Payment ko inherit kiya.
6. UPI class ne `pay()` method implement kiya.
7. UPI ka object create karke method call kiya.

### Important points

- Abstract class ka direct object nahi bana sakte.
- Abstract class mein normal methods ho sakte hain.
- Abstract class mein constructors ho sakte hain.
- Abstract class mein data members ho sakte hain.
- Derived class ko inherited pure virtual functions implement karne padte hain, warna woh bhi abstract rahegi.

### Abstract class ka object kyon nahi banta?

Kyunki abstract class incomplete ho sakti hai.

Example:

Payment ka kaam payment karna hai, lekin payment kis method se hogi, ye UPI ya Card class decide karegi.

Isliye hum directly Payment ka object nahi bana sakte.

---

## 3. Interface

### Definition

Interface ek contract hota hai jo define karta hai ki kisi class mein kaunse methods hone chahiye.

Interface batata hai **WHAT TO DO**, lekin implementation generally implementing class provide karti hai.

### Simple example

Maan lo hum ek application bana rahe hain jisme multiple payment methods hain.

Har payment method mein `pay()` method hona chahiye.

```text
        Payment Interface
                |
        -----------------
        |               |
      UPI             Card
```

Dono classes ko `pay()` method implement karna hoga.

### Interface in C++

C++ mein `interface` naam ka separate keyword nahi hota.

Hum pure abstract class ke through interface jaisa structure create kar sakte hain.

```cpp
#include <iostream>
using namespace std;

class PaymentInterface {
public:
    virtual void pay() = 0;

    virtual ~PaymentInterface() = default;
};

class UPI : public PaymentInterface {
public:
    void pay() override {
        cout << "UPI Payment Successful";
    }
};

class Card : public PaymentInterface {
public:
    void pay() override {
        cout << "Card Payment Successful";
    }
};

int main() {
    UPI p1;
    Card p2;

    p1.pay();
    cout << endl;

    p2.pay();

    return 0;
}
```

**Output:**

```text
UPI Payment Successful
Card Payment Successful
```

### Explanation

- `PaymentInterface` ek pure abstract class hai.
- Ismein `pay()` method declare kiya gaya hai.
- UPI aur Card dono ne ise inherit kiya.
- Dono classes ne apne according `pay()` implement kiya.

`virtual ~PaymentInterface() = default;` virtual destructor hai. Isse base class pointer ke through derived object delete karne par correct destructor call hota hai.

**Yaad rakho:** C++ mein interface banane ke liye generally pure abstract class use hoti hai.

---

## 4. Interface in JavaScript

JavaScript mein bhi `interface` naam ka built-in class-level keyword nahi hota.

Lekin hum abstract class ke through interface jaisa contract implement kar sakte hain.

```javascript
class Payment {
  pay() {
    throw new Error("pay() method must be implemented");
  }
}

class UPI extends Payment {
  pay() {
    console.log("UPI Payment Successful");
  }
}

class Card extends Payment {
  pay() {
    console.log("Card Payment Successful");
  }
}

const p1 = new UPI();
const p2 = new Card();

p1.pay();
p2.pay();
```

**Output:**

```text
UPI Payment Successful
Card Payment Successful
```

### Explanation

- Payment class ek common contract provide kar rahi hai.
- `pay()` ko child classes mein implement karna expected hai.
- UPI aur Card apna implementation provide karte hain.
- Agar base class ka `pay()` directly call karoge, toh error throw hoga.

**Important:** JavaScript mein ye language-enforced interface nahi hai. Ye ek coding pattern hai. TypeScript mein actual `interface` keyword available hai.

---

## 5. Interface in TypeScript

MERN ecosystem mein TypeScript ka use hota hai. Ismein interface directly available hai.

```typescript
interface Payment {
  pay(): void;
}

class UPI implements Payment {
  pay(): void {
    console.log("UPI Payment Successful");
  }
}

class Card implements Payment {
  pay(): void {
    console.log("Card Payment Successful");
  }
}

const p1: Payment = new UPI();
const p2: Payment = new Card();

p1.pay();
p2.pay();
```

**Output:**

```text
UPI Payment Successful
Card Payment Successful
```

### Important keywords

- `interface`: Contract define karta hai.
- `implements`: Class batati hai ki woh interface ka contract follow karegi.
- `extends`: Class kisi doosri class se inherit karti hai.

---

## 6. Abstract Class vs Interface

| Feature         | Abstract Class                   | Interface                     |
| --------------- | -------------------------------- | ----------------------------- |
| Main purpose    | Common structure aur behavior    | Contract define karna         |
| Object creation | Directly nahi                    | Directly nahi                 |
| Normal methods  | Ho sakte hain                    | Language par depend karta hai |
| Data members    | Ho sakte hain                    | Language par depend karta hai |
| Constructor     | Ho sakta hai                     | Generally nahi                |
| Implementation  | Abstract aur normal methods dono | Mainly contract               |
| C++             | Abstract class se                | Pure abstract class se        |
| TypeScript      | `abstract class`                 | `interface`                   |

**Note:** Interface ke features programming language ke according change hote hain. Upar diya comparison beginner-level general understanding ke liye hai.

---

## 7. Abstract Class vs Normal Class

| Normal Class                         | Abstract Class                             |
| ------------------------------------ | ------------------------------------------ |
| Direct object bana sakte hain        | Direct object nahi bana sakte              |
| Complete ya concrete implementation  | Incomplete methods ho sakte hain           |
| Object creation ke liye use hoti hai | Common base structure ke liye use hoti hai |

Example:

```cpp
class Animal {
public:
    void eat() {
        cout << "Animal is eating";
    }
};
```

Ye normal class hai.

```cpp
class Animal {
public:
    virtual void sound() = 0;
};
```

Ye abstract class hai.

---

## 8. Multiple Interfaces

Kabhi-kabhi ek class ko multiple contracts follow karne pad sakte hain.

Example:

Ek SmartPhone:

- Call kar sakta hai.
- Camera use kar sakta hai.
- Internet access kar sakta hai.

### TypeScript example

```typescript
interface Camera {
  takePhoto(): void;
}

interface Phone {
  makeCall(): void;
}

class SmartPhone implements Camera, Phone {
  takePhoto(): void {
    console.log("Photo taken");
  }

  makeCall(): void {
    console.log("Calling...");
  }
}

const mobile = new SmartPhone();

mobile.takePhoto();
mobile.makeCall();
```

**Output:**

```text
Photo taken
Calling...
```

Ek class multiple interfaces implement kar sakti hai.

C++ mein ek class multiple abstract base classes ko inherit karke aisa design bana sakti hai.

---

## 9. Real-Life Example

### Payment System

Maan lo ek e-commerce application hai.

User payment kar sakta hai:

- UPI
- Credit Card
- Net Banking

Sabhi payment types ka common contract hoga: `pay()`.

Lekin payment process alag hoga.

```typescript
interface Payment {
  pay(amount: number): void;
}

class UPI implements Payment {
  pay(amount: number): void {
    console.log(`Paid ₹${amount} using UPI`);
  }
}

class CreditCard implements Payment {
  pay(amount: number): void {
    console.log(`Paid ₹${amount} using Credit Card`);
  }
}

function checkout(payment: Payment, amount: number) {
  payment.pay(amount);
}

checkout(new UPI(), 500);
checkout(new CreditCard(), 1000);
```

**Output:**

```text
Paid ₹500 using UPI
Paid ₹1000 using Credit Card
```

### Is example se kya seekha?

- Payment interface ne contract define kiya.
- UPI ne apna implementation diya.
- CreditCard ne apna implementation diya.
- Checkout function ko implementation ki details jaanne ki zaroorat nahi hai.

Yahi flexible design hai.

---

## 10. MERN Stack Mein Use

MERN projects mein TypeScript use karte waqt interfaces aur abstract classes helpful hote hain.

### Interface ka use

API response ka structure define karne ke liye:

```typescript
interface User {
  name: string;
  email: string;
  age: number;
}

const user: User = {
  name: "Rahul",
  email: "rahul@example.com",
  age: 22,
};
```

Ab TypeScript check karega ki `user` object mein required properties hain ya nahi.

### Abstract class ka use

Common service logic define karne ke liye:

```typescript
abstract class BaseService {
  log(message: string): void {
    console.log(message);
  }

  abstract execute(): void;
}

class UserService extends BaseService {
  execute(): void {
    this.log("User service executed");
  }
}

const service = new UserService();
service.execute();
```

**Output:**

```text
User service executed
```

Note: TypeScript interfaces compile hone ke baad JavaScript output mein exist nahi karte. Ye primarily compile-time type checking ke liye hote hain.

---

## 11. Advantages

### Abstract Class

1. Common code reuse kar sakte hain.
2. Common structure define kar sakte hain.
3. Data members aur constructors rakh sakte hain.
4. Child classes ko required methods implement karne ke liye force kar sakte hain.

### Interface

1. Common contract define hota hai.
2. Different classes same contract follow kar sakti hain.
3. Code loosely coupled ho sakta hai.
4. Multiple interfaces implement kiye ja sakte hain.
5. Testing aur maintenance easy ho sakti hai.

---

## 12. Common Mistakes

1. Abstract class ka direct object banane ki koshish karna.
2. C++ mein `= 0` ka meaning na samajhna.
3. C++ mein assume karna ki `interface` naam ka keyword hota hai.
4. JavaScript mein TypeScript interface jaisa built-in feature samajhna.
5. `implements` aur `extends` ko same samajhna.
6. Abstract class aur interface ko har programming language mein identical samajhna.
7. Ye sochna ki interface mein har language mein sirf methods hi ho sakte hain.

---

## 13. Interview Questions and Answers

**Q1. What is an Abstract Class?**

Aisi class jiska direct object create nahi kar sakte aur jisme abstract aur normal methods ho sakte hain.

**Q2. What is an Interface?**

Interface ek contract hai jo class ke required structure ko define karta hai.

**Q3. Can we create an object of an Abstract Class?**

No, abstract class ka direct object create nahi kar sakte.

**Q4. Does C++ have an interface keyword?**

No. C++ mein pure abstract class ke through interface-like structure banate hain.

**Q5. Does JavaScript support interfaces directly?**

No. JavaScript mein built-in interface keyword nahi hai. TypeScript mein interface available hai.

**Q6. What is the difference between `extends` and `implements`?**

- `extends`: Class inheritance ke liye.
- `implements`: Interface ka contract follow karne ke liye.

**Q7. Can a class implement multiple interfaces?**

Yes, TypeScript mein ek class multiple interfaces implement kar sakti hai.

**Q8. Can an Abstract Class have a constructor?**

Yes, abstract class mein constructor ho sakta hai.

**Q9. Can an Abstract Class have normal methods?**

Yes, abstract class mein normal aur abstract dono methods ho sakte hain.

**Q10. When should we use an Interface?**

Jab different classes ke liye common contract define karna ho.

---

## 14. Practice Tasks

### Task 1: Shape Interface

TypeScript mein `Shape` interface banao.

Ismein `area()` method define karo.

Do classes banao:

- Circle
- Rectangle

Dono mein apne according area calculate karo.

### Task 2: Abstract Animal Class

C++ mein Animal abstract class banao.

- Pure virtual method: `sound()`
- Normal method: `eat()`

Dog aur Cat classes banao.

### Task 3: Payment System

TypeScript mein Payment interface banao.

UPI aur CreditCard classes se implement karo.

### Task 4: Multiple Interfaces

TypeScript mein do interfaces banao:

- Camera
- MusicPlayer

SmartPhone class mein dono implement karo.

---

## 15. Quick Revision

| Term           | Meaning                                       |
| -------------- | --------------------------------------------- |
| Abstract Class | Incomplete base class                         |
| Interface      | Contract                                      |
| `virtual`      | C++ mein virtual function declare karta hai   |
| `= 0`          | C++ mein pure virtual function                |
| `extends`      | Inheritance                                   |
| `implements`   | Interface contract follow karna               |
| `abstract`     | TypeScript mein abstract class/method ke liye |
| `interface`    | TypeScript mein contract define karne ke liye |

### One-line Revision

- Abstract Class = Common structure + shared behavior.
- Interface = Contract.
- C++ Interface = Pure abstract class ka pattern.
- JavaScript = Direct interface keyword nahi.
- TypeScript = Interface keyword available.
- `extends` = Inheritance.
- `implements` = Interface implementation.

---

## 16. Topic Completion Checklist

- [ ] Abstract Class samajh li.
- [ ] Interface samajh li.
- [ ] C++ examples samajh liye.
- [ ] JavaScript example samajh liya.
- [ ] TypeScript interface samajh liya.
- [ ] Abstract Class vs Interface difference samajh liya.
- [ ] Multiple Interfaces samajh liye.
- [ ] MERN examples samajh liye.
- [ ] Interview questions revise kar liye.
- [ ] Practice tasks complete kar liye.

**Topic 09 Complete: Interfaces & Abstract Classes**
