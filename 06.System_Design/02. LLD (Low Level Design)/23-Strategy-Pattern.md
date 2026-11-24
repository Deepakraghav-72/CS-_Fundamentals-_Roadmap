# 23. Strategy Pattern

## 1. Strategy Pattern kya hota hai?

Strategy Pattern ek **Behavioral Design Pattern** hai.

Iska main purpose different algorithms ya behaviors ko separate classes ya objects mein rakhna aur unhe interchangeably use karna hai.

Simple language mein:

**Strategy Pattern humein ek hi kaam ko perform karne ke multiple methods provide karta hai, jismein hum requirement ke according kisi bhi method ko select kar sakte hain.**

### Real-Life Example

Maan lo tumhe ek city se doosri city jaana hai.

Tumhare paas different travel options hain:

- Car
- Bike
- Train
- Bus

Tumhara main goal destination tak pahunchna hai.

Lekin tum situation ke according travel method change kar sakte ho.

Software mein Strategy Pattern bhi isi tarah kaam karta hai.

Ek task ke liye multiple strategies hoti hain aur requirement ke according strategy select ki jaati hai.

## 2. Strategy Pattern ki zaroorat kyon padti hai?

Maan lo tum ek E-commerce application bana rahe ho.

Application mein different discount methods hain:

- 10% Discount
- 20% Discount
- Festival Discount

Without Strategy Pattern:

```javascript
function calculateDiscount(type, price) {
  if (type === "NORMAL") {
    return price * 0.1;
  }

  if (type === "PREMIUM") {
    return price * 0.2;
  }

  if (type === "FESTIVAL") {
    return price * 0.3;
  }

  return 0;
}
```

### Is approach ki problems

1. Different algorithms ek hi function mein likhe hue hain.
2. New discount add karne par function modify karna padta hai.
3. Function bada aur difficult to maintain ho sakta hai.
4. Testing individual algorithms difficult ho sakti hai.
5. Code mein conditions badhti jaati hain.

Strategy Pattern mein hum har algorithm ko separate rakh sakte hain.

## 3. Strategy Pattern ka Basic Working

Strategy Pattern mein generally ye components hote hain:

1. Strategy Interface/Contract
2. Concrete Strategies
3. Context
4. Client

Diagram:

```text
             Client
                |
                v
             Context
                |
                v
         Strategy Contract
           /     |     \
          /      |      \
         v       v       v
     Strategy  Strategy Strategy
         A       B       C
```

Client requirement ke according Context ko strategy provide karta hai.

Context selected strategy ka behavior execute karta hai.

## 4. Strategy Pattern Example in JavaScript

Maan lo hum discount calculation system bana rahe hain.

### Step 1: Different Strategies Create Karo

```javascript
class NormalDiscount {
  calculate(price) {
    return price * 0.1;
  }
}

class PremiumDiscount {
  calculate(price) {
    return price * 0.2;
  }
}

class FestivalDiscount {
  calculate(price) {
    return price * 0.3;
  }
}
```

Har class ka kaam discount calculate karna hai, lekin algorithm alag hai.

### Step 2: Context Class Create Karo

```javascript
class ShoppingCart {
  constructor(discountStrategy) {
    this.discountStrategy = discountStrategy;
  }

  setDiscountStrategy(strategy) {
    this.discountStrategy = strategy;
  }

  calculateFinalPrice(price) {
    const discount = this.discountStrategy.calculate(price);

    return price - discount;
  }
}
```

ShoppingCart ko nahi pata ki discount kaise calculate ho raha hai.

Wo sirf selected strategy ka `calculate()` method call karta hai.

### Step 3: Strategy Use Karo

```javascript
const cart = new ShoppingCart(new NormalDiscount());

console.log(cart.calculateFinalPrice(1000));
```

Output:

```text
900
```

### Premium Discount

```javascript
cart.setDiscountStrategy(new PremiumDiscount());

console.log(cart.calculateFinalPrice(1000));
```

Output:

```text
800
```

### Festival Discount

```javascript
cart.setDiscountStrategy(new FestivalDiscount());

console.log(cart.calculateFinalPrice(1000));
```

Output:

```text
700
```

Ab hum same ShoppingCart object ke andar strategy change kar sakte hain.

## 5. Code ko Step-by-Step Samjho

### Step 1: Strategy Create Hui

```javascript
new NormalDiscount();
```

Normal discount algorithm ka object create hua.

### Step 2: Context ko Strategy Di

```javascript
const cart = new ShoppingCart(new NormalDiscount());
```

ShoppingCart ko selected strategy mil gayi.

### Step 3: Calculation Call Hui

```javascript
cart.calculateFinalPrice(1000);
```

ShoppingCart internally strategy ka `calculate()` method call karta hai.

### Step 4: Strategy Change Hui

```javascript
cart.setDiscountStrategy(new FestivalDiscount());
```

Ab ShoppingCart festival discount algorithm use karega.

