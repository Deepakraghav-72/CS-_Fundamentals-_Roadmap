# 24. Observer Pattern

## 1. Observer Pattern kya hota hai?

Observer Pattern ek **Behavioral Design Pattern** hai.

Iska main purpose ek object (Subject) mein hone wale changes ki information usse subscribe karne wale multiple objects (Observers) tak pahunchana hai.

Simple language mein:

**Jab ek object mein koi change hota hai, to us object ke saath registered doosre objects ko automatically update ya notify kiya jata hai.**

### Real-Life Example: YouTube Channel

Maan lo tumne kisi YouTube channel ko subscribe kiya hai.

Jab channel par new video upload hoti hai:

1. YouTube channel new video upload karta hai.
2. Channel apne subscribers ko notify karta hai.
3. Subscribers ko notification mil jaati hai.

Yahan:

- YouTube Channel = Subject
- Subscribers = Observers
- New Video Upload = Event
- Notification = Update

Tumhe har subscriber ko manually notification bhejne ki zaroorat nahi hoti. Subject registered observers ko notify karta hai.

## 2. Observer Pattern ki zaroorat kyon padti hai?

Maan lo tum ek E-commerce application bana rahe ho.

Jab kisi product ka price change hota hai, to:

- Customer ko notification bhejni hai.
- Admin dashboard update karna hai.
- Price history save karni hai.
- Analytics system ko update karna hai.

Without Observer Pattern:

```javascript
function updateProductPrice(price) {
  console.log("Price updated:", price);

  // Customer notification
  // Admin dashboard update
  // Price history save
  // Analytics update
}
```

### Is approach ki problems

1. Ek function multiple responsibilities handle karne lagta hai.
2. New notification feature add karne par existing function modify karna padta hai.
3. Code tightly coupled ho sakta hai.
4. Testing aur maintenance difficult ho sakti hai.

Observer Pattern mein hum alag-alag observers register kar sakte hain.

Subject mein change hone par sabhi registered observers ko notify kiya ja sakta hai.

## 3. Observer Pattern ka Basic Working

Observer Pattern mein generally ye components hote hain:

1. Subject
2. Observer
3. Concrete Subject
4. Concrete Observer

Diagram:

```text
             Client
                |
                v
             Subject
                |
        Register Observers
                |
       ---------------------
       |         |         |
       v         v         v
   Observer A Observer B Observer C
       |         |         |
       ---------------------
                |
                v
             Notify()
                |
       ---------------------
       |         |         |
       v         v         v
     Update    Update    Update
```

### Working Steps

1. Observer Subject ke saath register hota hai.
2. Subject observers ki list maintain karta hai.
3. Subject mein koi event ya change hota hai.
4. Subject `notify()` call karta hai.
5. Sabhi registered observers ka `update()` method call hota hai.
6. Observers ko latest information mil jaati hai.

## 4. Observer Pattern Example in JavaScript

Maan lo hum ek YouTube Channel ka example bana rahe hain.

### Step 1: Subject Class Create Karo

```javascript
class YouTubeChannel {
  constructor() {
    this.subscribers = [];
  }

  subscribe(observer) {
    this.subscribers.push(observer);
  }

  unsubscribe(observer) {
    this.subscribers = this.subscribers.filter((sub) => sub !== observer);
  }

  notify(video) {
    this.subscribers.forEach((observer) => {
      observer.update(video);
    });
  }

  uploadVideo(video) {
    console.log("New Video Uploaded:", video);

    this.notify(video);
  }
}
```

### Step 2: Observer Class Create Karo

```javascript
class Subscriber {
  constructor(name) {
    this.name = name;
  }

  update(video) {
    console.log(`${this.name} received notification: ${video}`);
  }
}
```

### Step 3: Subject aur Observers Create Karo

```javascript
const channel = new YouTubeChannel();

const user1 = new Subscriber("Rahul");
const user2 = new Subscriber("Aman");
const user3 = new Subscriber("Rohit");
```

### Step 4: Subscribe Karo

```javascript
channel.subscribe(user1);
channel.subscribe(user2);
channel.subscribe(user3);
```

Ab teeno subscribers channel ki subscriber list mein registered hain.

### Step 5: New Video Upload Karo

```javascript
channel.uploadVideo("Learn JavaScript");
```

Output:

