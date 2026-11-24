# Topic 04: Encapsulation (OOP)

## 1. Encapsulation kya hota hai?

**Encapsulation** OOP (Object-Oriented Programming) ka ek important concept hai.

Iska matlab hai:

- Data (variables) aur us data par kaam karne wale methods (functions) ko ek single unit, yani class, ke andar rakhna.
- Data ko direct access se protect karna.
- Data ko access ya modify karne ke liye controlled methods provide karna.

Simple language mein:

**Encapsulation = Data + Methods + Controlled Access**

### Real-life example: Bank Account

Maan lo tumhara bank account hai.

Usmein:

- Account balance hota hai.
- Deposit karne ka option hota hai.
- Withdraw karne ka option hota hai.
- Balance check karne ka option hota hai.

Kya tumhe bank ke internal system mein jaakar directly balance change karne ki permission hoti hai?

Nahi!

Tum deposit ya withdraw jaise valid operations ke through balance change karte ho.

Isi concept ko programming mein Encapsulation kehte hain.

---

## 2. Encapsulation ki zaroorat kyun hoti hai?

Maan lo humne ek BankAccount class banayi:

```cpp
class BankAccount {
public:
    int balance;
};
```

Ab koi bhi object ka balance directly change kar sakta hai:

```cpp
BankAccount account;

account.balance = 5000;
account.balance = -10000;
```

Problem ye hai ki account ka balance negative bhi ho sakta hai.

Real bank account mein aisa nahi hona chahiye.

Isliye hum data ko `private` banate hain aur usko modify karne ke liye controlled methods provide karte hain.

---

## 3. Access Modifiers

C++ mein 3 important access modifiers hote hain:

1. `public`
2. `private`
3. `protected`

Ye decide karte hain ki class ke members ko kahan se access kiya ja sakta hai.

### A. Public

- Public members ko class ke bahar se bhi access kar sakte hain.
- Inka access sabhi allowed code ke liye available hota hai.

Example:

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;
};

int main() {
    Student s1;

    s1.name = "Rahul";

    cout << s1.name;

    return 0;
}
```

**Output:**

```text
Rahul
```

### B. Private

- Private members ko directly class ke bahar access nahi kar sakte.
- Class ke member functions unhe access kar sakte hain.
- Class ke objects ke through direct access allowed nahi hota.

Example:

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int age;
};

int main() {
    Student s1;

    // s1.age = 20; // Error

    return 0;
}
```

Yahan `age` private hai, isliye `main()` se directly access nahi kar sakte.

### C. Protected

- Protected members ko same class ke andar access kar sakte hain.
- Derived (child) classes bhi unhe access kar sakti hain.
- Normal class ke bahar se directly access nahi kar sakte.

Example:

```cpp
#include <iostream>
using namespace std;

class Parent {
protected:
    int age = 25;
};

class Child : public Parent {
public:
    void showAge() {
        cout << age;
    }
};

int main() {
    Child c1;

    c1.showAge();

    return 0;
}
```

**Output:**

```text
25
```

### Access Modifiers Comparison

| Modifier  | Same Class | Derived Class | Outside Class |
| --------- | ---------- | ------------- | ------------- |
| Public    | Yes        | Yes           | Yes           |
| Private   | Yes        | No (directly) | No            |
| Protected | Yes        | Yes           | No            |

**Important:** C++ mein `class` ke members by default private hote hain, jabki `struct` ke members by default public hote hain.

---

## 4. Getters and Setters

Jab data private hota hai, toh usko access ya update karne ke liye hum getter aur setter methods bana sakte hain.

### Getter

Getter ek method hota hai jo private data ki value return karta hai.

Example:

```cpp
int getAge() {
    return age;
}
```

### Setter

Setter ek method hota hai jo private data ki value update karta hai.

Example:

```cpp
void setAge(int newAge) {
    age = newAge;
}
```

### Complete Example

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int age;

public:
    void setAge(int newAge) {
        if (newAge > 0) {
            age = newAge;
        }
    }

    int getAge() {
        return age;
    }
};