**Important:** JavaScript mein Java ya C++ ki tarah interface keyword built-in nahi hai. Hum same method contract follow karke Strategy Pattern implement kar sakte hain.

## 6. Strategy Pattern ke Main Components

### 1. Strategy

Common behavior ka contract define karta hai.

Example: `calculate(price)`.

JavaScript mein ye convention ya abstract base class ke through represent ho sakta hai.

### 2. Concrete Strategy

Actual algorithm implement karti hai.

Example:

- NormalDiscount
- PremiumDiscount
- FestivalDiscount

### 3. Context

Context selected strategy ko store karta hai aur uska use karta hai.

Example: ShoppingCart.

### 4. Client

Client decide karta hai ki kaunsi strategy use karni hai.

Example: Application code jo ShoppingCart ko strategy provide karta hai.

## 7. Strategy Pattern ka Real-World Example: Payment Methods

Maan lo application mein multiple payment methods hain.

- UPI
- Card
- Net Banking

Har payment method ka process alag ho sakta hai.

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

class PaymentProcessor {
  constructor(strategy) {
    this.strategy = strategy;
  }

  setStrategy(strategy) {
    this.strategy = strategy;
  }

  processPayment(amount) {
    this.strategy.pay(amount);
  }
}

const processor = new PaymentProcessor(new UpiPayment());

processor.processPayment(500);

processor.setStrategy(new CardPayment());

