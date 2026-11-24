# 13. Liskov Substitution Principle (LSP)

## 1. LSP Kya Hai?

LSP ka full form hai **Liskov Substitution Principle**.

Ye SOLID principles ka third principle hai.

Is principle ko Barbara Liskov ne introduce kiya tha.

### Simple Definition

Agar kisi program mein parent class ka object use ho raha hai, toh uski jagah child class ka object use karne par program ka expected behaviour break nahi hona chahiye.

Simple words mein:

**Child class ko parent class ki jagah safely use kar paana chahiye, bina program ka behaviour kharab kiye.**

### Example

Maan lo hamare paas ek parent class hai:

- `Bird`
- Child classes: `Sparrow` aur `Penguin`

Agar `Bird` class mein `fly()` method hai, toh problem hogi.

Kyunki:

- Sparrow fly kar sakti hai.
- Penguin fly nahi kar sakta.

Agar Penguin ko `Bird` ki jagah use karne par error ya unexpected behaviour aaye, toh LSP violate ho sakta hai.

---

## 2. LSP Ko Simple Example Se Samjho

Maan lo ek function hai:

```javascript
function makeBirdFly(bird) {
  bird.fly();
}
```

Ab hum Sparrow object pass karte hain:

```javascript
class Sparrow {
  fly() {
    console.log("Sparrow is flying");
  }
}

const sparrow = new Sparrow();

makeBirdFly(sparrow);
```

Output:

```text
Sparrow is flying
```

Ye sahi kaam kar raha hai.

Lekin Penguin ke saath:

```javascript
class Penguin {
  fly() {
    throw new Error("Penguins cannot fly");
  }
}

const penguin = new Penguin();

makeBirdFly(penguin);
```

Output:

```text
Error: Penguins cannot fly
```

Problem ye hai ki function ko aisa object chahiye jo fly kar sake, lekin Penguin us requirement ko fulfill nahi karta.

**Yahan design problem hai.**

---

## 3. LSP Follow Karne Ka Correct Way

Har Bird fly nahi kar sakta. Isliye `fly()` method ko general Bird class mein nahi rakhna chahiye.

Hum alag abstraction bana sakte hain.

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

function makeBirdFly(bird) {
  bird.fly();
}

const sparrow = new Sparrow();

makeBirdFly(sparrow);
```

Output:

```text
Bird is flying
```

Ab Penguin ko `makeBirdFly()` mein pass nahi karenge, kyunki woh `FlyingBird` type ka nahi hai.

### Structure

```text
             Bird
               |
       -----------------
       |               |
   FlyingBird       Penguin
       |
    Sparrow
```

**Important:** Inheritance ka use tabhi karo jab child class parent ka expected behaviour properly maintain kar sake.

---

## 4. Real-World Rectangle and Square Example

Ye LSP samajhne ka ek famous example hai.

Maan lo ek Rectangle class hai.

Rectangle mein:

- Width alag set kar sakte hain.
- Height alag set kar sakte hain.
- Area = Width × Height.

### Rectangle Class

```javascript
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  setWidth(width) {
    this.width = width;
  }

  setHeight(height) {
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}
```

Use:

```javascript
const rectangle = new Rectangle(10, 5);

console.log(rectangle.getArea());
```

Output:

```text
50
```

### Problem: Square Inheritance

Square mein width aur height equal hone chahiye.

```javascript
class Square extends Rectangle {
  constructor(side) {
    super(side, side);
  }

  setWidth(width) {
    this.width = width;
    this.height = width;
  }

  setHeight(height) {
    this.width = height;
    this.height = height;
  }
}
```

Ab:

```javascript
function calculateArea(rectangle) {
  rectangle.setWidth(10);
  rectangle.setHeight(5);

  return rectangle.getArea();
}

const rectangle = new Rectangle(10, 5);
console.log(calculateArea(rectangle));

