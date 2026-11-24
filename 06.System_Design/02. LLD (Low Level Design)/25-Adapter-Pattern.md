# 25. Adapter Pattern

## 1. Adapter Pattern kya hota hai?

Adapter Pattern ek **Structural Design Pattern** hai.

Iska main purpose do incompatible interfaces ko compatible banana hai, taaki wo ek doosre ke saath kaam kar sakein.

Simple language mein:

**Adapter Pattern ek bridge ya converter ki tarah kaam karta hai, jo ek interface ko doosre interface ke expected format mein convert karta hai.**

### Real-Life Example: Mobile Charger

Maan lo tumhare paas ek mobile hai jiska charging port USB-C hai.

Lekin tumhare paas purana charger hai jiska connector Micro USB hai.

Dono directly compatible nahi hain.

Tum ek adapter use karte ho jo Micro USB connector ko USB-C ke compatible bana deta hai.

Software development mein Adapter Pattern bhi isi tarah kaam karta hai.

## 2. Adapter Pattern ki zaroorat kyon padti hai?

Maan lo tum ek application bana rahe ho.

Tumhara application ek payment service use karta hai jo ye method provide karti hai:

```javascript
makePayment(amount);
```

Lekin tumhe ek third-party payment provider use karna hai jo ye method provide karta hai:

```javascript
processTransaction(amount);
```

Dono ka kaam payment process karna hai, lekin method names aur interfaces different hain.

Directly use karne par compatibility problem aa sakti hai.

Adapter Pattern is problem ko solve kar sakta hai.

## 3. Adapter Pattern ka Basic Working

Adapter Pattern mein generally ye components hote hain:

1. Client
2. Target Interface
3. Adaptee
4. Adapter

Diagram:

```text
             Client
                |
                v
         Target Interface
                |
                v
             Adapter
                |
                v
             Adaptee
```

### Components ka meaning

- **Client:** Wo code jo service use karna chahta hai.
- **Target:** Wo interface jise client expect karta hai.
- **Adaptee:** Existing class ya third-party service jiska interface different hai.
- **Adapter:** Dono interfaces ke beech conversion karta hai.

## 4. Adapter Pattern Example in JavaScript

Maan lo hamare application ko `makePayment()` method chahiye.

Lekin third-party service `processTransaction()` provide karti hai.

### Step 1: Target Interface ka Expected Behavior

JavaScript mein interface keyword nahi hota, isliye hum expected method ko convention ke through define karenge.

```javascript
class PaymentProcessor {
  makePayment(amount) {
    throw new Error("makePayment() must be implemented");
  }
}
```

Client ko `makePayment()` method chahiye.

### Step 2: Existing Third-Party Class

```javascript
class OldPaymentGateway {
  processTransaction(amount) {
    console.log(`Payment of ${amount} processed by Old Gateway`);
  }
}
```

Is class mein `processTransaction()` method hai.

### Step 3: Adapter Class

```javascript
class PaymentAdapter extends PaymentProcessor {
  constructor(oldGateway) {
    super();
    this.oldGateway = oldGateway;
  }

  makePayment(amount) {
    this.oldGateway.processTransaction(amount);
  }
}
```

Adapter `makePayment()` ko `processTransaction()` se connect karta hai.

### Step 4: Client Code

```javascript
const oldGateway = new OldPaymentGateway();

const paymentAdapter = new PaymentAdapter(oldGateway);

paymentAdapter.makePayment(1000);
```

Output:

```text
Payment of 1000 processed by Old Gateway
```

### Step-by-Step Flow

1. Client `makePayment(1000)` call karta hai.
2. PaymentAdapter ka `makePayment()` execute hota hai.
3. Adapter internally `processTransaction(1000)` call karta hai.
4. OldPaymentGateway payment process karta hai.

Client ko third-party service ke internal method ka naam jaanne ki zaroorat nahi padti.

## 5. Adapter Pattern ke Main Components

### 1. Target

Client jis interface ya method ko expect karta hai.

Example: `makePayment()`.

### 2. Adaptee

Existing class ya third-party service jiska interface incompatible hai.

Example: `OldPaymentGateway`.

### 3. Adapter

Target aur Adaptee ko connect karta hai.

Example: `PaymentAdapter`.

### 4. Client

Adapter ke through service use karta hai.

Example: Application ka payment code.

## 6. Adapter Pattern ke Types

Adapter Pattern ke do commonly discussed forms hain:

### 1. Object Adapter

Object Adapter mein Adapter ke andar Adaptee ka object store kiya jata hai.

Is approach ko composition kehte hain.

Example:

```javascript
class PaymentAdapter {
  constructor(gateway) {
    this.gateway = gateway;
  }

  makePayment(amount) {
    this.gateway.processTransaction(amount);
  }
}
```

Yahan Adapter ke paas Gateway ka object hai.

### 2. Class Adapter

Class Adapter inheritance ke through Adaptee ka behavior inherit karta hai aur Target interface provide karta hai.

