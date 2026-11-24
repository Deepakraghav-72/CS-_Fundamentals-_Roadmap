# Topic 27: LLD Design Approach, Testing & Best Practices

# PART A: LLD DESIGN APPROACH

## 1. LLD Design Approach kya hai?

LLD Design Approach ka matlab hai kisi software problem ko systematically samajhna aur uske classes, objects, relationships, methods aur interactions design karna.

Simple language mein:

Maan lo tumhe ek Parking Lot Management System banana hai.

Code likhne se pehle tumhe decide karna hoga:

- System mein kaun-kaun si entities hongi?
- Kaun-kaun si classes banengi?
- Classes ke andar kaun se properties hongi?
- Kaun se methods honge?
- Classes ek doosre ke saath kaise interact karengi?
- System ko test kaise karenge?

In sab decisions ko systematically lena hi LLD Design Approach hai.

## 2. LLD Design karne ke steps

Ek achha LLD banane ke liye generally ye steps follow karte hain:

1. Problem Understanding
2. Requirements Gathering
3. Identify Entities
4. Identify Classes and Objects
5. Define Attributes and Methods
6. Define Relationships
7. Apply SOLID Principles
8. Choose Design Patterns
9. Create UML Diagrams
10. Implement the Code
11. Test the System
12. Refactor and Improve

Ab har step ko detail mein samajhte hain.

## 3. Step 1 – Problem Understanding

Sabse pehle problem ko clearly samjho.

Example:

Tumhe Parking Lot Management System design karna hai.

Is system mein:

- Vehicles parking mein enter karenge.
- Vehicles ko parking spots milenge.
- Vehicle parking se exit karega.
- Parking fee calculate hogi.
- Available spots ka status maintain hoga.

Problem ko samjhe bina directly coding start nahi karni chahiye.

## 4. Step 2 – Requirements Gathering

Requirements ka matlab hai system se kya-kya kaam karwana hai.

Requirements do important types ki hoti hain:

### A. Functional Requirements

Functional Requirements batati hain ki system kya-kya functionality provide karega.

Parking System ke examples:

1. Vehicle entry allow karna.
2. Available parking spot find karna.
3. Vehicle ko spot assign karna.
4. Parking ticket generate karna.
5. Vehicle exit process karna.
6. Parking fee calculate karna.
7. Available spots show karna.

### B. Non-Functional Requirements

Non-Functional Requirements batati hain ki system ki quality aur performance kaisi honi chahiye.

Examples:

- System fast hona chahiye.
- System reliable hona chahiye.
- Data secure hona chahiye.
- Code maintainable hona chahiye.
- Multiple users ko handle kar sake.

**Difference:**

| Functional Requirements | Non-Functional Requirements  |
| ----------------------- | ---------------------------- |
| System kya karega?      | System kaise perform karega? |
| Vehicle entry           | Fast response                |
| Ticket generation       | Reliability                  |
| Fee calculation         | Security                     |

## 5. Step 3 – Identify Entities

Entity ka matlab hai system ke andar present important real-world objects ya concepts.

Parking System mein entities:

- ParkingLot
- ParkingFloor
- ParkingSpot
- Vehicle
- ParkingTicket
- Payment

In entities ko identify karne se humein classes design karne mein help milti hai.

**Important:** Har entity ka separate class banana compulsory nahi hota. Class tab banani chahiye jab uski independent responsibility ya useful behavior ho.

## 6. Step 4 – Identify Classes and Objects

Class ek blueprint hoti hai, jabki object us class ka actual instance hota hai.

Parking System ke possible classes:

```text
ParkingLot
ParkingFloor
ParkingSpot
Vehicle
ParkingTicket
Payment
ParkingManager
```

Example:

```javascript
class Vehicle {
  constructor(number, type) {
    this.number = number;
    this.type = type;
  }
}

const vehicle1 = new Vehicle("UP13AB1234", "CAR");

console.log(vehicle1.number);
console.log(vehicle1.type);
```

Output:

```text
UP13AB1234
CAR
```

Yahan:

- `Vehicle` = Class
- `vehicle1` = Object

## 7. Step 5 – Define Attributes and Methods