processor.processPayment(1000);
```

Output:

```text
Paid 500 using UPI
Paid 1000 using Card
```

Ye example pattern samjhane ke liye hai. Real payment processing mein payment gateway, authentication, transaction verification aur error handling bhi required hote hain.

## 8. Strategy Pattern vs If-Else

| If-Else Approach                                                   | Strategy Pattern                                   |
| ------------------------------------------------------------------ | -------------------------------------------------- |
| Algorithms ek function mein ho sakte hain                          | Algorithms separate objects mein hote hain         |
| Conditions badh sakti hain                                         | Strategies independently manage hoti hain          |
| New algorithm ke liye existing function modify karna pad sakta hai | New strategy add karke extend kar sakte hain       |
| Simple cases mein useful                                           | Multiple interchangeable algorithms mein useful    |
| Testing mixed logic difficult ho sakti hai                         | Individual strategies test karna easy ho sakta hai |

## 9. Strategy Pattern vs State Pattern

Dono Behavioral Design Patterns hain, lekin inka purpose alag hai.

| Strategy Pattern                      | State Pattern                                                  |
| ------------------------------------- | -------------------------------------------------------------- |
| Different algorithms select karta hai | Object ke current state ke according behavior change karta hai |
| Client strategy select kar sakta hai  | State transition se behavior change ho sakta hai               |
| Focus: How to perform a task          | Focus: Object kis state mein hai                               |
| Example: Payment methods              | Example: Order status                                          |

### Easy Example

Strategy:

Tum decide karte ho ki payment UPI se karni hai ya Card se.

State:

Order ka behavior uske current status ke according change hota hai, jaise Pending, Shipped ya Delivered.

## 10. Strategy Pattern vs Factory Pattern

| Strategy Pattern                     | Factory Pattern                          |
| ------------------------------------ | ---------------------------------------- |
| Behavior/algorithm select karta hai  | Object creation organize karta hai       |
| Behavioral Pattern                   | Factory Method Creational Pattern        |
| Strategies interchangeable hoti hain | Factory required object create karti hai |
| Example: Discount algorithms         | Example: Payment object creation         |

**Remember:**

Factory = Object kaise create hoga?

Strategy = Kaunsa behavior/algorithm use hoga?

## 11. Strategy Pattern ke Advantages

### 1. Loose Coupling

Context concrete strategies par directly depend nahi karta.

### 2. Easy Extension

Nayi strategy add karna comparatively easy hota hai.

### 3. Code Reusability

Strategies ko different contexts mein reuse kar sakte hain.

### 4. Better Testing

Har strategy ko independently test kar sakte hain.

### 5. Runtime Flexibility

Application ke execution ke time strategy change kar sakte hain.

### 6. Cleaner Code

Multiple algorithms ko separate rakh sakte hain.

## 12. Strategy Pattern ke Disadvantages

### 1. More Classes/Objects

Har strategy ke liye separate implementation banani pad sakti hai.

### 2. Extra Complexity

Simple problem ke liye unnecessary abstraction ho sakti hai.

### 3. Client Responsibility

Kai implementations mein client ko suitable strategy select karni padti hai.

### 4. Similar Code

Agar algorithms bahut similar hon, to separate strategies unnecessary duplication create kar sakti hain.

## 13. MERN Stack mein Strategy Pattern

MERN Stack applications mein Strategy Pattern useful ho sakta hai.

### Example 1: Authentication Strategy

Application mein different authentication methods ho sakte hain:

- Email and Password
- Google Login
- OTP Login

Har method ka authentication process alag hai.

In processes ko separate strategies mein organize kiya ja sakta hai.

### Example 2: File Upload Strategy

Application different storage providers use kar sakti hai:

- Local Storage
- AWS S3
- Cloudinary

Har provider ke liye separate upload strategy implement ki ja sakti hai.

### Example 3: Sorting Strategy

Product listing mein different sorting algorithms/criteria ho sakte hain:

- Price Low to High
- Price High to Low
- Newest First
- Popularity

Requirement ke according sorting strategy select ki ja sakti hai.

## 14. Strategy Pattern kab use karna chahiye?

Strategy Pattern use karo jab:

1. Ek task ke multiple algorithms hon.
2. Runtime par algorithm change karna ho.
3. Bahut saare if-else conditions manage karne pad rahe hon.
4. Algorithms ko independently test karna ho.
5. Existing code ko baar-baar modify kiye bina new behavior add karna ho.

### Kab avoid karna chahiye?

1. Sirf ek simple algorithm ho.
2. Different behaviors bahut kam aur stable hon.
3. Separate classes unnecessary complexity create kar rahi hon.

## 15. Common Mistakes

1. Strategy aur State Pattern ko same samajhna.
2. Context ke andar saare algorithms likh dena.
3. Different strategies mein common method contract follow na karna.
4. Invalid strategy handle na karna.
5. Har chhote if-else ke liye Strategy Pattern use karna.
6. Factory aur Strategy ka purpose confuse karna.

## 16. Interview Questions & Answers

### Q1. What is Strategy Pattern?

Strategy Pattern ek Behavioral Design Pattern hai jo different algorithms ko separate karke interchangeable banata hai.

### Q2. Why do we use Strategy Pattern?

Multiple algorithms ko clean aur independently manage karne ke liye.

### Q3. What is Context?

Context wo class hoti hai jo selected strategy ko store karti hai aur uska behavior use karti hai.

### Q4. Can we change strategy at runtime?

Yes. Context mein strategy update karne ka method provide kar sakte hain.

### Q5. What is Concrete Strategy?

Concrete Strategy actual algorithm ki implementation hoti hai.

### Q6. Is Strategy a Creational Pattern?

No. Strategy ek Behavioral Design Pattern hai.

### Q7. What is the difference between Strategy and State?

Strategy algorithms select karne par focus karta hai, jabki State object ke current state ke according behavior change karta hai.

### Q8. What is the main advantage of Strategy Pattern?

Algorithms ko separate rakhna, loose coupling aur easy extension.

### Q9. Does JavaScript support interfaces natively?

No. JavaScript mein built-in interface keyword nahi hai. Common method contract follow karke pattern implement kar sakte hain.

### Q10. Give a real-world example.

Shopping cart mein different discount algorithms ya application mein different payment methods.

## 17. Practical Tasks

### Task 1: Discount Strategy

Three classes banao:

- NormalDiscount
- PremiumDiscount
- FestivalDiscount

Har class mein `calculate(price)` method hona chahiye.

ShoppingCart class banao jo strategy use karke final price calculate kare.

### Task 2: Payment Strategy

Three payment classes banao:

- UpiPayment
- CardPayment
- NetBankingPayment

Ek PaymentProcessor banao jisme strategy runtime par change ho sake.

### Task 3: Sorting Strategy

Different sorting strategies banao:

- PriceLowToHigh
- PriceHighToLow
- NewestFirst

Ek ProductList context banao jo selected strategy ke according products sort kare.

## 18. Quick Revision

| Term              | Meaning                                        |
| ----------------- | ---------------------------------------------- |
| Strategy Pattern  | Different algorithms ko interchangeable banana |
| Category          | Behavioral                                     |
| Strategy          | Common behavior contract                       |
| Concrete Strategy | Actual algorithm                               |
| Context           | Selected strategy use karta hai                |
| Client            | Strategy select/provide karta hai              |
| Runtime Switching | Execution ke time strategy change karna        |

### Important Points

- Strategy Pattern Behavioral Design Pattern hai.
- Multiple algorithms ko separate rakhta hai.
- Context selected strategy ka use karta hai.
- Strategy runtime par change ho sakti hai.
- Factory object creation handle karta hai.
- Strategy behavior selection handle karta hai.
- State Pattern se iska purpose different hai.

## 19. Topic Completion Checklist

- [ ] Strategy Pattern ka meaning samajh liya.
- [ ] Strategy Pattern ki need samajh li.
- [ ] Working flow samajh liya.
- [ ] Strategy aur Concrete Strategy samajh li.
- [ ] Context aur Client samajh liya.
- [ ] JavaScript code samajh liya.
- [ ] Runtime strategy switching samajh li.
- [ ] Strategy vs If-Else samajh liya.
- [ ] Strategy vs State samajh liya.
- [ ] Strategy vs Factory samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Interview questions revise kar liye.
- [ ] Practical tasks complete kar liye.

**Topic 23 Complete: Strategy Pattern**
