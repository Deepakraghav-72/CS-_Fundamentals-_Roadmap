# Topic 26: Decorator & Facade Design Patterns

## 1. Structural Design Patterns kya hote hain?

Structural Design Patterns batate hain ki different classes aur objects ko kaise combine karke ek better structure banaya ja sakta hai.

Inka main focus hota hai:

- Objects ke beech relationships banana.
- Code ko flexible aur maintainable banana.
- Complex structure ko manage karna easy banana.

Examples:

1. Decorator Pattern
2. Facade Pattern
3. Adapter Pattern
4. Proxy Pattern
5. Composite Pattern

Is topic mein Decorator aur Facade padhenge.

---

# PART A: DECORATOR PATTERN

## 2. Decorator Pattern kya hai?

Decorator Pattern ek Structural Design Pattern hai jo kisi existing object ke behavior mein additional functionality add karta hai, bina uski original class ko modify kiye.

Simple language mein:

Maan lo tumhare paas ek simple coffee hai. Tum usmein:

- Milk add kar sakte ho.
- Sugar add kar sakte ho.
- Cream add kar sakte ho.

Har baar coffee ki original class change karne ki zarurat nahi hoti. Hum decorators ki help se additional features add kar sakte hain.

Yahi Decorator Pattern hai.

### Real-life example

Ek simple coffee ki cost ₹50 hai.

| Coffee                        | Cost |
| ----------------------------- | ---: |
| Simple Coffee                 |  ₹50 |
| Coffee + Milk                 |  ₹60 |
| Coffee + Milk + Sugar         |  ₹65 |
| Coffee + Milk + Sugar + Cream |  ₹80 |

Har additional feature coffee ko decorate kar raha hai.

## 3. Decorator Pattern ki need kyu hoti hai?

Maan lo tum ek coffee application bana rahe ho.

Agar har combination ke liye separate class banaoge:

- SimpleCoffee
- MilkCoffee
- SugarCoffee
- MilkSugarCoffee
- MilkSugarCreamCoffee

To combinations badhne par classes ki sankhya bahut badh jayegi.

Is problem ko **Class Explosion** kaha ja sakta hai.

Decorator Pattern se hum additional features ko dynamically combine kar sakte hain.

## 4. Decorator Pattern ke main components

Decorator Pattern mein generally ye components hote hain:

1. **Component:** Common contract ya interface.
2. **Concrete Component:** Original object.
3. **Decorator:** Wrapper jo original object ko contain karta hai.
4. **Concrete Decorator:** Additional behavior add karta hai.
5. **Client:** In objects ko use karta hai.

### Structure

```text
             Component
                 |
        -------------------
        |                 |
 ConcreteComponent    Decorator
                          |
                   Concrete Decorators
                    /             \
              MilkDecorator   SugarDecorator
```

## 5. Decorator Pattern – JavaScript Example

JavaScript mein interfaces built-in nahi hote. Isliye hum common methods ka same contract follow karenge.

### Step 1: Base Coffee

```javascript
class SimpleCoffee {
  getDescription() {
    return "Simple Coffee";
  }

  getCost() {
    return 50;
  }
}
```

Ye hamari original coffee class hai.

### Step 2: Base Decorator

```javascript
class CoffeeDecorator {
  constructor(coffee) {
    this.coffee = coffee;
  }

  getDescription() {
    return this.coffee.getDescription();
  }

  getCost() {
    return this.coffee.getCost();
  }
}
```

Is class ka kaam existing coffee object ko wrap karna hai.

`this.coffee` ke through original object ke methods call hote hain.

### Step 3: Milk Decorator

```javascript
class MilkDecorator extends CoffeeDecorator {
  getDescription() {
    return this.coffee.getDescription() + " + Milk";
  }

  getCost() {
    return this.coffee.getCost() + 10;
  }
}
```

Milk add karne par:

- Description mein Milk add hoga.
- Cost mein ₹10 add honge.

### Step 4: Sugar Decorator

