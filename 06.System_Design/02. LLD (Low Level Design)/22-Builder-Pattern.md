# 22. Builder Pattern

## 1. Builder Pattern kya hota hai?

Builder Pattern ek **Creational Design Pattern** hai.

Iska main purpose complex objects ko step-by-step create karna hai.

Simple language mein:

**Builder Pattern ki help se hum kisi complex object ko ek-ek step mein configure aur construct kar sakte hain.**

Maan lo tumhe ek computer assemble karna hai.

Computer ke different parts hote hain:

- Processor
- RAM
- Storage
- Graphics Card
- Motherboard

Har computer mein ye saare parts same hona zaroori nahi hai.

Kisi computer mein 8GB RAM ho sakti hai aur kisi mein 32GB RAM.

Builder Pattern isi tarah objects ko required configuration ke according step-by-step build karne mein help karta hai.

## 2. Builder Pattern ki zaroorat kyon padti hai?

Maan lo tum ek User object create karna chahte ho.

User ki properties hain:

- Name
- Email
- Age
- Phone
- Address
- City
- Country

Without Builder Pattern:

```javascript
const user = new User(
  "Rahul",
  "rahul@gmail.com",
  22,
  "9876543210",
  "Delhi",
  "Delhi",
  "India",
);
```

### Is approach ki problems

1. Constructor mein bahut saare parameters ho sakte hain.
2. Parameters ka order yaad rakhna difficult ho sakta hai.
3. Optional values manage karna difficult ho sakta hai.
4. Code readable nahi rehta.
5. Future mein properties add hone par constructor complicated ho sakta hai.

Is problem ko Builder Pattern solve karne mein help karta hai.

## 3. Builder Pattern ka Basic Working

Builder Pattern mein generally:

1. Builder object create hota hai.
2. Required properties step-by-step set hoti hain.
3. Har step builder object return kar sakta hai.
4. Last mein `build()` call hota hai.
5. Final object return hota hai.

Diagram:

```text
       Client
          |
          v
    Create Builder
          |
          v
    Set Name
          |
          v
    Set Email
          |
          v
    Set Age
          |
          v
       build()
          |
          v
     Final Object
```

## 4. Builder Pattern Example in JavaScript

Maan lo humein ek User object create karna hai.

### Step 1: User Class

```javascript
class User {
  constructor(name, email, age, city) {
    this.name = name;
    this.email = email;
    this.age = age;
    this.city = city;
  }
}
```

Ye hamara final object hai.

### Step 2: User Builder Class

```javascript
class UserBuilder {
  constructor(name, email) {
    this.user = {
      name,
      email,
    };
  }

  setAge(age) {
    this.user.age = age;
    return this;
  }

  setCity(city) {
    this.user.city = city;
    return this;
  }

  build() {
    return new User(
      this.user.name,
      this.user.email,
      this.user.age,
      this.user.city,
    );
  }
}
```

### Step 3: Builder ka Use

```javascript
const user = new UserBuilder("Rahul", "rahul@gmail.com")
  .setAge(22)
  .setCity("Delhi")
  .build();

console.log(user);
```

Output:

```text
User {
  name: 'Rahul',
  email: 'rahul@gmail.com',
  age: 22,
  city: 'Delhi'
}
```

## 5. Code ko Step-by-Step Samjho

### Step 1: Builder Create

```javascript
const builder = new UserBuilder("Rahul", "rahul@gmail.com");
```

Builder object create hota hai.

### Step 2: Age Set

```javascript
builder.setAge(22);
```

Age property set ho jaati hai.

### Step 3: City Set

```javascript
builder.setCity("Delhi");
```

City property set ho jaati hai.

### Step 4: Final Object Build

```javascript
const user = builder.build();
```

`build()` final User object return karta hai.

### Important: return this ka meaning

```javascript
setAge(age) {
  this.user.age = age;
  return this;
}
```

`return this` ka meaning hai current Builder object ko return karna.

Iski wajah se hum method chaining kar sakte hain.

Example:

```javascript
builder.setAge(22).setCity("Delhi").build();
```

Is technique ko **Method Chaining** kehte hain.

## 6. Builder Pattern mein Important Components

### 1. Product

Final object jise create karna hai.

Example: `User`.

### 2. Builder

Object ko step-by-step construct karne wali class.

Example: `UserBuilder`.

### 3. Concrete Builder

Builder ki actual implementation jo object ke different parts set karti hai.

Example: `UserBuilder` khud ek concrete builder hai.

### 4. Director (Optional)

Director decide karta hai ki builder ke methods kis sequence mein call honge.

Har Builder Pattern implementation mein Director zaroori nahi hota.

## 7. Director ka Example