int main() {
    Student s1;

    s1.setAge(20);

    cout << s1.getAge();

    return 0;
}
```

**Output:**

```text
20
```

Yahan:

- `age` private hai.
- `setAge()` age update karta hai.
- `getAge()` age return karta hai.
- Invalid age ko reject kiya ja sakta hai.

**Note:** Real projects mein object ki initial state valid rakhne ke liye constructor ka use bhi karna chahiye. Sirf setter par depend nahi karna chahiye.

---

## 5. Data Hiding

Data Hiding ka matlab hai class ke important data ko direct external access se protect karna.

Example:

```cpp
class BankAccount {
private:
    double balance;
};
```

Yahan `balance` private hai.

Isliye class ke bahar se koi directly balance change nahi kar sakta.

**Encapsulation aur Data Hiding ka relation:**

- Encapsulation data aur methods ko ek class mein organize karta hai.
- Data Hiding data ke direct access ko restrict karta hai.
- Private access modifier data hiding achieve karne ka ek common method hai.

---

## 6. Invariants kya hote hain?

**Invariant** ek aisi condition ya rule hota hai jo object ki valid state mein hamesha true rehna chahiye.

Example: Bank Account

Rule:

```text
Balance >= 0
```

Matlab account ka balance negative nahi hona chahiye.

Agar hum withdrawal karte hain, toh check karna padega ki sufficient balance available hai ya nahi.

Isi tarah:

- Student ki age valid range mein honi chahiye.
- Product ki price negative nahi honi chahiye.
- Quantity negative nahi honi chahiye.

Encapsulation methods ke through in rules ko maintain karne mein help karta hai.

---

## 7. Constructor aur Encapsulation

Constructor ek special member function hota hai jo object create hone par automatically call hota hai.

Encapsulation mein constructor ka use object ko starting se valid state dene ke liye hota hai.

Example:

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int age;

public:
    Student(int a) {
        if (a > 0) {
            age = a;
        } else {
            age = 1;
        }
    }

    int getAge() const {
        return age;
    }
};

int main() {
    Student s1(20);

    cout << s1.getAge();

    return 0;
}
```

**Output:**

```text
20
```

Yahan constructor ensure karta hai ki age starting se valid ho.

### Const Getter

```cpp
int getAge() const {
    return age;
}
```

Getter ke end mein `const` ka matlab hai ki ye member function object ki normal state ko modify nahi karega.

Ye C++ mein const correctness ka important part hai.

---

## 8. Complete Practical Example: Bank Account

Ye example Encapsulation ko achhe se samjhata hai.

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    double balance;

public:
    BankAccount(double initialBalance) {
        if (initialBalance >= 0) {
            balance = initialBalance;
        } else {
            balance = 0;
        }
    }

    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "Amount deposited successfully!" << endl;
        } else {
            cout << "Invalid deposit amount!" << endl;
        }
    }

    void withdraw(double amount) {
        if (amount <= 0) {
            cout << "Invalid withdrawal amount!" << endl;
        }
        else if (amount <= balance) {
            balance -= amount;
            cout << "Withdrawal successful!" << endl;
        }
        else {
            cout << "Insufficient balance!" << endl;
        }
    }

    double getBalance() const {
        return balance;
    }
};

int main() {
    BankAccount account(5000);

    account.deposit(2000);

    account.withdraw(1000);

    cout << "Final Balance: "
         << account.getBalance() << endl;

    return 0;
}
```

**Output:**

```text
Amount deposited successfully!
Withdrawal successful!
Final Balance: 6000
```

### Code kaise work kar raha hai?

1. `BankAccount account(5000)` se object create hota hai.
2. Constructor balance ko 5000 set karta hai.
3. `deposit(2000)` balance ko 7000 kar deta hai.
4. `withdraw(1000)` balance ko 6000 kar deta hai.
5. `getBalance()` final balance return karta hai.

### Is example mein Encapsulation kahan hai?

- `balance` private hai.
- Direct balance access nahi kar sakte.
- Deposit aur withdrawal methods ke through balance update hota hai.
- Invalid amount reject hota hai.
- Getter balance read karne ka controlled way deta hai.

---

## 9. JavaScript mein Encapsulation

Encapsulation sirf C++ mein nahi, JavaScript mein bhi use hota hai.

Modern JavaScript classes mein private fields ke liye `#` syntax use hota hai.