const square = new Square(5);
console.log(calculateArea(square));
```

Output:

```text
50
25
```

Function ko expected tha ki width 10 aur height 5 set karne ke baad area 50 milega.

Lekin Square mein height set karte hi width bhi 5 ho gayi. Isliye area 25 mila.

**Yahan child class ne parent class ke expected behaviour ko change kar diya.**

Is particular mutable Rectangle-Square design mein LSP violate ho raha hai.

Important: Iska matlab ye nahi ki har situation mein Square aur Rectangle ka relationship galat hai. Problem tab hoti hai jab child class parent ke promised behaviour ko maintain nahi kar pati.

---

## 5. Rectangle-Square Problem Ka Better Solution

Dono ko ek common abstraction de sakte hain: `Shape`.

```javascript
class Shape {
  getArea() {
    throw new Error("getArea() must be implemented");
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}

class Square extends Shape {
  constructor(side) {
    super();
    this.side = side;
  }

  getArea() {
    return this.side * this.side;
  }
}
```

Ab common function:

```javascript
function printArea(shape) {
  console.log(shape.getArea());
}

const rectangle = new Rectangle(10, 5);
const square = new Square(5);

printArea(rectangle);
printArea(square);
```

Output:

```text
50
25
```

Dono Shape hain aur dono apna area correctly calculate kar rahe hain.

Yahan common contract `getArea()` hai, jise dono classes correctly follow kar rahi hain.

---

## 6. LSP Ke 3 Important Rules

LSP follow karne ke liye 3 important rules samajhna zaroori hai.

### Rule 1: Subtype Should Not Strengthen Preconditions

Precondition ka matlab hai: method ko call karne se pehle jo conditions satisfy honi chahiye.

Child class ko parent class ke comparison mein extra strict conditions nahi lagani chahiye.

Example:

Parent class:

```javascript
class Payment {
  pay(amount) {
    if (amount <= 0) {
      throw new Error("Invalid amount");
    }

    console.log("Payment successful");
  }
}
```

Agar child class sirf ₹1000 ya usse zyada payment accept kare, toh usne extra condition laga di.

```javascript
class OnlinePayment extends Payment {
  pay(amount) {
    if (amount < 1000) {
      throw new Error("Minimum payment is 1000");
    }

    console.log("Online payment successful");
  }
}
```

Parent ₹500 accept kar sakta tha, lekin child ₹500 reject kar raha hai.

Isliye child ne precondition ko stronger bana diya.

**Rule:** Child class ko parent se zyada strict input requirements nahi rakhni chahiye.

### Rule 2: Subtype Should Not Weaken Postconditions

Postcondition ka matlab hai: method execute hone ke baad jo guarantee milni chahiye.

Child class ko parent ke promised result se kam guarantee nahi deni chahiye.

Example:

Maan lo parent method successful payment ke baad receipt return karne ka promise karta hai.

```javascript
class Payment {
  pay(amount) {
    return {
      success: true,
      receiptId: "R123",
    };
  }
}
```

Child class agar successful payment ke baad receipt dena band kar de, toh parent ka promise break ho jayega.

**Rule:** Child class ko parent ke promised output aur behaviour ko maintain karna chahiye.

### Rule 3: Child Should Preserve Parent Invariants

Invariant ka matlab hai: class ki aisi condition jo hamesha true rehni chahiye.

Example:

Bank account mein balance negative nahi hona chahiye.

```javascript
class BankAccount {
  constructor(balance) {
    if (balance < 0) {
      throw new Error("Balance cannot be negative");
    }

    this.balance = balance;
  }
}
```

Child class ko bhi ye condition maintain karni chahiye.

Agar child class bina valid reason ke negative balance allow kar de, toh parent class ka invariant break ho sakta hai.

**Rule:** Child class ko parent class ki important conditions maintain karni chahiye.

---

## 7. Behavioral Subtyping Kya Hai?

LSP ka ek important concept hai: **Behavioral Subtyping**.

Iska matlab hai ki child class sirf parent class se inherit hi na kare, balki parent ke expected behaviour ko bhi maintain kare.

Sirf method names same hona enough nahi hai.

Example:

```javascript
class Vehicle {
  start() {
    console.log("Vehicle started");
  }
}
```

Agar child class `start()` method ko implement karti hai, lekin uska behaviour parent ke contract se completely alag hai, toh LSP problem ho sakti hai.

**LSP inheritance ke syntax se zyada behaviour aur contract par focus karta hai.**

---

## 8. LSP in C++

C++ mein inheritance aur virtual functions ke through LSP samajh sakte hain.

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual double getArea() const = 0;

    virtual ~Shape() = default;
};

class Rectangle : public Shape {
private:
    double width;
    double height;

public:
    Rectangle(double w, double h) {
        width = w;
        height = h;
    }

    double getArea() const override {
        return width * height;
    }
};

class Square : public Shape {
private:
    double side;

public:
    Square(double s) {
        side = s;
    }

    double getArea() const override {
        return side * side;
    }
};

void printArea(const Shape& shape) {
    cout << shape.getArea() << endl;
}

int main() {
    Rectangle rectangle(10, 5);
    Square square(5);

    printArea(rectangle);
    printArea(square);

    return 0;
}
```

Output:

```text
50
25
```

### Code Explanation

- `Shape` ek abstract class hai.
- `getArea()` ek pure virtual function hai.
- Rectangle apne formula se area calculate karta hai.
- Square apne formula se area calculate karta hai.
- `printArea()` kisi bhi Shape ka area print kar sakta hai.
- Dono child classes common contract follow kar rahi hain.

---

## 9. LSP in MERN Stack

MERN Stack mein bhi LSP ka use samajhna important hai.

MERN Stack:

- MongoDB
- Express.js
- React.js
- Node.js

Maan lo tumhare application mein multiple payment providers hain:

- Razorpay
- Stripe

Tum ek common payment contract define kar sakte ho.

### JavaScript Example

```javascript
class PaymentService {
  async pay(amount) {
    throw new Error("pay() must be implemented");
  }
}

class RazorpayService extends PaymentService {
  async pay(amount) {
    return {
      success: true,
      provider: "Razorpay",
      amount,
    };
  }
}

class StripeService extends PaymentService {
  async pay(amount) {
    return {
      success: true,
      provider: "Stripe",
      amount,
    };
  }
}
```

Common function:

```javascript
async function processPayment(paymentService, amount) {
  return await paymentService.pay(amount);
}
```

Use:

```javascript
const razorpay = new RazorpayService();
const stripe = new StripeService();

processPayment(razorpay, 500);
processPayment(stripe, 500);
```

Dono services ko same expected contract follow karna chahiye.

Real application mein payment providers ke actual responses, errors, validation aur security rules ko bhi properly handle karna hota hai.

**Note:** JavaScript mein TypeScript jaisi compile-time interface checking built-in nahi hoti. Isliye contract ko tests aur validation ke through enforce karna useful hota hai.

---

## 10. LSP and Inheritance

| Inheritance                                      | LSP                                           |
| ------------------------------------------------ | --------------------------------------------- |
| Parent-child relationship banata hai.            | Parent-child behaviour ko correct rakhta hai. |
| Code reuse mein help karta hai.                  | Safe substitution ensure karta hai.           |
| Syntax aur structure se related hai.             | Behaviour aur contract se related hai.        |
| Har inheritance automatically correct nahi hoti. | Correct behavioural relationship zaroori hai. |

**Yaad rakho:** Har child class ko parent class se inherit karna hi chahiye, aisa nahi hai.

Inheritance tabhi use karo jab child parent ke expected behaviour ko maintain kar sake.

---

## 11. LSP and OCP Relationship

OCP ka full form hai Open/Closed Principle.

OCP kehta hai:

Software entities extension ke liye open aur modification ke liye closed honi chahiye.

LSP ensure karta hai ki naye child classes add karne par existing code ka expected behaviour break na ho.

Example:

Agar payment system mein naya payment provider add karna hai, toh use existing payment contract follow karna chahiye.

- OCP: Naya provider add karna easy ho.
- LSP: Naya provider existing code ke saath correctly work kare.

Dono principles ek dusre ko support karte hain.

---

## 12. LSP Ke Advantages

1. Code reliable banta hai.
2. Unexpected errors kam hote hain.
3. Inheritance ka correct use hota hai.
4. Code reusable banta hai.
5. Testing easy hoti hai.
6. Existing code mein new child classes add karna safer hota hai.
7. Maintenance easy hoti hai.

## 13. LSP Follow Na Karne Ke Disadvantages

1. Child class unexpected behaviour de sakti hai.
2. Runtime errors aa sakte hain.
3. Parent class par depend karne wala code break ho sakta hai.
4. Code maintain karna difficult ho sakta hai.
5. Inheritance hierarchy confusing ho sakti hai.

---

## 14. Common Mistakes

| Mistake                                         | Correct Approach                                       |
| ----------------------------------------------- | ------------------------------------------------------ |
| Har related class mein inheritance use karna    | Inheritance tabhi use karo jab behaviour compatible ho |
| Child method mein unsupported error throw karna | Suitable abstraction design karo                       |
| Parent ka expected output change kar dena       | Parent contract maintain karo                          |
| Extra strict input conditions lagana            | Parent ki preconditions follow karo                    |
| Parent ke invariants ignore karna               | Important conditions preserve karo                     |
| Sirf same method name ko LSP samajhna           | Actual behaviour check karo                            |

---

## 15. Interview Questions and Answers

### Q1. What is Liskov Substitution Principle?

LSP kehta hai ki parent class ke object ki jagah child class ka object use karne par program ka expected behaviour break nahi hona chahiye.

### Q2. Who introduced LSP?

Barbara Liskov.

### Q3. LSP belongs to which SOLID principle number?

Third principle.

### Q4. What is behavioral subtyping?

Child class ka parent class ke expected behaviour aur contract ko maintain karna behavioral subtyping hai.

### Q5. Can every child class replace its parent class?

Nahi. Child class tabhi replace kar sakti hai jab woh parent ke expected behaviour ko correctly maintain kare.

### Q6. Explain Rectangle-Square problem.

Mutable Rectangle mein width aur height independently change ho sakti hain. Square mein dono equal hoti hain. Agar Square setters ko override karke parent ka expected behaviour change kar de, toh LSP violate ho sakta hai.

### Q7. What are preconditions?

Method call hone se pehle satisfy hone wali conditions.

### Q8. What are postconditions?

Method execute hone ke baad milne wali guarantees.

### Q9. What are invariants?

Class ki important conditions jo hamesha true rehni chahiye.

### Q10. What is the relationship between LSP and OCP?

OCP extension ko easy banata hai, aur LSP ensure karta hai ki new implementations existing code ke expected behaviour ko break na karein.

---

## 16. Practice Tasks

### Task 1: Bird Example

Ek Bird class banao.

- `eat()` method rakho.
- `FlyingBird` class banao.
- `Sparrow` ko FlyingBird se inherit karao.
- `Penguin` ko Bird se inherit karao.
- Ensure karo Penguin ko fly karne ke liye force na kiya jaye.

### Task 2: Shape Example

- Shape base class banao.
- Rectangle class banao.
- Square class banao.
- Dono mein `getArea()` implement karo.
- Ek common function se dono ka area print karao.

### Task 3: Payment System

- PaymentService class banao.
- RazorpayService banao.
- StripeService banao.
- Dono ko same expected payment contract follow karwao.

---

## 17. Quick Revision

- LSP = Liskov Substitution Principle.
- SOLID ka third principle.
- Barbara Liskov ne introduce kiya.
- Child class parent ki jagah safely use honi chahiye.
- Parent ka expected behaviour break nahi hona chahiye.
- Child ko extra strict preconditions nahi lagani chahiye.
- Child ko parent ki postconditions weaken nahi karni chahiye.
- Parent ke invariants maintain hone chahiye.
- Sirf inheritance kar lena LSP follow karna nahi hai.
- Behavioural compatibility sabse important hai.

---

## 18. Topic Completion Checklist

- [ ] LSP ka meaning samajh aa gaya.
- [ ] Bird-Penguin example samajh aa gaya.
- [ ] Rectangle-Square problem samajh aa gayi.
- [ ] Correct design approach samajh aa gaya.
- [ ] Preconditions, postconditions aur invariants samajh aa gaye.
- [ ] C++ example samajh aa gaya.
- [ ] MERN payment example samajh aa gaya.
- [ ] Practice tasks complete kar liye.

**Topic 13 Complete: Liskov Substitution Principle (LSP).**