```text
New Video Uploaded: Learn JavaScript

Rahul received notification: Learn JavaScript
Aman received notification: Learn JavaScript
Rohit received notification: Learn JavaScript
```

### Step 6: Unsubscribe Karo

Maan lo Rahul channel unsubscribe kar deta hai.

```javascript
channel.unsubscribe(user1);
```

Ab dobara video upload karo:

```javascript
channel.uploadVideo("Learn System Design");
```

Output:

```text
New Video Uploaded: Learn System Design

Aman received notification: Learn System Design
Rohit received notification: Learn System Design
```

Rahul ko notification nahi mili kyunki usne unsubscribe kar diya tha.

## 5. Code ko Step-by-Step Samjho

### 1. subscribers Array

```javascript
this.subscribers = [];
```

Ye array registered observers ko store karta hai.

### 2. subscribe()

```javascript
subscribe(observer) {
  this.subscribers.push(observer);
}
```

New observer ko subscriber list mein add karta hai.

### 3. unsubscribe()

```javascript
unsubscribe(observer) {
  this.subscribers = this.subscribers.filter(
    (sub) => sub !== observer
  );
}
```

Selected observer ko list se remove karta hai.

### 4. notify()

```javascript
notify(video) {
  this.subscribers.forEach((observer) => {
    observer.update(video);
  });
}
```

Sabhi registered observers ka `update()` method call karta hai.

### 5. update()

```javascript
update(video) {
  console.log(video);
}
```

Observer ko Subject se information milti hai.

**Important:** JavaScript mein built-in `interface` keyword nahi hai. Observer objects ko common `update()` method follow karna hota hai.

## 6. Observer Pattern ke Main Components

### 1. Subject

Subject observers ko register aur unregister karta hai.

Ye observers ki list maintain karta hai aur changes hone par notify karta hai.

### 2. Observer

Observer ek common contract define karta hai.

Example: `update()` method.

### 3. Concrete Subject

Ye actual object hota hai jisme changes hote hain.

Example: YouTubeChannel.

### 4. Concrete Observer

Ye actual observer hota hai jo notifications receive karta hai.

Example: Subscriber.

## 7. Observer Pattern ka Real-World Example: Stock Price

Maan lo ek stock market application hai.

Jab kisi stock ka price change hota hai, to us stock ko follow karne wale users ko update milna chahiye.

```javascript
class Stock {
  constructor(name, price) {
    this.name = name;
    this.price = price;
    this.observers = [];
  }

  subscribe(observer) {
    this.observers.push(observer);
  }

  notify() {
    this.observers.forEach((observer) => {
      observer.update(this.name, this.price);
    });
  }

  setPrice(newPrice) {
    this.price = newPrice;

    console.log("Stock price changed:", newPrice);

    this.notify();
  }
}

class StockInvestor {
  constructor(name) {
    this.name = name;
  }

  update(stockName, price) {
    console.log(`${this.name}: ${stockName} price is ${price}`);
  }
}

const stock = new Stock("TCS", 3500);

const investor1 = new StockInvestor("Rahul");
const investor2 = new StockInvestor("Aman");

stock.subscribe(investor1);
stock.subscribe(investor2);

stock.setPrice(3600);
```

Output:

```text
Stock price changed: 3600

Rahul: TCS price is 3600
Aman: TCS price is 3600
```

Yahan stock price change hone par registered investors automatically update receive karte hain.

## 8. Observer Pattern vs Pub-Sub Pattern

Dono patterns ka concept similar lag sakta hai, lekin dono exactly same nahi hain.

### Observer Pattern

- Subject directly observers ko jaanta hai.
- Observers directly Subject ke saath register hote hain.
- Subject observers ko notify karta hai.

### Pub-Sub Pattern

- Publisher event publish karta hai.
- Subscriber events subscribe karta hai.
- Beech mein Event Bus ya Message Broker ho sakta hai.
- Publisher aur Subscriber ek-doosre ko directly know karna zaroori nahi hai.

Diagram:

```text
OBSERVER PATTERN

Subject
   |
   | Direct Notification
   |
   +------> Observer A
   |
   +------> Observer B


PUB-SUB PATTERN

Publisher
    |
    v
 Event Bus
    |
    +------> Subscriber A
    |
    +------> Subscriber B
```

### Difference Table