JavaScript mein multiple class inheritance supported nahi hai, isliye traditional Class Adapter approach directly implement karna possible nahi hota.

Object Adapter JavaScript applications mein commonly practical choice hota hai.

## 7. Adapter Pattern ka Real-World Example: Temperature Converter

Maan lo ek application Celsius temperature expect karti hai.

Lekin existing system Fahrenheit temperature return karta hai.

Adapter Fahrenheit ko Celsius mein convert kar sakta hai.

```javascript
class FahrenheitSensor {
  getTemperature() {
    return 98.6;
  }
}

class CelsiusAdapter {
  constructor(sensor) {
    this.sensor = sensor;
  }

  getTemperature() {
    const fahrenheit = this.sensor.getTemperature();

    return ((fahrenheit - 32) * 5) / 9;
  }
}

const sensor = new FahrenheitSensor();

const adapter = new CelsiusAdapter(sensor);

console.log(adapter.getTemperature());
```

Output:

```text
37
```

Yahan:

- FahrenheitSensor = Adaptee
- CelsiusAdapter = Adapter
- `getTemperature()` in Celsius = Target behavior
- Client = Adapter ko use karne wala code

## 8. Adapter Pattern vs Decorator Pattern

Dono Structural Design Patterns hain, lekin inka purpose alag hai.

| Adapter Pattern                       | Decorator Pattern                                      |
| ------------------------------------- | ------------------------------------------------------ |
| Interface compatible banata hai       | Existing object mein additional behavior add karta hai |
| Interface conversion par focus        | Behavior extension par focus                           |
| Client ko expected interface deta hai | Original interface generally preserve karta hai        |
| Example: Payment API adapter          | Example: Logging decorator                             |

### Easy Example

Adapter:

Ek third-party payment method ko apne application ke expected method ke according convert karna.

Decorator:

Payment process ke around extra logging ya monitoring add karna.

## 9. Adapter Pattern vs Facade Pattern

| Adapter                                          | Facade                                                  |
| ------------------------------------------------ | ------------------------------------------------------- |
| Incompatible interfaces ko compatible banata hai | Complex subsystem ko simple interface deta hai          |
| Interface conversion par focus                   | Complexity hide karne par focus                         |
| Usually existing service ko adapt karta hai      | Multiple subsystem operations ko organize kar sakta hai |
| Example: Old payment API adapter                 | Example: Video conversion facade                        |

## 10. Adapter Pattern ke Advantages

### 1. Compatibility

Incompatible classes ko ek saath work karne mein help karta hai.

### 2. Existing Code Reuse

Existing ya third-party code ko reuse kar sakte hain.

### 3. Loose Coupling

Client ko Adaptee ke internal interface se directly deal nahi karna padta.

### 4. Easy Integration

Different APIs aur services ko integrate karna easier ho sakta hai.

### 5. Better Maintainability

Interface conversion ko separate class mein manage kar sakte hain.

## 11. Adapter Pattern ke Disadvantages

### 1. Extra Classes

Adapter ke liye additional code likhna padta hai.

### 2. Complexity

Bahut saare adapters hone par application complicated ho sakti hai.

### 3. Performance Overhead

Adapter ke through additional method calls ya data conversion ho sakta hai.

### 4. Complex Conversion

Agar dono systems ke data structures bahut different hain, to adapter implementation complicated ho sakti hai.

## 12. MERN Stack mein Adapter Pattern

MERN applications mein Adapter Pattern bahut useful ho sakta hai, especially third-party APIs integrate karte waqt.

### Example 1: Payment Gateway Integration

Maan lo tumhare application ko ek common payment interface chahiye.

Lekin different providers ke methods different hain:

- Provider A: `createPayment()`
- Provider B: `processTransaction()`

Tum dono ke liye separate adapters bana sakte ho.

```javascript
class ProviderAAdapter {
  constructor(provider) {
    this.provider = provider;
  }

  pay(amount) {
    return this.provider.createPayment(amount);
  }
}

class ProviderBAdapter {
  constructor(provider) {
    this.provider = provider;
  }

  pay(amount) {
    return this.provider.processTransaction(amount);
  }
}
```

Ab application dono adapters ko common `pay()` method ke through use kar sakti hai.

### Example 2: External API Response Adapter

Maan lo tumhara frontend ye data expect karta hai:

```javascript
{
  fullName: "Rahul",
  email: "rahul@gmail.com"
}
```

Lekin third-party API ye data return karti hai:

```javascript
{
  first_name: "Rahul",
  email_address: "rahul@gmail.com"
}
```

Adapter data format convert kar sakta hai:

```javascript
function userAdapter(apiUser) {
  return {
    fullName: apiUser.first_name,
    email: apiUser.email_address,
  };
}

const apiResponse = {
  first_name: "Rahul",
  email_address: "rahul@gmail.com",
};

const user = userAdapter(apiResponse);

console.log(user);
```

Output:

```javascript
{
  fullName: "Rahul",
  email: "rahul@gmail.com"
}
```

### Example 3: Storage Provider Adapter

Maan lo application different file storage services use karti hai:

- Local Storage
- AWS S3
- Cloudinary

Har provider ka API different ho sakta hai.

Adapters common methods provide kar sakte hain, jaise:

- `uploadFile()`
- `deleteFile()`
- `getFileUrl()`

Isse application ke baaki code ko provider-specific methods jaanne ki zaroorat kam hoti hai.

## 13. Adapter Pattern kab use karna chahiye?

Adapter Pattern use karo jab:

1. Do classes ke interfaces incompatible hon.
2. Third-party API integrate karni ho.
3. Existing legacy code reuse karna ho.
4. Different services ko common interface dena ho.
5. Data formats convert karne hon.

### Kab avoid karna chahiye?

1. Dono interfaces already compatible hon.
2. Direct method call se kaam ho raha ho.
3. Adapter unnecessary complexity create kar raha ho.
4. Conversion logic bahut simple ho aur separate abstraction ki zaroorat na ho.

## 14. Common Mistakes

1. Adapter aur Decorator ko same samajhna.
2. Adapter aur Facade ko confuse karna.
3. Adapter ke andar unnecessary business logic add karna.
4. Existing Adaptee ka behavior galat map karna.
5. Error handling ignore karna.
6. Data conversion mein missing fields handle na karna.
7. Har third-party function ke liye unnecessary adapter banana.

## 15. Interview Questions & Answers

### Q1. What is Adapter Pattern?

Adapter Pattern ek Structural Design Pattern hai jo incompatible interfaces ko compatible banata hai.

### Q2. Why do we use Adapter Pattern?

Existing ya third-party classes ko apne application ke expected interface ke according use karne ke liye.

### Q3. What is Adaptee?

Adaptee wo existing class ya service hoti hai jiska interface client ke expected interface se different hota hai.

### Q4. What is Target?

Target wo interface hai jise client expect karta hai.

### Q5. What is Adapter?

Adapter wo class hoti hai jo Target aur Adaptee ke beech conversion karti hai.

### Q6. What are the types of Adapter Pattern?

Object Adapter aur Class Adapter.

### Q7. Which adapter approach uses composition?

Object Adapter.

### Q8. What is the difference between Adapter and Decorator?

Adapter interface compatibility provide karta hai, jabki Decorator additional behavior add karta hai.

### Q9. Is Adapter a Structural Pattern?

Yes.

### Q10. Give a real-world example.

Third-party payment gateway ke different methods ko application ke common payment interface mein convert karna.

## 16. Practical Tasks

### Task 1: Payment Adapter

Ek OldPaymentGateway class banao jisme `processTransaction()` method ho.

Ek PaymentAdapter banao jo `makePayment()` method provide kare.

Client ko sirf `makePayment()` use karna chahiye.

### Task 2: Temperature Adapter

Ek FahrenheitSensor class banao.

Ek CelsiusAdapter banao jo Fahrenheit temperature ko Celsius mein convert kare.

### Task 3: User Data Adapter

Ek API response adapter banao jo:

```javascript
{
  first_name: "Rahul",
  last_name: "Sharma",
  email_address: "rahul@gmail.com"
}
```

ko convert karke ye format return kare:

```javascript
{
  fullName: "Rahul Sharma",
  email: "rahul@gmail.com"
}
```

## 17. Quick Revision

| Term            | Meaning                                      |
| --------------- | -------------------------------------------- |
| Adapter Pattern | Incompatible interfaces ko compatible banana |
| Category        | Structural                                   |
| Target          | Client ka expected interface                 |
| Adaptee         | Existing incompatible class                  |
| Adapter         | Interface conversion karta hai               |
| Client          | Adapter ko use karta hai                     |
| Object Adapter  | Composition use karta hai                    |
| Class Adapter   | Inheritance use karta hai                    |

### Important Points

- Adapter Pattern Structural Design Pattern hai.
- Ye interface compatibility provide karta hai.
- Existing code ko reuse karne mein help karta hai.
- Object Adapter composition use karta hai.
- Class Adapter inheritance use karta hai.
- Adapter aur Decorator ka purpose different hai.
- Adapter aur Facade bhi different patterns hain.

## 18. Topic Completion Checklist

- [ ] Adapter Pattern ka meaning samajh liya.
- [ ] Adapter Pattern ki need samajh li.
- [ ] Working flow samajh liya.
- [ ] Target aur Adaptee samajh liya.
- [ ] Adapter aur Client samajh liya.
- [ ] Object Adapter samajh liya.
- [ ] Class Adapter samajh liya.
- [ ] JavaScript example samajh liya.
- [ ] Adapter vs Decorator samajh liya.
- [ ] Adapter vs Facade samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Interview questions revise kar liye.
- [ ] Practical tasks complete kar liye.

**Topic 25 Complete: Adapter Pattern**