Ab har class ke data aur behavior decide karte hain.

Example:

### Vehicle Class

Attributes:

- vehicleNumber
- vehicleType

Methods:

- getVehicleNumber()
- getVehicleType()

### ParkingSpot Class

Attributes:

- spotId
- spotType
- isAvailable

Methods:

- assignVehicle()
- removeVehicle()
- isFree()

### ParkingTicket Class

Attributes:

- ticketId
- entryTime
- exitTime
- vehicle

Methods:

- generateTicket()
- calculateDuration()

Example:

```javascript
class ParkingSpot {
  constructor(spotId, spotType) {
    this.spotId = spotId;
    this.spotType = spotType;
    this.isAvailable = true;
  }

  assignVehicle() {
    if (!this.isAvailable) {
      return false;
    }

    this.isAvailable = false;
    return true;
  }

  removeVehicle() {
    this.isAvailable = true;
  }
}

const spot = new ParkingSpot(1, "CAR");

console.log(spot.assignVehicle());
console.log(spot.isAvailable);
```

Output:

```text
true
false
```

## 8. Step 6 – Define Relationships

Ab decide karo ki classes ek doosre ke saath kaise connected hongi.

Important relationships:

### A. Association

Do independent objects ke beech relationship.

Example:

Driver aur Car.

Driver car ko use karta hai, lekin dono independently exist kar sakte hain.

### B. Aggregation

Weak whole-part relationship.

Example:

Department aur Professor.

Department ke remove hone ke baad bhi Professor independently exist kar sakta hai.

### C. Composition

Strong whole-part relationship.

Example:

House aur Room.

Is relationship mein part ka lifecycle whole ke saath closely connected hota hai.

### D. Inheritance

Ek class doosri class ke properties aur behavior inherit karti hai.

Example:

```javascript
class Vehicle {
  constructor(number) {
    this.number = number;
  }
}

class Car extends Vehicle {
  constructor(number) {
    super(number);
    this.type = "CAR";
  }
}
```

### E. Dependency

Ek class temporary ya limited use ke liye doosri class par depend karti hai.

Example: PaymentService kisi PaymentGateway ko method ke andar use kar sakti hai.

## 9. Step 7 – Apply SOLID Principles

SOLID principles code ko maintainable aur flexible banane mein help karte hain.

| Principle                 | Meaning                                             |
| ------------------------- | --------------------------------------------------- |
| S – Single Responsibility | Class ki ek clear responsibility honi chahiye       |
| O – Open/Closed           | Extension ke liye open, modification ke liye closed |
| L – Liskov Substitution   | Child class parent ki jagah safely use ho           |
| I – Interface Segregation | Unnecessary methods force nahi karne chahiye        |
| D – Dependency Inversion  | High-level modules abstractions par depend karein   |

Example:

Agar `ParkingSpot` class ke andar:

- Parking assign karna
- Payment process karna
- Email send karna
- Report generate karna

Sab kuch karwa rahe ho, toh class ki responsibilities bahut zyada ho jayengi.

Better design mein responsibilities separate classes ko deni chahiye.

## 10. Step 8 – Choose Design Patterns

Problem ke according suitable design pattern choose karo.

Examples:

| Problem                                  | Suitable Pattern |
| ---------------------------------------- | ---------------- |
| Object creation complex hai              | Factory          |
| Object ki single shared instance chahiye | Singleton        |
| Behavior dynamically add karna hai       | Decorator        |
| Complex subsystem simplify karna hai     | Facade           |
| Different algorithms switch karne hain   | Strategy         |
| Multiple objects ko notify karna hai     | Observer         |

Important:

Har problem mein design pattern forcefully use nahi karna chahiye.

Pattern tabhi use karo jab actual problem solve hoti ho.

## 11. Step 9 – Create UML Diagrams

UML ka full form Unified Modeling Language hai.

UML diagrams system ko visually represent karte hain.

LLD mein important diagrams:

### A. Class Diagram

Classes, attributes, methods aur relationships show karta hai.

Example:

```text
+----------------------+
|       Vehicle        |
+----------------------+
| - number             |
| - type               |
+----------------------+
| + getNumber()        |
| + getType()          |
+----------------------+
```

