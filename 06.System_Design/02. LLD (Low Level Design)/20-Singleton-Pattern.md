# 20. Singleton Pattern

## 1. Singleton Pattern kya hota hai?

Singleton ek **Creational Design Pattern** hai.

Iska purpose hota hai kisi class ka sirf ek instance create karna aur application mein usi instance ko repeatedly access karna.

Simple language mein:

**Singleton Pattern ensure karta hai ki kisi class ka ek hi shared instance ho aur us instance ko application ke different parts use kar saken.**

### Real-life Example

Maan lo tumhare application mein ek central configuration manager hai.

Ismein application ki common settings hain:

- Application name
- API configuration
- Environment settings
- Common options

Agar har component apna alag configuration manager create kare, to unnecessary multiple instances ban sakte hain.

Singleton Pattern se ek shared instance maintain kar sakte hain.

## 2. Instance kya hota hai?

Instance ka matlab hota hai kisi class se create hua object.

Example:

```javascript
class User {
  constructor(name) {
    this.name = name;
  }
}

const user1 = new User("Rahul");
const user2 = new User("Aman");
```

Yahan:

- `User` ek class hai.
- `user1` ek instance hai.
- `user2` doosra instance hai.

Check:

```javascript
console.log(user1 === user2);
```

Output:

```text
false
```

Kyunki dono alag objects hain.

Singleton ka goal hai ki same Singleton class se baar-baar access karne par wahi shared object mile.

## 3. Singleton Pattern ki zaroorat kyon padti hai?

Maan lo application mein database connection manage karna hai.

Agar har jagah naya database connection manager create karoge to:

- Unnecessary objects create ho sakte hain.
- Resources waste ho sakte hain.
- Configuration manage karna difficult ho sakta hai.
- Connection management complex ho sakta hai.

Singleton Pattern shared instance provide karke is problem ko manage karne mein help kar sakta hai.

**Note:** Database connection ke liye actual production applications mein connection pooling aur proper lifecycle management bhi important hote hain. Singleton akela database scalability problem solve nahi karta.

## 4. Singleton Pattern ke Main Rules

Ek traditional Singleton implementation mein commonly ye rules hote hain:

1. Class apne instance ko internally manage karti hai.
2. Instance pehli baar create hota hai.
3. Baad mein existing instance return hota hai.
4. External code ko directly multiple instances create karne se roka jata hai.

Traditional object-oriented implementation mein constructor ko private rakha ja sakta hai, taaki class ke bahar se object create na ho.

JavaScript mein constructor private nahi hota in the same way as Java/C++. JavaScript private fields aur controlled construction techniques provide karta hai.

## 5. JavaScript mein Simple Singleton Example

JavaScript mein Singleton ko closure aur factory function ke through implement kar sakte hain.

```javascript
const Singleton = (function () {
  let instance;

  function createInstance() {
    return {
      name: "My Application",
      version: "1.0",
    };
  }

  return {
    getInstance: function () {
      if (!instance) {
        instance = createInstance();
      }

      return instance;
    },
  };
})();

const obj1 = Singleton.getInstance();
const obj2 = Singleton.getInstance();

console.log(obj1 === obj2);
```

Output:

```text
true
```

### Code ko step-by-step samjho

**Step 1:**

```javascript
let instance;
```

Yahan instance variable declare kiya hai.

Initially iski value `undefined` hai.

**Step 2:**

```javascript
function createInstance() {
  return {
    name: "My Application",
    version: "1.0",
  };
}
```

Ye function ek object create karta hai.

**Step 3:**

```javascript
if (!instance) {
  instance = createInstance();
}
```

Agar instance exist nahi karta, to naya object create hota hai.

**Step 4:**

```javascript
return instance;
```

Agar instance already exist karta hai, to wahi object return hota hai.

Isliye:

```javascript
obj1 === obj2;
```

Output `true` aata hai.

## 6. JavaScript ES6 Class ke through Singleton

JavaScript mein class aur static property ka use karke bhi Singleton implement kar sakte hain.

```javascript
class Database {
  static instance;

  constructor() {
    if (Database.instance) {
      return Database.instance;
    }

    this.connection = "Database Connected";

    Database.instance = this;
  }
}

const db1 = new Database();
const db2 = new Database();

console.log(db1 === db2);
console.log(db1.connection);
```

Output:

```text
true
Database Connected
```

### Explanation

- `static instance` class-level property hai.
- Pehli baar object create hota hai.
- Object `Database.instance` mein save hota hai.
- Next time constructor call hota hai to existing instance return hota hai.