```javascript
class SugarDecorator extends CoffeeDecorator {
  getDescription() {
    return this.coffee.getDescription() + " + Sugar";
  }

  getCost() {
    return this.coffee.getCost() + 5;
  }
}
```

Sugar add karne par ₹5 extra lagenge.

### Step 5: Client Code

```javascript
let coffee = new SimpleCoffee();

coffee = new MilkDecorator(coffee);

coffee = new SugarDecorator(coffee);

console.log(coffee.getDescription());

console.log(coffee.getCost());
```

### Output

```text
Simple Coffee + Milk + Sugar
65
```

## 6. Code kaise work kar raha hai?

Step by step samjho:

**Step 1:**

```javascript
let coffee = new SimpleCoffee();
```

Original coffee create hui.

Cost = ₹50

**Step 2:**

```javascript
coffee = new MilkDecorator(coffee);
```

Ab MilkDecorator ne original coffee ko wrap kar liya.

Cost = ₹50 + ₹10 = ₹60

**Step 3:**

```javascript
coffee = new SugarDecorator(coffee);
```

Ab SugarDecorator ne MilkDecorator wale object ko wrap kar liya.

Cost = ₹60 + ₹5 = ₹65

Final description:

```text
Simple Coffee + Milk + Sugar
```

### Object wrapping ka visual flow

```text
SugarDecorator
      |
      v
MilkDecorator
      |
      v
SimpleCoffee
```

Har decorator apne andar previous object ko rakhta hai.

## 7. Decorator Pattern ki important characteristics

1. Existing class ko modify kiye bina behavior add kar sakte hain.
2. Multiple decorators combine kar sakte hain.
3. Runtime par additional functionality add kar sakte hain.
4. Inheritance ke comparison mein composition ka use karta hai.
5. Wrapping order se final behavior change ho sakta hai.

### Decorator order important kyu hai?

Maan lo:

- MilkDecorator coffee ki cost par ₹10 add karta hai.
- DiscountDecorator total cost par 10% discount deta hai.

Agar pehle Milk aur phir Discount lagaya, to discount milk ke extra charge par bhi lagega.

Agar pehle Discount aur phir Milk lagaya, to milk ka charge discount ke baad add hoga.

Isliye wrapping order important ho sakta hai.

## 8. Decorator Pattern ke advantages

- Existing code modify nahi karna padta.
- Runtime par functionality add kar sakte hain.
- Different features ko combine kar sakte hain.
- Code reusable banta hai.
- Single Responsibility Principle follow karne mein help karta hai.

## 9. Decorator Pattern ke disadvantages

- Bahut saare decorators hone par code complex ho sakta hai.
- Debugging difficult ho sakti hai.
- Wrapping order ka dhyan rakhna padta hai.
- Runtime par objects ki structure samajhna difficult ho sakta hai.

## 10. Decorator Pattern kab use karein?

Use karo jab:

- Kisi object mein optional features add karne hon.
- Original class ko modify nahi karna ho.
- Features ko different combinations mein use karna ho.
- Runtime par behavior extend karna ho.

Avoid karo jab simple inheritance ya ek simple function se kaam ho sakta ho.

## 11. MERN Stack mein Decorator Pattern

MERN application mein is pattern ka idea kuch services ke around additional behavior add karne mein useful ho sakta hai.

Example:

```text
Original User Service
        |
        v
Logging Decorator
        |
        v
Caching Decorator
        |
        v
Client
```

Yahan:

- Original service user data fetch karti hai.
- Logging decorator operation log kar sakta hai.
- Caching decorator result cache kar sakta hai.

**Important:** Express middleware chain mein bhi functionality layers hoti hain, lekin har middleware chain automatically GoF Decorator Pattern nahi hoti. Dono concepts ko same nahi samajhna chahiye.

## 12. Decorator vs Inheritance

| Decorator                         | Inheritance                                         |
| --------------------------------- | --------------------------------------------------- |
| Composition use karta hai         | Parent-child relationship use karta hai             |
| Runtime par wrap kar sakte hain   | Behavior generally class structure se milta hai     |
| Features combine kar sakte hain   | Combinations ke liye many subclasses ban sakti hain |
| Original object ko wrap karta hai | Child class parent se inherit karti hai             |