### B. Sequence Diagram

Objects ke beech messages ka order show karta hai.

Example:

```text
User       ParkingLot       ParkingSpot
 |              |                |
 | Enter        |                |
 |------------->|                |
 |              | Find Available |
 |              |--------------->|
 |              |                |
 |              | Assign Spot    |
 |              |--------------->|
 | Ticket       |                |
 |<-------------|                |
```

### C. Activity Diagram

System ke workflow ya activities show karta hai.

Example:

```text
Start
  |
Vehicle Entry
  |
Find Available Spot
  |
Spot Available?
  |
  | Yes
  v
Assign Spot
  |
Generate Ticket
  |
 End
```

## 12. Step 10 – Implement the Code

Ab design ko actual programming language mein implement karte hain.

LLD mein commonly use hoti hain:

- Java
- C++
- Python
- JavaScript

Tum JavaScript ke through bhi OOP aur design patterns implement kar sakte ho.

Implementation se pehle class responsibilities aur relationships clear hone chahiye.

## 13. Step 11 – Test the System

Code likhne ke baad check karna hota hai ki system expected behavior de raha hai ya nahi.

Testing ke different levels hote hain:

- Unit Testing
- Integration Testing
- System Testing
- End-to-End Testing

Inhe hum aage detail mein padhenge.

## 14. Step 12 – Refactor and Improve

Refactoring ka matlab hai code ka internal structure improve karna bina uske expected external behavior ko change kiye.

Example:

Agar ek class bahut badi ho gayi hai, toh uski responsibilities separate classes mein divide kar sakte hain.

Refactoring ke benefits:

- Readability improve hoti hai.
- Duplicate code reduce hota hai.
- Maintenance easy hoti hai.
- Code quality improve hoti hai.

---

# PART B: LLD TESTING

## 15. Software Testing kya hai?

Software Testing ek process hai jisme hum check karte hain ki software expected requirements ke according work kar raha hai ya nahi.

Simple language mein:

Hum code likhte hain aur phir verify karte hain ki:

- Correct output aa raha hai ya nahi.
- Errors aa rahe hain ya nahi.
- Different situations mein code sahi work kar raha hai ya nahi.

Example:

Parking spot available hai toh vehicle assign hona chahiye.

Parking spot already occupied hai toh doosre vehicle ko assign nahi hona chahiye.

In dono conditions ko test karna software testing hai.

## 16. Unit Testing

Unit Testing mein software ke smallest testable parts ko independently test kiya jata hai.

Usually individual functions ya methods test hote hain.

Example:

```javascript
function add(a, b) {
  return a + b;
}
```

Test:

```javascript
console.log(add(2, 3) === 5);
```

Output:

```text
true
```

Ye simple manual check hai. Proper unit testing mein Jest jaise testing framework use kar sakte hain.

## 17. Integration Testing

Integration Testing mein check karte hain ki multiple modules ya components ek saath correctly work kar rahe hain ya nahi.

Example:

E-commerce application mein:

```text
Order Service
     |
     v
Payment Service
     |
     v
Inventory Service
```

Test karna ki order create hone par payment aur inventory modules expected tarike se interact kar rahe hain ya nahi.

## 18. System Testing

System Testing mein complete application ko test kiya jata hai.

Example:

Parking System mein:

- Vehicle entry.
- Spot allocation.
- Ticket generation.
- Payment.
- Vehicle exit.

Complete workflow test karna System Testing hai.

## 19. End-to-End (E2E) Testing

E2E Testing mein real user ke perspective se complete workflow test karte hain.

Example: E-commerce website.

```text
User Login
    |
Browse Products
    |
Add to Cart
    |
Checkout
    |
Payment
    |
Order Confirmation
```

Is poore user journey ko test karna E2E Testing hai.

## 20. Unit vs Integration vs System vs E2E Testing

| Testing Type        | Kya Test Hota Hai?              |
| ------------------- | ------------------------------- |
| Unit Testing        | Individual function/class       |
| Integration Testing | Multiple modules ka interaction |
| System Testing      | Complete system                 |
| E2E Testing         | Complete user journey           |

## 21. Test Case kya hota hai?