**Important:** Ye JavaScript implementation hai. JavaScript constructor se existing object return kar sakta hai. Traditional private-constructor Singleton ka exact equivalent nahi hai.

## 7. Singleton Pattern ka Real MERN Example

MERN Stack mein hum ek shared configuration ya service instance maintain kar sakte hain.

Example: Application Configuration Manager.

### config.js

```javascript
class Config {
  constructor() {
    if (Config.instance) {
      return Config.instance;
    }

    this.appName = "MERN Application";
    this.port = 5000;

    Config.instance = this;
  }
}

const config = new Config();

export default config;
```

### server.js

```javascript
import config from "./config.js";

console.log(config.appName);
console.log(config.port);
```

### app.js

```javascript
import config from "./config.js";

console.log(config.appName);
```

Dono files same module se exported configuration object use karengi.

### Important Node.js Concept

Node.js ES Modules ko normally module URL ke basis par cache karta hai.

Isliye same module ko same resolved path se import karne par uska module-level object reuse hota hai.

Is example mein module caching bhi shared object maintain karne mein help karti hai.

Real MERN project mein configuration ke liye har baar custom Singleton class banana necessary nahi hota. Simple exported object ya module-level instance bhi sufficient ho sakta hai.

## 8. Database Connection Manager Example

Ek simplified database connection manager:

```javascript
class DatabaseConnection {
  constructor() {
    if (DatabaseConnection.instance) {
      return DatabaseConnection.instance;
    }

    this.connected = false;

    DatabaseConnection.instance = this;
  }

  connect() {
    if (!this.connected) {
      this.connected = true;
      console.log("Database Connected");
    }
  }
}

const db1 = new DatabaseConnection();
const db2 = new DatabaseConnection();

db1.connect();
db2.connect();

console.log(db1 === db2);
```

Output:

```text
Database Connected
true
```

Yahan second call par existing instance reuse hota hai.

**Production Note:** Real MongoDB connection ke liye Mongoose connection lifecycle, connection pooling, error handling aur application shutdown properly manage karna chahiye.

## 9. Singleton Pattern ke Advantages

### 1. Single Shared Instance

Ek shared object ko multiple components use kar sakte hain.

### 2. Resource Management

Unnecessary duplicate objects create hone se bach sakte hain.

### 3. Centralized Management

Common configuration ya service ko ek central place se manage kar sakte hain.

### 4. Easy Access

Application ke different parts same instance access kar sakte hain.

### 5. Consistent State

Same shared instance use karne se uski state shared rehti hai.

## 10. Singleton Pattern ke Disadvantages

### 1. Global State

Singleton global state jaisa behave kar sakta hai.

Isse application ka behavior samajhna difficult ho sakta hai.

### 2. Tight Coupling

Multiple components directly Singleton par depend karne lagte hain.

### 3. Testing Difficult

Tests ke beech shared state ki wajah se unexpected results aa sakte hain.

### 4. Concurrency Problems

Multithreaded environments mein thread-safe initialization ka dhyan rakhna padta hai.

### 5. Overuse

Har service ko Singleton banana good design nahi hota.

## 11. Singleton Pattern vs Normal Object

| Singleton                          | Normal Object Creation                    |
| ---------------------------------- | ----------------------------------------- |
| Shared instance maintain karta hai | Multiple instances create ho sakte hain   |
| Same object reuse hota hai         | Har creation par naya object ho sakta hai |
| Shared state possible              | Objects ki state independent ho sakti hai |
| Example: Shared config             | Example: Individual user objects          |

Example:

```javascript
const obj1 = Singleton.getInstance();
const obj2 = Singleton.getInstance();

console.log(obj1 === obj2); // true
```

Normal objects:

```javascript
const obj1 = {};
const obj2 = {};

console.log(obj1 === obj2); // false
```

## 12. Singleton Pattern vs Factory Pattern

| Singleton                                 | Factory                                            |
| ----------------------------------------- | -------------------------------------------------- |
| Single shared instance maintain karta hai | Objects create karne ka process organize karta hai |
| Focus instance uniqueness par             | Focus object creation par                          |
| Same instance reuse hota hai              | Different objects create ho sakte hain             |
| Example: Config Manager                   | Example: Payment Object Factory                    |

## 13. Singleton Pattern kab use karna chahiye?

Singleton useful ho sakta hai:

1. Shared configuration manager.
2. Centralized logger.
3. Shared service manager.
4. Application-level cache manager.
5. Carefully managed database connection manager.

