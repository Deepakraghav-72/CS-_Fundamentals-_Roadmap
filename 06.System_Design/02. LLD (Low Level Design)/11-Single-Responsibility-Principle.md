# Single Responsibility Principle (SRP)

## 1. Introduction

SRP ka full form hai:

**Single Responsibility Principle**

Ye SOLID principles ka first principle hai.

Is principle ka main purpose hai ki ek class ki responsibilities clearly defined aur focused honi chahiye.

### Definition

A class should have only one reason to change.

### Simple language

Ek class ko ek hi type ki responsibility deni chahiye.

Agar ek class multiple unrelated kaam kar rahi hai, toh us class ko separate classes mein divide karna better hota hai.

**Important:** Iska matlab ye nahi hai ki ek class mein sirf ek method hona chahiye. Ek class mein multiple methods ho sakte hain, agar woh sab ek hi responsibility se related hain.

---

## 2. Real-Life Example

Maan lo ek restaurant hai.

Restaurant mein alag-alag kaam hote hain:

- Chef food prepare karta hai.
- Waiter customer ka order leta hai.
- Cashier payment handle karta hai.

Agar ek hi person ko ye saare kaam karne padhein, toh workload aur confusion badh sakta hai.

Software mein bhi isi tarah responsibilities ko separate rakhna useful hota hai.

---

## 3. SRP Violation – Wrong Example

Maan lo hum ek User class bana rahe hain.

```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  saveUser() {
    console.log("User saved in database");
  }

  sendEmail() {
    console.log("Email sent to", this.email);
  }

  generateReport() {
    console.log("User report generated");
  }
}

const user = new User("Rahul", "rahul@example.com");

user.saveUser();
user.sendEmail();
user.generateReport();
```

### Output

```text
User saved in database
Email sent to rahul@example.com
User report generated
```

### Is code mein problem kya hai?

User class multiple responsibilities perform kar rahi hai:

1. User data manage karna.
2. Database mein user save karna.
3. Email send karna.
4. Report generate karna.

Maan lo future mein email service change ho jati hai.

Toh humein User class mein bhi changes karne pad sakte hain.

Isi tarah database ya report generation change hone par bhi User class modify karni pad sakti hai.

Ye SRP violation hai.

---

## 4. SRP Follow Karne Wala Correct Example

Ab hum same code ko separate classes mein divide karenge.

```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
}

class UserRepository {
  save(user) {
    console.log("User saved:", user.name);
  }
}

class EmailService {
  send(user) {
    console.log("Email sent to:", user.email);
  }
}

class ReportService {
  generate(user) {
    console.log("Report generated for:", user.name);
  }
}

const user = new User("Rahul", "rahul@example.com");

const repository = new UserRepository();
const emailService = new EmailService();
const reportService = new ReportService();

repository.save(user);
emailService.send(user);
reportService.generate(user);
```

### Output

```text
User saved: Rahul
Email sent to: rahul@example.com
Report generated for: Rahul
```

### Explanation

Ab humne responsibilities separate kar di hain:

| Class          | Responsibility         |
| -------------- | ---------------------- |
| User           | User data manage karna |
| UserRepository | Database operations    |
| EmailService   | Email send karna       |
| ReportService  | Report generate karna  |

Ab agar email sending ka logic change hota hai, toh humein sirf EmailService par kaam karna hoga.

User class ko change karne ki zaroorat nahi padegi.

Yahi SRP hai.

---

## 5. What Does One Reason to Change Mean?

SRP ki definition mein ek important phrase hai:

**One Reason to Change**

Iska matlab hai ki ek class ke change hone ka reason uski focused responsibility se related hona chahiye.

Example:

UserRepository ki responsibility database operations hain.

Agar database save karne ka logic change hota hai, toh UserRepository change ho sakti hai.

Lekin email ka format change hone par UserRepository ko change karne ki zaroorat nahi honi chahiye.

### Easy Example

| Change                     | Kis class ko change karna chahiye? |
| -------------------------- | ---------------------------------- |
| User data structure change | User                               |
| Database save logic change | UserRepository                     |
| Email format change        | EmailService                       |
| Report format change       | ReportService                      |

---

## 6. SRP in C++

### Wrong Example

```cpp
#include <iostream>
using namespace std;

class Employee {
public:
    void getDetails() {
        cout << "Getting employee details\n";
    }

    void saveToDatabase() {
        cout << "Saving employee to database\n";
    }

    void generateSalaryReport() {
        cout << "Generating salary report\n";
    }
};

int main() {
    Employee emp;

    emp.getDetails();
    emp.saveToDatabase();
    emp.generateSalaryReport();

    return 0;
}
```

Problem: Employee class employee details, database saving aur report generation sab handle kar rahi hai.

### Correct Example

```cpp
#include <iostream>
using namespace std;

class Employee {
public:
    string name;

    Employee(string n) {
        name = n;
    }
};

class EmployeeRepository {
public:
    void save(Employee emp) {
        cout << "Saving " << emp.name << " to database\n";
    }
};

class SalaryReport {
public:
    void generate(Employee emp) {
        cout << "Generating salary report for "
             << emp.name << "\n";
    }
};

int main() {
    Employee emp("Rahul");

    EmployeeRepository repository;
    SalaryReport report;

    repository.save(emp);
    report.generate(emp);

    return 0;
}
```

### Output

```text
Saving Rahul to database
Generating salary report for Rahul
```

Ab har class ki responsibility focused hai.

---

## 7. SRP in MERN Stack

MERN Stack application mein SRP bahut useful hai.

Maan lo hum ek User Management API bana rahe hain.

Ek clean structure kuch aisa ho sakta hai:

```text
backend/
│
├── controllers/
│   └── userController.js
│
├── services/
│   └── userService.js
│
├── models/
│   └── User.js
│
├── repositories/
│   └── userRepository.js
│
└── routes/
    └── userRoutes.js
```

### Har file ka kaam

| File              | Responsibility                    |
| ----------------- | --------------------------------- |
| userRoutes.js     | API routes define karna           |
| userController.js | Request aur response handle karna |
| userService.js    | Business logic                    |
| User.js           | User ka data/model structure      |
| userRepository.js | Database operations               |

### Example Flow

```text
Client Request
      |
      v
userRoutes.js
      |
      v
userController.js
      |
      v
userService.js
      |
      v
userRepository.js
      |
      v
MongoDB
```

Example:

1. Client `/users` par request bhejta hai.
2. Route request ko controller tak bhejta hai.
3. Controller service ko call karta hai.
4. Service business logic execute karti hai.
5. Repository database operation perform karti hai.
6. Result wapas controller ke through client ko milta hai.

**Note:** Ye ek common architectural approach hai. Har chhote MERN project mein separate repository layer banana compulsory nahi hota.

---

## 8. Advantages of SRP

### 1. Easy Maintenance

Code change karna easy hota hai kyunki responsibilities separate hoti hain.

### 2. Easy Testing

Har class ko independently test kar sakte hain.

### 3. Code Reusability

Ek focused class ko doosre parts mein reuse kar sakte hain.

### 4. Less Coupling

Unrelated functionality ek hi class mein mix nahi hoti.

### 5. Easy Debugging

Error kis responsibility mein hai, identify karna comparatively easy hota hai.

### 6. Team Collaboration

Different developers separate classes ya modules par kaam kar sakte hain.

---

## 9. Disadvantages / Limitations

SRP ka overuse bhi nahi karna chahiye.

1. Bahut saari unnecessary classes create ho sakti hain.
2. Small projects unnecessarily complicated ho sakte hain.
3. Classes ke beech coordination badh sakta hai.
4. Overengineering ka risk hota hai.

**Remember:** SRP ka goal meaningful separation hai, maximum classes banana nahi.

---

## 10. Common Mistakes

1. Ek class mein multiple methods hone ko SRP violation samajhna.
2. Har method ke liye alag class banana.
3. Related responsibilities ko bhi unnecessarily separate kar dena.
4. Database logic, email logic aur business logic ko ek class mein rakhna.
5. SRP ko sirf JavaScript ya C++ ka rule samajhna.

SRP ek general software design principle hai.

---

## 11. Interview Questions and Answers

**Q1. What is SRP?**

SRP ke according ek class ki ek focused responsibility honi chahiye aur uske change hone ka ek main reason hona chahiye.

**Q2. What is the full form of SRP?**

Single Responsibility Principle.

**Q3. Does SRP mean one class should have only one method?**

No. Ek class mein multiple related methods ho sakte hain.

**Q4. What is a reason to change?**

Aisa requirement ya responsibility-related change jiski wajah se class modify karni pade.

**Q5. Why is SRP important?**

Ye code ko maintainable, reusable aur testable banane mein help karta hai.

**Q6. Give an example of SRP violation.**

Ek User class jo user data, database operations, email sending aur report generation sab handle kare.

**Q7. How can we fix an SRP violation?**

Responsibilities ko logically separate classes ya modules mein divide karke.

**Q8. Is SRP applicable to functions and modules?**

SRP primarily class-level principle ke roop mein explain hota hai, lekin same idea functions aur modules ko design karte waqt bhi useful hai.

**Q9. Can a class have multiple responsibilities if they are related?**

Class mein multiple methods ho sakte hain, agar woh ek cohesive responsibility ko support karte hain.

**Q10. What is the biggest benefit of SRP?**

Code ko change aur maintain karna easier banana.

---

## 12. Practice Tasks

### Task 1 – Student Management

Ek Student class banao jo:

- Student details store kare.
- Database mein save kare.
- Email send kare.

Pehle wrong design banao, phir SRP follow karke separate classes banao.

### Task 2 – E-commerce Application

In responsibilities ko separate classes mein divide karo:

- Product data.
- Order creation.
- Payment processing.
- Email notification.
- Invoice generation.

### Task 3 – Employee Management

C++ mein classes banao:

- Employee
- EmployeeRepository
- SalaryCalculator
- SalaryReport

Har class ki responsibility clearly define karo.

### Task 4 – MERN Architecture

Ek User Management API ke liye routes, controller aur service ki responsibilities likho.

---

## 13. Quick Revision

| Point             | Meaning                                 |
| ----------------- | --------------------------------------- |
| Full Form         | Single Responsibility Principle         |
| SOLID Position    | First principle                         |
| Main Rule         | One focused responsibility              |
| Main Benefit      | Easy maintenance                        |
| Famous Definition | One reason to change                    |
| Violation         | Unrelated responsibilities in one class |

### One-line Revision

**SRP = Ek class ko ek focused responsibility do, taaki unrelated changes ke liye us class ko modify na karna pade.**

---

## 14. Topic Completion Checklist

- [ ] SRP ka meaning samajh liya.
- [ ] One Reason to Change samajh liya.
- [ ] Wrong example samajh liya.
- [ ] Correct example samajh liya.
- [ ] C++ implementation practice kar li.
- [ ] JavaScript implementation practice kar li.
- [ ] MERN architecture mein SRP samajh liya.
- [ ] Advantages aur limitations samajh li.
- [ ] Interview questions revise kar liye.
- [ ] Practice tasks complete kar liye.

**Topic 11 Complete: Single Responsibility Principle (SRP)**