## 13. Decorator vs Adapter vs Proxy

| Pattern   | Main Purpose                                |
| --------- | ------------------------------------------- |
| Decorator | Existing object mein behavior add karna     |
| Adapter   | Incompatible interface ko compatible banana |
| Proxy     | Object ke access ko control karna           |

Example:

- Decorator: Coffee mein Milk add karna.
- Adapter: Different charger ko compatible banana.
- Proxy: Original object tak access control karna.

---

# PART B: FACADE PATTERN

## 14. Facade Pattern kya hai?

Facade Pattern ek Structural Design Pattern hai jo complex subsystem ke liye ek simple, unified interface provide karta hai.

Simple language mein:

Maan lo tum cinema hall mein movie dekhne jaate ho.

Tumhe alag-alag departments se baat nahi karni padti:

- Ticket department
- Seat management
- Payment department
- Food department

Tum counter par jaate ho aur ek simple process follow karte ho.

Facade Pattern bhi complex system ke liye ek simple entry point provide karta hai.

## 15. Facade Pattern ki need kyu hoti hai?

Maan lo ek video conversion system banana hai.

Video convert karne ke liye multiple operations chahiye:

1. Video file read karna.
2. Codec identify karna.
3. Audio process karna.
4. Video encode karna.
5. File save karna.

Agar client ko har subsystem ko individually call karna pade, to client code complex ho jayega.

Facade Pattern in sab operations ko ek simple method ke andar organize kar deta hai.

## 16. Facade Pattern ke main components

Facade Pattern mein mainly 3 components hote hain:

1. **Facade:** Simple interface provide karta hai.
2. **Subsystems:** Actual complex operations perform karte hain.
3. **Client:** Facade ko use karta hai.

### Structure

```text
             Client
                |
                v
              Facade
                |
       -------------------
       |        |        |
    System A System B System C
```

Client ko subsystems ki internal details pata hona zaroori nahi hai.

## 17. Facade Pattern – JavaScript Example

Hum ek video conversion system ka example banayenge.

### Step 1: Video File

```javascript
class VideoFile {
  constructor(name) {
    this.name = name;
  }
}
```

Ye video file ko represent karegi.

### Step 2: Codec Reader

```javascript
class CodecReader {
  read(file) {
    console.log("Reading codec:", file.name);
  }
}
```

Ye video ka codec read karega.

### Step 3: Audio Mixer

```javascript
class AudioMixer {
  process() {
    console.log("Processing audio...");
  }
}
```

Ye audio process karega.

### Step 4: Video Encoder

```javascript
class VideoEncoder {
  encode(file) {
    console.log("Encoding video:", file.name);
  }
}
```

Ye video encode karega.

### Step 5: File Writer

```javascript
class FileWriter {
  save(file) {
    console.log("Saving converted file:", file.name);
  }
}
```

Ye converted file save karega.

### Step 6: Video Conversion Facade

```javascript
class VideoConverterFacade {
  constructor() {
    this.codecReader = new CodecReader();
    this.audioMixer = new AudioMixer();
    this.videoEncoder = new VideoEncoder();
    this.fileWriter = new FileWriter();
  }

  convert(file) {
    this.codecReader.read(file);

    this.audioMixer.process();

    this.videoEncoder.encode(file);

    this.fileWriter.save(file);
  }
}
```

Ye hamara Facade hai.

Iske andar saare subsystems ko organize kiya gaya hai.

### Step 7: Client Code

```javascript
const video = new VideoFile("movie.mp4");

const converter = new VideoConverterFacade();

converter.convert(video);
```

Client ko sirf `convert()` method call karna pada.

### Output

```text
Reading codec: movie.mp4
Processing audio...
Encoding video: movie.mp4
Saving converted file: movie.mp4
```

## 18. Code kaise work kar raha hai?

**Step 1:** Client video file create karta hai.

```javascript
const video = new VideoFile("movie.mp4");
```

**Step 2:** Facade object create hota hai.