Test Case ek set of conditions aur steps hota hai jisse hum kisi feature ki correctness verify karte hain.

Example: Parking Spot Assignment.

| Test Case | Input/Condition   | Expected Result             |
| --------- | ----------------- | --------------------------- |
| TC01      | Spot available    | Vehicle assigned            |
| TC02      | Spot occupied     | Assignment rejected         |
| TC03      | Spot becomes free | New vehicle can be assigned |
| TC04      | Invalid vehicle   | Request rejected            |

Good test cases mein normal cases ke saath edge cases bhi hone chahiye.

## 22. Edge Cases kya hote hain?

Edge Cases unusual ya boundary situations hoti hain jinhe test karna important hota hai.

Example:

Parking System:

- Parking lot completely full hai.
- Vehicle number empty hai.
- Vehicle already parked hai.
- Invalid vehicle type diya gaya hai.
- Exit request bina valid ticket ke aayi hai.

In conditions ko ignore karne se real application mein bugs aa sakte hain.

## 23. Test-Driven Development (TDD)

TDD ka full form Test-Driven Development hai.

Is approach mein pehle test likha jata hai, phir code implement kiya jata hai.

TDD ke 3 famous steps:

1. Red – Pehle failing test likho.
2. Green – Minimum code likho jo test pass kara de.
3. Refactor – Code ko improve karo aur tests dobara run karo.

```text
Write Test
    |
    v
Test Fails (Red)
    |
    v
Write Code
    |
    v
Test Passes (Green)
    |
    v
Refactor
    |
    v
Repeat
```

### TDD ke benefits

- Requirements clear hoti hain.
- Bugs early identify hote hain.
- Code testable banta hai.
- Refactoring mein confidence milta hai.

---

# PART C: JAVASCRIPT TESTING WITH JEST

## 24. Jest kya hai?

Jest JavaScript Testing Framework hai.

Iska use JavaScript code ke automated tests likhne aur run karne ke liye kiya jata hai.

Jest se:

- Unit tests.
- Integration tests.
- Mocking.
- Assertions.

kar sakte hain.

## 25. Jest ka basic example

Pehle project mein Jest install karo:

```bash
npm install --save-dev jest
```

`package.json` mein script add karo:

```json
{
  "scripts": {
    "test": "jest"
  }
}
```

### Step 1: Function file

`math.js`

```javascript
function add(a, b) {
  return a + b;
}

module.exports = add;
```

### Step 2: Test file

`math.test.js`

```javascript
const add = require("./math");

test("adds two numbers", () => {
  expect(add(2, 3)).toBe(5);
});
```

### Step 3: Test run karo

```bash
npm test
```

Expected result: Jest test ko pass show karega.

### Important Jest terms

| Term         | Meaning                              |
| ------------ | ------------------------------------ |
| test()       | Test case define karta hai           |
| expect()     | Actual result ko check karta hai     |
| toBe()       | Expected value se compare karta hai  |
| describe()   | Related tests ko group karta hai     |
| beforeEach() | Har test se pehle setup chalata hai  |
| afterEach()  | Har test ke baad cleanup chalata hai |

**Note:** Upar ka example CommonJS syntax use karta hai. Agar project ES Modules use karta hai, toh Jest configuration aur import/export syntax accordingly set karna hoga.

---

# PART D: LLD BEST PRACTICES

## 26. Best Practices kya hoti hain?

Best Practices ka matlab hai code likhne ke aise proven methods jo software ko readable, maintainable, reliable aur scalable banane mein help karte hain.

## 27. Single Responsibility Follow Karo

Har class ki ek clear responsibility honi chahiye.

Bad Example:

```javascript
class User {
  saveUser() {}
  sendEmail() {}
  generateReport() {}
  processPayment() {}
}
```

Is class ke andar unrelated responsibilities hain.

Better Example:

```javascript
class UserService {
  saveUser() {}
}

class EmailService {
  sendEmail() {}
}

class ReportService {
  generateReport() {}
}

class PaymentService {
  processPayment() {}
}
```

Ab har class ki responsibility clear hai.

## 28. DRY Principle

DRY ka full form hai:

**Don't Repeat Yourself.**