```javascript
class Computer {
  constructor(cpu, ram, storage) {
    this.cpu = cpu;
    this.ram = ram;
    this.storage = storage;
  }
}

class ComputerBuilder {
  constructor() {
    this.cpu = null;
    this.ram = null;
    this.storage = null;
  }

  setCPU(cpu) {
    this.cpu = cpu;
    return this;
  }

  setRAM(ram) {
    this.ram = ram;
    return this;
  }

  setStorage(storage) {
    this.storage = storage;
    return this;
  }

  build() {
    if (!this.cpu || !this.ram || !this.storage) {
      throw new Error("All computer parts are required");
    }

    return new Computer(this.cpu, this.ram, this.storage);
  }
}

class ComputerDirector {
  static buildGamingPC(builder) {
    return builder
      .setCPU("Intel Core i7")
      .setRAM("32GB")
      .setStorage("1TB SSD")
      .build();
  }
}

const builder = new ComputerBuilder();

const gamingPC = ComputerDirector.buildGamingPC(builder);

console.log(gamingPC);
```

Output:

```text
Computer {
  cpu: 'Intel Core i7',
  ram: '32GB',
  storage: '1TB SSD'
}
```

Director yahan predefined construction sequence provide kar raha hai.

## 8. Builder Pattern vs Constructor

| Constructor                                             | Builder Pattern                          |
| ------------------------------------------------------- | ---------------------------------------- |
| Object constructor se create hota hai                   | Object step-by-step create hota hai      |
| Many parameters confusing ho sakte hain                 | Properties clearly set kar sakte hain    |
| Optional parameters manage karna difficult ho sakta hai | Optional configuration easy ho sakti hai |
| Simple objects ke liye useful                           | Complex objects ke liye useful           |

## 9. Builder Pattern vs Factory Pattern

Dono Creational Design Patterns hain, lekin inka purpose alag hai.

| Factory Pattern                             | Builder Pattern                                   |
| ------------------------------------------- | ------------------------------------------------- |
| Decide karta hai kaunsa object create hoga  | Object kaise step-by-step construct hoga          |
| Object creation ko centralize karta hai     | Object construction process ko organize karta hai |
| Different object types return kar sakta hai | Usually ek complex object configure karta hai     |
| Example: PaymentFactory                     | Example: ComputerBuilder                          |

### Easy Example

Factory:

```javascript
const payment = PaymentFactory.create("UPI");
```

Builder:

```javascript
const computer = new ComputerBuilder()
  .setCPU("Intel")
  .setRAM("16GB")
  .setStorage("1TB")
  .build();
```

**Yaad rakho:**

Factory = Kaunsa object banana hai?

Builder = Object ko kaise step-by-step banana hai?

## 10. Builder Pattern ke Advantages

### 1. Readable Code

Method names se samajh aata hai ki kaunsi property set ho rahi hai.

### 2. Step-by-Step Construction

Complex objects ko multiple steps mein create kar sakte hain.

### 3. Optional Parameters

Optional properties ko easily configure kar sakte hain.

### 4. Better Maintainability

Object construction logic alag manage hota hai.

### 5. Method Chaining

`return this` ki help se clean chaining possible hoti hai.

### 6. Validation

Final object create karne se pehle `build()` mein validation kar sakte hain.

## 11. Builder Pattern ke Disadvantages

### 1. Extra Code

Builder ke liye separate class likhni pad sakti hai.

### 2. More Complexity

Simple object ke liye Builder unnecessary complexity create kar sakta hai.

### 3. Maintenance

Builder aur Product dono ko update karna pad sakta hai.

### 4. Overengineering

Har object ke liye Builder banana good practice nahi hai.

## 12. MERN Stack mein Builder Pattern

MERN Stack mein Builder Pattern ka use complex configuration objects banane mein ho sakta hai.

### Example 1: API Request Builder

```javascript
class ApiRequestBuilder {
  constructor(url) {
    this.request = {
      url,
      method: "GET",
      headers: {},
      body: null,
    };
  }

  setMethod(method) {
    this.request.method = method;
    return this;
  }

  setHeaders(headers) {
    this.request.headers = headers;
    return this;
  }

  setBody(body) {
    this.request.body = body;
    return this;
  }

  build() {
    return { ...this.request };
  }
}

const request = new ApiRequestBuilder("https://example.com/api/users")
  .setMethod("POST")
  .setHeaders({
    "Content-Type": "application/json",
  })
  .setBody({
    name: "Rahul",
  })
  .build();

console.log(request);
```

Output:

```javascript
{
  url: "https://example.com/api/users",
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: {
    name: "Rahul"
  }
}
```

Ye ek educational example hai. Real application mein request execute karne ke liye `fetch()` ya Axios use karna hoga.

### Example 2: Query Configuration

Maan lo Express application mein query configuration step-by-step build karni hai.