| Observer                                       | Pub-Sub                                             |
| ---------------------------------------------- | --------------------------------------------------- |
| Subject directly observers ko notify karta hai | Publisher event bus ke through publish karta hai    |
| Direct relationship hota hai                   | Usually indirect relationship hota hai              |
| Subject observers ki list maintain karta hai   | Broker/Event Bus subscriptions manage kar sakta hai |
| Mostly in-process communication mein useful    | Distributed systems mein bhi useful                 |

## 9. Observer Pattern vs Strategy Pattern

| Observer Pattern                       | Strategy Pattern                                      |
| -------------------------------------- | ----------------------------------------------------- |
| Multiple observers ko notify karta hai | Multiple algorithms mein se strategy select karta hai |
| Behavioral Pattern                     | Behavioral Pattern                                    |
| One-to-many relationship               | Context aur selected strategy ka relationship         |
| Example: YouTube notifications         | Example: Discount calculation                         |

## 10. Observer Pattern ke Advantages

### 1. Loose Coupling

Subject aur observers ke beech direct dependency kam ho sakti hai.

### 2. Easy Extension

New observer add karne ke liye Subject ka main code modify karna zaroori nahi hota.

### 3. Automatic Notification

Subject mein changes hone par registered observers automatically notify hote hain.

### 4. Reusability

Same observer ko different subjects ke saath use kiya ja sakta hai, agar required contract compatible ho.

### 5. Better Separation

Subject aur observers ki responsibilities separate rehti hain.

## 11. Observer Pattern ke Disadvantages

### 1. Memory Leaks

Agar observers ko unsubscribe nahi kiya gaya, to unnecessary references memory mein reh sakte hain.

### 2. Notification Order

Multiple observers ka execution order kabhi-kabhi important ho sakta hai.

### 3. Debugging Difficult

Ek event se multiple observers execute ho sakte hain. Isliye flow track karna difficult ho sakta hai.

### 4. Performance Issues

Agar bahut saare observers registered hain, to notification process slow ho sakta hai.

### 5. Unexpected Updates

Agar observer properly handle nahi kiya gaya, to unwanted ya repeated updates aa sakte hain.

## 12. MERN Stack mein Observer Pattern

MERN Stack applications mein Observer Pattern aur uske related event-driven concepts ka use kaafi useful ho sakta hai.

### Example 1: React useState

React mein state update hone par component re-render ho sakta hai.

```javascript
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>{count}</h2>

      <button onClick={() => setCount(count + 1)}>Increase</button>
    </div>
  );
}

export default Counter;
```

Yahan React state change ke baad UI ko update karta hai.

**Note:** React ka `useState` Observer Pattern ka direct implementation nahi hai. Lekin state changes aur UI updates ka concept Observer Pattern se related hai.

### Example 2: Node.js EventEmitter

Node.js ka `EventEmitter` event-based communication provide karta hai.

```javascript
const EventEmitter = require("node:events");

const eventEmitter = new EventEmitter();

eventEmitter.on("orderPlaced", (order) => {
  console.log("Email notification:", order.id);
});

eventEmitter.on("orderPlaced", (order) => {
  console.log("Admin notified:", order.id);
});

eventEmitter.emit("orderPlaced", {
  id: 101,
});
```

Output:

```text
Email notification: 101
Admin notified: 101
```

Yahan:

- `on()` = Event listener register karna.
- `emit()` = Event trigger karna.
- Registered listeners = Observers ki tarah kaam karte hain.

Node.js EventEmitter Observer-style event notification ka practical example hai.

### Example 3: E-commerce Order Updates

Maan lo customer order place karta hai.

Order place hone par:

- Email notification bhejni hai.
- Admin ko update dena hai.
- Analytics update karni hai.

Order event ke observers ye tasks handle kar sakte hain.

Large-scale applications mein in tasks ko message queue ya event broker ke through asynchronously process karna better ho sakta hai.

## 13. Observer Pattern kab use karna chahiye?

Observer Pattern use karo jab:

1. Ek object ke changes multiple objects ko notify karne hon.
2. One-to-many relationship ho.
3. Event-based communication chahiye.
4. Notification system develop karna ho.
5. Subject aur observers ko loosely coupled rakhna ho.

### Kab avoid karna chahiye?