Example:

```javascript
class BankAccount {
  #balance;

  constructor(initialBalance) {
    this.#balance = initialBalance >= 0 ? initialBalance : 0;
  }

  deposit(amount) {
    if (amount > 0) {
      this.#balance += amount;
    }
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount(5000);

account.deposit(2000);

console.log(account.getBalance());
```

**Output:**

```text
7000
```

### Important Points

- `#balance` JavaScript ka private field hai.
- Isko class ke bahar directly access nahi kar sakte.
- `deposit()` controlled update karta hai.
- `getBalance()` value return karta hai.

Example:

```javascript
console.log(account.#balance);
```

Ye syntax error dega, kyunki private field class ke bahar access nahi ho sakta.

**Important:** JavaScript mein `_balance` sirf naming convention hai. Underscore lagane se field actually private nahi hoti. Real private field ke liye `#balance` use hota hai.

### JavaScript Getter and Setter

JavaScript mein `get` aur `set` keywords bhi use kar sakte hain.

```javascript
class Student {
  #age;

  constructor(age) {
    this.age = age;
  }

  get age() {
    return this.#age;
  }

  set age(value) {
    if (value > 0) {
      this.#age = value;
    }
  }
}

const student = new Student(20);

console.log(student.age);

student.age = 22;

console.log(student.age);
```

**Output:**

```text
20
22
```

---

## 10. MERN Stack mein Encapsulation

MERN Stack mein Encapsulation ka use different layers mein samajh sakte hain.

### A. Backend – JavaScript Classes

Backend mein private fields aur methods ka use karke internal data ko control kar sakte hain.

### B. Mongoose Validation

Mongoose schema mein validation lagana bhi data integrity maintain karne mein help karta hai.

Example:

```javascript
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },

  age: {
    type: Number,
    min: 1,
    max: 120,
  },
});
```

Yahan age ke liye validation lagayi gayi hai.

**Important Difference:** Mongoose validation database documents ke data ko validate karti hai. Ye class-based Encapsulation ke exactly same concept nahi hai.

### C. API ke through Controlled Access

Backend mein hum direct database access dene ke bajaye API routes aur business logic ke through data access karwate hain.

Example:

```text
Frontend
   |
   v
API Request
   |
   v
Backend Controller
   |
   v
Business Logic
   |
   v
Database
```

Isse application ke internal implementation ko control aur protect karna easy hota hai.

---

## 11. Advantages of Encapsulation

1. **Data Security:** Important data ko direct access se protect karta hai.
2. **Data Validation:** Invalid values ko reject kar sakte hain.
3. **Controlled Access:** Data ko modify karne ka proper method milta hai.
4. **Maintainability:** Code ko manage karna easy hota hai.
5. **Flexibility:** Internal implementation change karne par external code ko kam changes karne padte hain.
6. **Code Organization:** Data aur related methods ek class mein rehte hain.

## 12. Disadvantages of Encapsulation

1. Extra getter aur setter methods likhne pad sakte hain.
2. Small programs mein unnecessary complexity badh sakti hai.
3. Galat design ki wajah se unnecessary methods create ho sakte hain.
4. Har field ke liye getter/setter banana zaroori nahi hota.

**Best Practice:** Sirf wahi data expose karo jiska external code ko genuinely access chahiye.

---

## 13. Encapsulation vs Abstraction

Dono OOP concepts hain, lekin dono ka purpose different hai.

| Encapsulation                                           | Abstraction                                       |
| ------------------------------------------------------- | ------------------------------------------------- |
| Data aur methods ko class mein bundle karta hai         | Unnecessary implementation details hide karta hai |
| Controlled access provide karta hai                     | Essential features expose karta hai               |
| Data protection par focus karta hai                     | Complexity hide karne par focus karta hai         |
| Private/public jaise access modifiers use ho sakte hain | Abstract classes aur interfaces use ho sakte hain |