### Kab avoid karna chahiye?

1. Jab multiple independent instances required hon.
2. Jab testing mein isolated objects chahiye hon.
3. Jab dependency injection better solution ho.
4. Jab Singleton unnecessary global state create kar raha ho.
5. Jab simple module-level object sufficient ho.

## 14. Common Mistakes

1. Singleton ko ek normal object samajhna.
2. Har class ko Singleton bana dena.
3. Ye assume karna ki Singleton automatically thread-safe hota hai.
4. Database connection pooling ko Singleton samajhna.
5. Testing ke time shared state ignore karna.
6. JavaScript module caching aur Singleton pattern ko exactly same concept samajhna.
7. Ye assume karna ki multiple application servers mein bhi ek hi global instance automatically share hoga.

**Important:** Agar tumhare application ki 3 separate server processes chal rahi hain, to har process ka apna Singleton instance ho sakta hai. Singleton automatically distributed single instance provide nahi karta.

## 15. Interview Questions & Answers

### Q1. What is Singleton Pattern?

Singleton ek Creational Design Pattern hai jo ek class ka single shared instance maintain karta hai.

### Q2. Why do we use Singleton Pattern?

Common shared objects ko centrally manage karne aur unnecessary duplicate instances avoid karne ke liye.

### Q3. Is Singleton a Creational Pattern?

Yes, Singleton Creational Design Pattern hai.

### Q4. Can Singleton have multiple objects?

Traditional Singleton design ka purpose ek hi shared instance maintain karna hai.

### Q5. What is Lazy Initialization?

Jab object ko application start hote hi create karne ke bajay first requirement par create kiya jata hai, use Lazy Initialization kehte hain.

### Q6. What is Global State?

Aisi shared state jise application ke multiple parts access ya modify kar sakte hain.

### Q7. Is Singleton thread-safe by default?

Nahi. Implementation aur programming language ke according thread safety ensure karni pad sakti hai.

### Q8. Can we use Singleton in JavaScript?

Yes. JavaScript mein closure, module-level exports aur class-based techniques se Singleton-style implementation bana sakte hain.

### Q9. Does Singleton work across multiple servers?

Automatically nahi. Har process ya server apna instance maintain kar sakta hai.

### Q10. What is the biggest disadvantage of Singleton?

Global shared state aur tight coupling create hone ka risk.

## 16. Practical Tasks

### Task 1: Basic Singleton

Ek Singleton class banao jisme:

- Ek instance variable ho.
- Pehli baar object create ho.
- Second time same object return ho.

Check:

```javascript
console.log(obj1 === obj2);
```

Expected:

```text
true
```

### Task 2: Logger Singleton

Ek Logger Singleton banao.

Requirements:

- `log(message)` method ho.
- Message console mein print ho.
- Multiple calls same Logger instance use karein.

### Task 3: Configuration Singleton

Ek Config Singleton banao jisme:

```javascript
appName = "My MERN App";
port = 5000;
environment = "development";
```

Do alag variables mein instance lo aur check karo ki dono same hain.

## 17. Quick Revision

| Term                | Meaning                                |
| ------------------- | -------------------------------------- |
| Singleton           | Single shared instance                 |
| Category            | Creational                             |
| Instance            | Class se create object                 |
| Lazy Initialization | Need hone par object create karna      |
| Shared State        | Multiple parts ka same state use karna |
| Global State        | Application-wide accessible state      |
| Module Caching      | Same module ko reuse karna             |

### Remember

- Singleton ek Creational Pattern hai.
- Iska goal single shared instance maintain karna hai.
- First time object create hota hai.
- Next time existing object return hota hai.
- JavaScript mein closures aur modules se Singleton-style behavior implement kar sakte hain.
- Overuse se tight coupling aur global state problems aa sakti hain.
- Multiple server processes ke across Singleton automatically shared nahi hota.

## 18. Topic Completion Checklist

- [ ] Singleton Pattern ka meaning samajh liya.
- [ ] Instance ka meaning samajh liya.
- [ ] Singleton ki need samajh li.
- [ ] Singleton ke rules samajh liye.
- [ ] Closure-based implementation samajh li.
- [ ] Class-based implementation samajh li.
- [ ] MERN example samajh liya.
- [ ] Advantages aur disadvantages samajh liye.
- [ ] Factory vs Singleton difference samajh liya.
- [ ] Interview questions revise kar liye.
- [ ] Practical tasks complete kar liye.

**Topic 20 Complete: Singleton Pattern**