1. Sirf ek object ko update karna ho aur direct method call sufficient ho.
2. Observers ki unnecessary complexity create ho rahi ho.
3. Notification order aur execution control bahut important ho aur design usse handle na karta ho.

## 14. Common Mistakes

1. Subject aur Observer ka role confuse karna.
2. Unsubscribe karna bhool jana.
3. Observer ke andar common `update()` contract follow na karna.
4. Unnecessary observers register karna.
5. Observer aur Pub-Sub ko exactly same samajhna.
6. Har event ke liye Observer Pattern use karna.
7. Notification errors ko handle na karna.

## 15. Interview Questions & Answers

### Q1. What is Observer Pattern?

Observer Pattern ek Behavioral Design Pattern hai jisme ek Subject ke changes hone par registered Observers automatically notify hote hain.

### Q2. What is Subject?

Subject wo object hota hai jo observers ko register, unregister aur notify karta hai.

### Q3. What is Observer?

Observer wo object hota hai jo Subject ke changes ki notification receive karta hai.

### Q4. What is the purpose of subscribe()?

Kisi observer ko Subject ke saath register karna.

### Q5. What is the purpose of unsubscribe()?

Observer ko Subject ki registered list se remove karna.

### Q6. What is notify()?

notify() method registered observers ko update bhejta hai.

### Q7. What is the difference between Observer and Pub-Sub?

Observer mein Subject directly observers ko notify karta hai, jabki Pub-Sub mein communication usually Event Bus ya Broker ke through hoti hai.

### Q8. Is Observer a Behavioral Pattern?

Yes.

### Q9. Give a real-world example.

YouTube channel ke subscribers ko new video upload hone par notification milna.

### Q10. What is Node.js EventEmitter?

Node.js EventEmitter ek event-based mechanism hai jisme listeners register hote hain aur event emit hone par execute hote hain.

## 16. Practical Tasks

### Task 1: YouTube Subscription System

Classes banao:

- YouTubeChannel
- Subscriber

Methods:

- subscribe()
- unsubscribe()
- notify()
- uploadVideo()

Ek channel mein minimum 3 subscribers register karo.

New video upload hone par sabko notification milni chahiye.

### Task 2: Weather Monitoring System

Ek WeatherStation class banao.

Weather change hone par registered observers ko temperature update milna chahiye.

Methods:

- subscribe()
- unsubscribe()
- setTemperature()
- notify()

### Task 3: Order Notification System

Ek Order class banao.

Order place hone par:

- EmailObserver
- AdminObserver
- AnalyticsObserver

ko notify karo.

Har observer ka apna `update()` method hona chahiye.

## 17. Quick Revision

| Term              | Meaning                                        |
| ----------------- | ---------------------------------------------- |
| Observer Pattern  | Changes par registered objects ko notify karna |
| Category          | Behavioral                                     |
| Subject           | Observers manage karta hai                     |
| Observer          | Notification receive karta hai                 |
| Concrete Subject  | Actual changing object                         |
| Concrete Observer | Actual notification receiver                   |
| subscribe()       | Observer register karna                        |
| unsubscribe()     | Observer remove karna                          |
| notify()          | Observers ko update bhejna                     |
| update()          | Observer ka notification handler               |

### Important Points

- Observer Pattern Behavioral Design Pattern hai.
- Ismein one-to-many relationship hota hai.
- Subject observers ko notify karta hai.
- Observer notification receive karta hai.
- subscribe() se observer register hota hai.
- unsubscribe() se observer remove hota hai.
- Node.js EventEmitter Observer-style event handling provide karta hai.
- Pub-Sub related hai, lekin exactly same nahi hai.

## 18. Topic Completion Checklist

- [ ] Observer Pattern ka meaning samajh liya.
- [ ] Observer Pattern ki need samajh li.
- [ ] Working flow samajh liya.
- [ ] Subject aur Observer samajh liya.
- [ ] Concrete Subject aur Concrete Observer samajh liya.
- [ ] subscribe() aur unsubscribe() samajh liya.
- [ ] notify() aur update() samajh liya.
- [ ] JavaScript example samajh liya.
- [ ] Observer vs Pub-Sub samajh liya.
- [ ] Observer vs Strategy samajh liya.
- [ ] Node.js EventEmitter samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Interview questions revise kar liye.
- [ ] Practical tasks complete kar liye.

**Topic 24 Complete: Observer Pattern**