```javascript
class QueryBuilder {
  constructor() {
    this.query = {};
  }

  setName(name) {
    this.query.name = name;
    return this;
  }

  setAge(age) {
    this.query.age = age;
    return this;
  }

  build() {
    return { ...this.query };
  }
}

const filter = new QueryBuilder().setName("Rahul").setAge(22).build();

console.log(filter);
```

Output:

```javascript
{
  name: "Rahul",
  age: 22
}
```

MERN application mein is tarah ka builder query filters ya configuration objects ko organize karne mein help kar sakta hai. User input ko validate aur sanitize karna phir bhi zaroori hai.

## 13. Builder Pattern kab use karna chahiye?

Builder Pattern use karo jab:

1. Object mein bahut saari properties hon.
2. Bahut saari properties optional hon.
3. Object ko multiple steps mein construct karna ho.
4. Constructor bahut complicated ho raha ho.
5. Build karne se pehle validation karni ho.
6. Readable object creation code chahiye.

### Kab avoid karna chahiye?

1. Object simple ho.
2. Sirf 1–2 properties hon.
3. Direct constructor se kaam easily ho raha ho.
4. Builder unnecessary code badha raha ho.

## 14. Common Mistakes

1. Factory aur Builder ko same samajhna.
2. `return this` bhool jana, jab method chaining chahiye.
3. `build()` mein validation na karna.
4. Incomplete object create karne dena.
5. Har simple object ke liye Builder banana.
6. Builder aur final Product ko confuse karna.
7. Director ko mandatory samajhna.

## 15. Interview Questions & Answers

### Q1. What is Builder Pattern?

Builder Pattern ek Creational Design Pattern hai jo complex objects ko step-by-step construct karne mein help karta hai.

### Q2. Why do we use Builder Pattern?

Complex constructors aur multiple optional parameters ko manage karne ke liye.

### Q3. What is the purpose of build()?

`build()` method final object create karke return karta hai.

### Q4. What is method chaining?

Ek object ke multiple methods ko continuously call karna method chaining kehlata hai.

### Q5. Why do we use return this?

Current object return karne ke liye, taaki method chaining possible ho.

### Q6. Is Director mandatory?

No. Director optional hota hai.

### Q7. What is the difference between Factory and Builder?

Factory decide karta hai kaunsa object create hoga, Builder decide karta hai object ko step-by-step kaise construct karna hai.

### Q8. Is Builder a Creational Pattern?

Yes.

### Q9. Can Builder validate an object?

Yes. `build()` method mein validation kar sakte hain.

### Q10. Give a real-world example of Builder Pattern.

Computer configuration builder, API request builder, ya complex User configuration builder.

## 16. Practical Tasks

### Task 1: Laptop Builder

Ek Laptop class aur LaptopBuilder class banao.

Properties:

- Brand
- Processor
- RAM
- Storage
- Graphics Card

Builder ke methods:

- setBrand()
- setProcessor()
- setRAM()
- setStorage()
- setGraphicsCard()
- build()

### Task 2: User Builder

User object create karo jisme:

- Name required ho.
- Email required ho.
- Age optional ho.
- City optional ho.

`build()` method mein required properties validate karo.

### Task 3: API Request Builder

API request ke liye builder banao jisme:

- URL
- Method
- Headers
- Body

ko step-by-step configure kar sako.

## 17. Quick Revision

| Term             | Meaning                                     |
| ---------------- | ------------------------------------------- |
| Builder Pattern  | Complex object ko step-by-step create karna |
| Category         | Creational                                  |
| Product          | Final object                                |
| Builder          | Object construction handle karta hai        |
| Concrete Builder | Builder ki actual implementation            |
| Director         | Optional construction sequence controller   |
| build()          | Final object return karta hai               |
| Method Chaining  | Multiple methods ko chain karna             |
| return this      | Current object return karna                 |

### Important Points

- Builder Pattern complex objects ke liye useful hai.
- Object ko step-by-step configure kar sakte hain.
- `build()` final object return karta hai.
- `return this` method chaining allow karta hai.
- Director optional hai.
- Simple objects ke liye Builder avoid kar sakte hain.

## 18. Topic Completion Checklist

- [ ] Builder Pattern ka meaning samajh liya.
- [ ] Builder Pattern ki need samajh li.
- [ ] Basic working flow samajh liya.
- [ ] Product aur Builder samajh liya.
- [ ] Concrete Builder samajh liya.
- [ ] Director samajh liya.
- [ ] Method Chaining samajh li.
- [ ] Factory vs Builder difference samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Advantages aur disadvantages samajh liye.
- [ ] Interview questions revise kar liye.
- [ ] Practical tasks complete kar liye.

**Topic 22 Complete: Builder Pattern**