Iska matlab hai same logic ko baar-baar copy-paste karne se bachna.

Bad Example:

```javascript
function calculateTaxForA(price) {
  return price * 0.18;
}

function calculateTaxForB(price) {
  return price * 0.18;
}
```

Better Example:

```javascript
function calculateTax(price) {
  return price * 0.18;
}

console.log(calculateTax(1000));
console.log(calculateTax(2000));
```

Common logic ko reusable function mein rakho.

## 29. KISS Principle

KISS ka full form hai:

**Keep It Simple, Stupid.**

Iska meaning hai design ko unnecessarily complex mat banao.

Example:

Agar simple condition se problem solve ho sakti hai toh unnecessary design patterns aur extra classes mat banao.

Simple code aksar maintain karna easy hota hai.

## 30. YAGNI Principle

YAGNI ka full form hai:

**You Aren't Gonna Need It.**

Iska matlab hai aisi functionality abhi implement mat karo jiski actual requirement hi nahi hai.

Example:

Agar application mein abhi email login ki requirement hai, toh bina requirement ke 10 different login providers ka complex architecture mat banao.

Future possibilities ko dhyan mein rakhna achha hai, lekin unnecessary features banana nahi.

## 31. Composition over Inheritance

Is principle ka matlab hai jab suitable ho, toh inheritance ke comparison mein composition ko prefer karo.

Inheritance:

```javascript
class Animal {
  eat() {
    console.log("Eating");
  }
}

class Dog extends Animal {}
```

Composition:

```javascript
const canEat = {
  eat() {
    console.log("Eating");
  },
};

const dog = {
  ...canEat,
  bark() {
    console.log("Barking");
  },
};

dog.eat();
dog.bark();
```

Composition se objects ko different behaviors ke saath combine karna possible hota hai.

Lekin iska matlab ye nahi ki inheritance kabhi use nahi karna chahiye. Dono ka use situation ke according karo.

## 32. Loose Coupling

Loose Coupling ka matlab hai classes ek doosre ki internal implementation par unnecessarily depend na karein.

Example:

Agar OrderService directly kisi specific payment provider ke implementation par tightly depend karti hai, toh provider change karna difficult ho sakta hai.

Better design mein PaymentService ek common contract ke through different payment providers ko use kar sakti hai.

Benefits:

- Code flexible hota hai.
- Testing easier hoti hai.
- Changes ka impact kam hota hai.

## 33. High Cohesion

High Cohesion ka matlab hai ek class ke andar present methods aur properties ek hi related responsibility se connected honi chahiye.

Example:

PaymentService mein:

- processPayment()
- refundPayment()
- getPaymentStatus()

Ye related responsibilities hain.

Lekin usmein sendEmail() aur generatePDF() rakhna unnecessary ho sakta hai.

## 34. Encapsulation Follow Karo

Encapsulation ka matlab data aur us par operate karne wale methods ko ek unit mein organize karna aur internal data ko controlled access dena.

Example:

```javascript
class BankAccount {
  #balance = 0;

  deposit(amount) {
    if (amount <= 0) {
      throw new Error("Invalid amount");
    }

    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();

account.deposit(500);

console.log(account.getBalance());
```

Output:

```text
500
```

Yahan `#balance` private field hai. Isse class ke bahar directly access nahi kar sakte.

## 35. Meaningful Naming Use Karo

Variables, functions aur classes ke names meaningful hone chahiye.

Bad:

```javascript
let x = 100;

function calc(a, b) {
  return a * b;
}
```

Better:

```javascript
let productPrice = 100;

function calculateTotalPrice(price, quantity) {
  return price * quantity;
}
```

Code padhne wale ko easily samajh aana chahiye ki code kya kar raha hai.

## 36. Error Handling Proper Rakho

Application mein errors ko properly handle karna chahiye.

Example:

```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }

  return a / b;
}

try {
  console.log(divide(10, 0));
} catch (error) {
  console.log(error.message);
}
```

Output:

```text
Cannot divide by zero
```

Real-world applications mein errors ko meaningful tarike se handle aur log karna chahiye. Sensitive internal details user ko expose nahi karni chahiye.

## 37. Avoid God Class