```javascript
const converter = new VideoConverterFacade();
```

**Step 3:** Client ek hi method call karta hai.

```javascript
converter.convert(video);
```

**Step 4:** Facade internally:

- CodecReader ko call karta hai.
- AudioMixer ko call karta hai.
- VideoEncoder ko call karta hai.
- FileWriter ko call karta hai.

Client ko in sab classes ke internal operations manage nahi karne padte.

## 19. Facade Pattern ki important characteristics

1. Complex subsystem ko simple interface deta hai.
2. Client aur subsystem ke beech coupling kam kar sakta hai.
3. Multiple operations ko ek entry point se organize karta hai.
4. Subsystems independently exist kar sakte hain.
5. Client ko internal implementation details jaanne ki zarurat nahi hoti.

## 20. Facade Pattern ke advantages

- Complex code use karna easy ho jata hai.
- Client code simple rehta hai.
- Subsystems ki internal details hide hoti hain.
- Code maintain karna easier ho sakta hai.
- Client aur subsystem ke beech dependency kam hoti hai.

## 21. Facade Pattern ke disadvantages

- Facade class bahut badi ho sakti hai.
- Agar har operation Facade mein add karte rahe to ye God Object ban sakta hai.
- Client ko zarurat padne par direct subsystem access bhi dena pad sakta hai.
- Facade subsystem ki complexity ko khatam nahi karta, sirf use karna easy banata hai.

## 22. Facade Pattern kab use karein?

Use karo jab:

- Multiple classes ko ek saath use karna padta ho.
- Complex subsystem ke liye simple interface banana ho.
- Client code mein repeated orchestration ho.
- Internal implementation ko client se hide karna ho.

Avoid karo jab subsystem already simple ho aur Facade unnecessary extra layer create kare.

## 23. MERN Stack mein Facade Pattern

Maan lo tum ek MERN e-commerce application bana rahe ho.

User checkout karta hai.

Checkout ke liye multiple services kaam karti hain:

- Inventory Service
- Payment Service
- Shipping Service
- Notification Service

Without Facade:

```text
Client / Controller
   |
   |-- Inventory Service
   |-- Payment Service
   |-- Shipping Service
   |-- Notification Service
```

With Facade:

```text
Checkout Controller
        |
        v
   Checkout Facade
        |
   -------------------
   |       |         |
Inventory Payment  Shipping
                 |
            Notification
```

Example:

```javascript
class CheckoutFacade {
  constructor(inventory, payment, shipping, notification) {
    this.inventory = inventory;
    this.payment = payment;
    this.shipping = shipping;
    this.notification = notification;
  }

  async checkout(order) {
    await this.inventory.reserve(order);

    await this.payment.charge(order);

    await this.shipping.createShipment(order);

    await this.notification.sendConfirmation(order);

    return {
      success: true,
      message: "Order placed successfully",
    };
  }
}
```

Controller ko ek simple method call karna padega:

```javascript
await checkoutFacade.checkout(order);
```

**Important:** Real payment/checkout system mein error handling, transaction consistency, compensation, idempotency aur security bhi zaroori hain. Facade akela in problems ko solve nahi karta.

---

# PART C: IMPORTANT COMPARISONS

## 24. Decorator vs Facade

| Decorator Pattern                           | Facade Pattern                              |
| ------------------------------------------- | ------------------------------------------- |
| Existing object mein behavior add karta hai | Complex subsystem ko simple banata hai      |
| Object ko wrap karta hai                    | Multiple subsystems ko coordinate karta hai |
| Additional functionality provide karta hai  | Simple unified interface provide karta hai  |
| Example: Coffee + Milk                      | Example: Video Conversion Facade            |

## 25. Decorator vs Facade vs Adapter vs Proxy

| Pattern   | Main Work                   | Example          |
| --------- | --------------------------- | ---------------- |
| Decorator | Behavior add karna          | Coffee mein Milk |
| Facade    | Complexity simplify karna   | Video Converter  |
| Adapter   | Interface compatible banana | Charger Adapter  |
| Proxy     | Access control karna        | Virtual Proxy    |