### Easy Example

**Encapsulation:** Bank account ka balance private rakhna aur deposit/withdraw methods provide karna.

**Abstraction:** User ko sirf ATM ke withdraw option ka use karna hota hai; ATM ka internal process samajhna zaroori nahi.

---

## 14. Common Mistakes

1. Important data ko public rakh dena.
2. Har variable ke liye bina reason getter/setter bana dena.
3. Setter mein validation na lagana.
4. Constructor mein initial state validate na karna.
5. Encapsulation aur Abstraction ko same samajhna.
6. JavaScript mein `_variable` ko actual private field samajhna.
7. `protected` ko class ke bahar publicly accessible samajhna.

---

## 15. Interview Questions and Answers

### Q1. What is Encapsulation?

Encapsulation is an OOP concept that bundles data and methods into a single unit and controls access to the internal data.

### Q2. What is Data Hiding?

Data Hiding means restricting direct access to internal data of a class.

### Q3. Which access modifiers are available in C++?

Public, Private and Protected.

### Q4. What is the difference between Getter and Setter?

- Getter reads and returns a value.
- Setter updates a value, often after validation.

### Q5. Can we access private members outside a class?

No, private members cannot be accessed directly from outside the class.

### Q6. What is an invariant?

An invariant is a condition that must remain true for an object to stay in a valid state.

### Q7. Is Encapsulation possible in JavaScript?

Yes. JavaScript supports private class fields using the `#` syntax.

### Q8. Is Encapsulation the same as Abstraction?

No. Encapsulation focuses on bundling and controlled access, while Abstraction focuses on hiding unnecessary implementation details.

---

## 16. Practice Tasks

### Task 1: Student Class

Ek `Student` class banao:

- Private variable: `age`
- Setter: `setAge()`
- Getter: `getAge()`
- Age zero ya negative accept nahi honi chahiye.

### Task 2: Bank Account

Ek `BankAccount` class banao:

- Private variable: `balance`
- Constructor mein initial balance set karo.
- `deposit()` method banao.
- `withdraw()` method banao.
- `getBalance()` method banao.
- Negative balance allow nahi hona chahiye.

### Task 3: Product Class

Ek `Product` class banao:

- Private variable: `price`
- Setter mein negative price reject karo.
- Getter se price return karo.

### Task 4: JavaScript Encapsulation

JavaScript mein `User` class banao:

- Private field: `#password`
- Constructor mein password set karo.
- Password ko directly access nahi karna chahiye.
- Ek method se password verify karo.

---

## 17. Quick Revision

| Concept          | Meaning                                  |
| ---------------- | ---------------------------------------- |
| Encapsulation    | Data + Methods + Controlled Access       |
| Data Hiding      | Direct access restrict karna             |
| Public           | Class ke bahar accessible                |
| Private          | Direct external access allowed nahi      |
| Protected        | Class aur derived class mein accessible  |
| Getter           | Value read karna                         |
| Setter           | Value update karna                       |
| Invariant        | Object ki valid-state condition          |
| Constructor      | Object ko initialize karna               |
| C++ const getter | Object ki normal state modify nahi karta |
| JS Private Field | `#fieldName`                             |

### One-Line Revision

**Encapsulation ka main purpose data aur related methods ko ek class mein bundle karke data ka access controlled banana hai.**

---

## 18. Completion Checklist

- [ ] Encapsulation ka meaning samajh liya.
- [ ] Public, Private aur Protected samajh liya.
- [ ] Getters aur Setters samajh liye.
- [ ] Data Hiding samajh li.
- [ ] Invariants samajh liye.
- [ ] Constructor ka role samajh liya.
- [ ] C++ Bank Account example samajh liya.
- [ ] JavaScript private fields samajh liye.
- [ ] Encapsulation vs Abstraction ka difference samajh liya.
- [ ] Practice tasks complete kar liye.

**Topic 04 – Encapsulation Complete.**