God Class aisi class hoti hai jo bahut saari unrelated responsibilities handle karti hai.

Example:

```text
ApplicationManager
    |
    |-- User Management
    |-- Payment Processing
    |-- Email Sending
    |-- Report Generation
    |-- Database Management
    |-- Order Management
```

Problem:

- Class bahut complex ho jati hai.
- Testing difficult hoti hai.
- Changes ka impact badh jata hai.

Solution:

Responsibilities ko suitable separate classes/services mein divide karo.

## 38. Avoid Overengineering

Overengineering ka matlab hai simple problem ke liye unnecessary complex solution banana.

Example:

Agar ek simple calculator banana hai, toh uske liye 15 classes aur 5 design patterns banana zaroori nahi hai.

Rule:

**Simple requirement = Simple design.**

Requirements complex hon toh design ko accordingly improve karo.

---

# PART E: COMPLETE LLD DESIGN EXAMPLE

## 39. Parking Lot System – Design Approach

Ab tak padhe hue concepts ko ek example mein combine karte hain.

### Step 1: Requirements

Functional:

- Vehicle entry.
- Parking spot assignment.
- Ticket generation.
- Payment.
- Vehicle exit.

Non-Functional:

- Reliable.
- Maintainable.
- Fast response.
- Correct parking availability.

### Step 2: Identify Classes

```text
ParkingLot
ParkingFloor
ParkingSpot
Vehicle
ParkingTicket
Payment
ParkingManager
```

### Step 3: Responsibilities

| Class          | Responsibility                         |
| -------------- | -------------------------------------- |
| ParkingLot     | Complete parking facility manage karna |
| ParkingFloor   | Floor ke spots manage karna            |
| ParkingSpot    | Individual spot manage karna           |
| Vehicle        | Vehicle information rakhna             |
| ParkingTicket  | Entry aur exit information rakhna      |
| Payment        | Payment information manage karna       |
| ParkingManager | Parking workflow coordinate karna      |

### Step 4: Basic Class Relationship

```text
ParkingLot
    |
    v
ParkingFloor
    |
    v
ParkingSpot
    |
    v
Vehicle

ParkingManager
    |
    v
ParkingTicket
    |
    v
Payment
```

Ye simplified conceptual structure hai. Actual UML relationship aur multiplicity requirements ke according define hongi.

### Step 5: Basic Workflow

```text
Vehicle Arrives
      |
      v
Find Available Spot
      |
      v
Spot Available?
   /       \
 Yes        No
  |          |
  v          v
Assign      Reject
Spot        Entry
  |
  v
Generate Ticket
  |
  v
Vehicle Parks
  |
  v
Vehicle Exit
  |
  v
Calculate Fee
  |
  v
Process Payment
  |
  v
Release Spot
  |
  v
End
```

### Step 6: Testing Scenarios

- Available spot par vehicle assign ho.
- Full parking mein entry reject ho.
- Same spot do vehicles ko assign na ho.
- Valid ticket ke bina exit process na ho.
- Payment successful hone par spot release ho.
- Payment fail hone par correct recovery process ho.

### Step 7: Best Practices

- Har class ki responsibility clear rakho.
- SOLID principles follow karo.
- Unnecessary code duplication avoid karo.
- Proper error handling karo.
- Unit aur integration tests likho.
- Unnecessary design patterns use mat karo.

---

# PART F: INTERVIEW QUESTIONS

## 40. Important Interview Questions

### Q1. What is LLD Design Approach?

LLD Design Approach ek systematic process hai jisme problem ko understand karke classes, objects, relationships, methods aur interactions design kiye jaate hain.

### Q2. What is the difference between Functional and Non-Functional Requirements?

Functional requirements batati hain system kya karega, jabki Non-Functional requirements batati hain system ki quality aur performance kaisi honi chahiye.

### Q3. What is Unit Testing?

Unit Testing mein individual functions ya components ko independently test kiya jata hai.

### Q4. What is Integration Testing?

Integration Testing mein multiple modules ke beech interaction test kiya jata hai.

### Q5. What is TDD?

Test-Driven Development ek development approach hai jisme pehle test likhte hain, phir code implement karte hain aur uske baad refactor karte hain.