In chaaron ko confuse mat karna.

Yaad rakhne ka shortcut:

- Decorator = Add behavior
- Facade = Simplify usage
- Adapter = Change interface
- Proxy = Control access

---

# PART D: INTERVIEW QUESTIONS

## 26. Important Interview Questions

### Q1. What is Decorator Pattern?

Decorator Pattern ek Structural Design Pattern hai jo existing object ko wrap karke usmein additional functionality add karta hai without modifying its original class.

### Q2. What is Facade Pattern?

Facade Pattern complex subsystem ke liye ek simple unified interface provide karta hai.

### Q3. Does Decorator Pattern use inheritance?

Decorator classes inheritance use kar sakti hain, lekin main idea composition aur object wrapping hai.

### Q4. What is the difference between Decorator and Adapter?

Decorator same compatible interface maintain karke behavior add karta hai, jabki Adapter incompatible interface ko client ke expected interface mein convert karta hai.

### Q5. What is the difference between Facade and Adapter?

Facade multiple subsystem operations ko simplify karta hai, jabki Adapter ek incompatible interface ko compatible banata hai.

### Q6. Can we use multiple decorators?

Yes. Multiple decorators ko wrap karke combine kar sakte hain.

### Q7. Does Facade hide the entire subsystem?

Facade simple interface provide karta hai. Lekin zaroori nahi ki subsystem ka direct access completely unavailable ho.

### Q8. Is Facade Pattern used in MERN?

Yes. Checkout, order processing aur other workflows mein multiple services ko coordinate karne ke liye Facade ka use kiya ja sakta hai.

---

# PART E: PRACTICE

## 27. Practical Coding Tasks

### Task 1: Coffee Decorator

Ek coffee system banao:

- Simple Coffee = ₹50
- Milk = ₹10
- Sugar = ₹5
- Cream = ₹15

Requirements:

- SimpleCoffee class banao.
- MilkDecorator banao.
- SugarDecorator banao.
- CreamDecorator banao.
- Sab decorators combine karke final cost print karo.

Expected final cost:

```text
50 + 10 + 5 + 15 = 80
```

### Task 2: Logging Decorator

Ek simple service banao jo user data return karti ho.

Logging decorator add karo jo service call hone par log print kare.

Expected output:

```text
Service called
User data returned
```

### Task 3: Checkout Facade

E-commerce checkout system banao.

Separate classes banao:

- InventoryService
- PaymentService
- ShippingService
- NotificationService

In sabko CheckoutFacade ke through coordinate karo.

Client ko sirf:

```javascript
checkoutFacade.checkout(order);
```

call karna chahiye.

---

# PART F: QUICK REVISION

## 28. Quick Revision Notes

### Decorator Pattern

- Structural Design Pattern hai.
- Existing object mein additional behavior add karta hai.
- Original class modify nahi karni padti.
- Composition aur wrapping use karta hai.
- Multiple decorators combine kar sakte hain.
- Wrapping order important ho sakta hai.

Example: Coffee + Milk + Sugar.

### Facade Pattern

- Structural Design Pattern hai.
- Complex subsystem ko simple interface deta hai.
- Multiple classes ko coordinate kar sakta hai.
- Client code ko simple banata hai.
- Internal subsystem logic ko organize karta hai.

Example: Video Conversion Facade.

### Most Important Difference

```text
Decorator = Add functionality

Facade = Simplify complexity
```

---

# 29. Topic Completion Checklist

- [ ] Structural Design Patterns samajh liye.
- [ ] Decorator Pattern samajh liya.
- [ ] Decorator ke components samajh liye.
- [ ] Coffee Decorator code samajh liya.
- [ ] Object wrapping samajh li.
- [ ] Decorator vs Adapter vs Proxy samajh liya.
- [ ] Facade Pattern samajh liya.
- [ ] Facade ke components samajh liye.
- [ ] Video Converter code samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Dono patterns ke differences samajh liye.
- [ ] Practical tasks complete kar liye.

**Topic 26 complete tab samjho jab dono patterns ke examples khud se bana sako.**