### Q6. What is Refactoring?

Refactoring code ki internal structure improve karna hai without changing its expected external behavior.

### Q7. What is DRY?

DRY ka full form Don't Repeat Yourself hai. Iska purpose repeated logic ko reduce karna hai.

### Q8. What is KISS?

KISS ka meaning Keep It Simple, Stupid hai. Design ko unnecessarily complex nahi banana chahiye.

### Q9. What is YAGNI?

YAGNI ka meaning You Aren't Gonna Need It hai. Unnecessary future features ko bina requirement implement nahi karna chahiye.

### Q10. What is Loose Coupling?

Loose Coupling ka matlab hai classes ke beech dependencies ko minimum aur manageable rakhna.

### Q11. What is High Cohesion?

High Cohesion ka matlab hai ek class ki responsibilities ek doosre se closely related honi chahiye.

### Q12. What is a God Class?

God Class ek aisi class hoti hai jo bahut saari unrelated responsibilities handle karti hai.

---

# PART G: PRACTICAL TASKS

## 41. Practical Coding Tasks

### Task 1: Library Management System

Classes design karo:

- Book
- Member
- Library
- IssueRecord

Requirements:

- Book add karna.
- Member register karna.
- Book issue karna.
- Book return karna.
- Available books show karna.

### Task 2: Unit Testing

Ek calculator class banao.

Methods:

- add()
- subtract()
- multiply()
- divide()

Har method ke liye unit tests likho.

Edge cases bhi test karo:

- Divide by zero.
- Negative numbers.
- Decimal numbers.

### Task 3: Apply SOLID

Ek single class mein User, Payment aur Email ka logic likho.

Phir use separate classes mein divide karo.

### Task 4: Parking Lot Design

Parking Lot ka basic LLD khud se design karo:

1. Requirements likho.
2. Classes identify karo.
3. Attributes aur methods decide karo.
4. Class diagram banao.
5. Parking entry aur exit workflow implement karo.
6. Test cases likho.

---

# PART H: QUICK REVISION

## 42. Quick Revision Notes

### LLD Design Approach

1. Problem Understand karo.
2. Requirements Gather karo.
3. Entities Identify karo.
4. Classes aur Objects banao.
5. Attributes aur Methods define karo.
6. Relationships define karo.
7. SOLID apply karo.
8. Suitable Design Patterns choose karo.
9. UML diagrams banao.
10. Code implement karo.
11. Testing karo.
12. Refactoring karo.

### Testing Types

| Type        | Purpose                |
| ----------- | ---------------------- |
| Unit        | Individual unit test   |
| Integration | Modules ka interaction |
| System      | Complete application   |
| E2E         | Complete user journey  |

### Best Practices

- SOLID
- DRY
- KISS
- YAGNI
- Composition over Inheritance
- Loose Coupling
- High Cohesion
- Encapsulation
- Meaningful Naming
- Proper Error Handling
- Avoid God Class
- Avoid Overengineering

### TDD

```text
Red → Green → Refactor
```

---

# 43. Topic Completion Checklist

- [ ] LLD Design Approach samajh liya.
- [ ] Problem Understanding samajh li.
- [ ] Functional aur Non-Functional Requirements samajh li.
- [ ] Entities aur Classes identify karna seekh liya.
- [ ] Attributes aur Methods define karna seekh liya.
- [ ] Relationships revise kar liye.
- [ ] SOLID Principles revise kar liye.
- [ ] UML Diagrams revise kar liye.
- [ ] Unit Testing samajh li.
- [ ] Integration Testing samajh li.
- [ ] System Testing samajh li.
- [ ] E2E Testing samajh li.
- [ ] Test Cases aur Edge Cases samajh liye.
- [ ] TDD samajh liya.
- [ ] Jest ka basic example samajh liya.
- [ ] DRY, KISS aur YAGNI samajh liye.
- [ ] Loose Coupling aur High Cohesion samajh liye.
- [ ] Refactoring aur Overengineering samajh liya.
- [ ] Parking Lot example revise kar liya.

**Topic 27 complete tab samjho jab tum kisi simple real-world problem ka LLD khud design kar sako aur uske test cases bhi likh sako.**
