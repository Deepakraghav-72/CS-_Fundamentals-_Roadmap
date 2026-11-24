# Topic 02: OOP Concepts Overview

## 1. What is OOP?

OOP ka full form **Object-Oriented Programming** hai.

OOP ek programming paradigm (approach) hai jisme hum program ko Classes aur Objects ke through organize karte hain.

Simple language mein:

**OOP mein hum real-world entities ko programming ke through represent karte hain.**

### Example

Real world mein ek Car hoti hai.

Car ki kuch properties hoti hain:

- Brand
- Color
- Model
- Speed

Aur kuch behaviors hote hain:

- Start
- Stop
- Accelerate
- Brake

Programming mein bhi hum Car ko ek object ke form mein represent kar sakte hain.

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    string color;

    void start() {
        cout << "Car Started";
    }
};

int main() {
    Car car1;

    car1.brand = "BMW";
    car1.color = "Black";

    car1.start();

    return 0;
}
```

Output:

```text
Car Started
```

Yahan:

- `Car` = Class
- `car1` = Object
- `brand`, `color` = Properties
- `start()` = Method

---

## 2. Why Do We Need OOP?

Maan lo tum ek student management system bana rahe ho.

Application mein 100 students hain.

Agar har student ka data alag-alag variables mein store karoge, to code difficult ho sakta hai.

Example:

```cpp
string student1Name = "Rahul";
int student1Age = 20;

string student2Name = "Aman";
int student2Age = 21;
```

Agar 1,000 students ho gaye, to data manage karna difficult ho jayega.

OOP ki help se hum ek Student class bana sakte hain.

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;
    int age;
};

int main() {
    Student s1;
    s1.name = "Rahul";
    s1.age = 20;

    Student s2;
    s2.name = "Aman";
    s2.age = 21;

    cout << s1.name << endl;
    cout << s2.name << endl;

    return 0;
}
```

Output:

```text
Rahul
Aman
```

Ab hum ek hi class se multiple objects create kar sakte hain.

---

## 3. Main Features of OOP

OOP ke four main pillars hote hain:

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

Inhe Four Pillars of OOP kaha jata hai.

```text
             OOP
              |
      +-------+-------+
      |       |       |
  Encapsulation  Abstraction
      |       |
  Inheritance  Polymorphism
```

In chaar concepts ka purpose code ko organized, reusable aur maintainable banana hai.

---

## 4. Encapsulation

### Definition

Encapsulation ka matlab hai data aur us data par kaam karne wale methods ko ek single unit (class) mein combine karna aur data ko controlled access dena.

Simple language mein:

**Data ko protect karna aur usko access karne ka controlled way provide karna Encapsulation hai.**

### Example

Bank account mein balance ko directly change karne ki permission nahi honi chahiye.

User deposit aur withdraw methods ke through balance change kare.

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    int balance = 1000;

public:
    void deposit(int amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    int getBalance() {
        return balance;
    }
};

int main() {
    BankAccount account;

    account.deposit(500);

    cout << account.getBalance();

    return 0;
}
```

Output:

```text
1500
```

Yahan:

- `balance` private hai.
- `deposit()` balance update karta hai.
- `getBalance()` balance read karta hai.

Isse data ko controlled access milta hai.

---

## 5. Abstraction

### Definition

Abstraction ka matlab hai unnecessary internal implementation details ko hide karke user ko sirf required functionality dikhana.

Simple language mein:

**User ko sirf ye batana ki kaam kaise use karna hai, andar kaise ho raha hai ye hide rakhna Abstraction hai.**

### Real-Life Example

Maan lo tum car drive karte ho.

Tum:

- Accelerator press karte ho.
- Brake press karte ho.
- Steering use karte ho.

Lekin tumhe engine ke andar ki complete working jaanna zaroori nahi hota.

Ye Abstraction ka example hai.

### Programming Example

```cpp
#include <iostream>
using namespace std;

class ATM {
public:
    void withdrawMoney() {
        checkBalance();
        cout << "Money Withdrawn";
    }

private:
    void checkBalance() {
        cout << "Checking Balance..." << endl;
    }
};

int main() {
    ATM atm;

    atm.withdrawMoney();

    return 0;
}
```

Output:

```text
Checking Balance...
Money Withdrawn
```

User sirf `withdrawMoney()` use karta hai. Internal method `checkBalance()` private hai.

---

## 6. Inheritance

### Definition

Inheritance ka matlab hai ek class ka doosri class ke properties aur methods ko inherit karna.

Simple language mein:

**Ek class doosri class ke existing features ko reuse kar sakti hai.**

### Example

Maan lo ek Parent class hai aur ek Child class hai.

Child class Parent class ke public aur protected members ko inherit kar sakti hai.

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "Animal is eating" << endl;
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Dog is barking";
    }
};

int main() {
    Dog d;

    d.eat();
    d.bark();

    return 0;
}
```

Output:

```text
Animal is eating
Dog is barking
```

Yahan:

- `Animal` = Parent/Base class
- `Dog` = Child/Derived class
- `Dog` ne `Animal` ka `eat()` method inherit kiya.

---

## 7. Polymorphism

### Definition

Polymorphism ka matlab hai one name, multiple forms.

Simple language mein:

**Ek hi interface ya method alag-alag situations mein different behavior de sakta hai.**

### Types of Polymorphism

1. Compile-time Polymorphism
2. Runtime Polymorphism

### A. Compile-time Polymorphism

Compile-time polymorphism mein compiler decide karta hai ki kaunsa function call hoga.

C++ mein function overloading iska example hai.

```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
};

int main() {
    Calculator c;

    cout << c.add(10, 20) << endl;
    cout << c.add(10, 20, 30);

    return 0;
}
```

Output:

```text
30
60
```

Same function name `add()` hai, lekin parameters different hain.

### B. Runtime Polymorphism

Runtime polymorphism mein function ka actual implementation runtime par decide hota hai.

C++ mein virtual functions ke through runtime polymorphism achieve kar sakte hain.

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal makes sound";
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks";
    }
};

int main() {
    Animal* animal = new Dog();

    animal->sound();

    delete animal;

    return 0;
}
```

Output:

```text
Dog barks
```

Yahan:

- `Animal` = Base class
- `Dog` = Derived class
- `virtual` runtime polymorphism enable karta hai.
- `override` batata hai ki derived class base class ke virtual function ko override kar rahi hai.

---

## 8. Four Pillars of OOP – Difference

| Pillar        | Main Purpose                                             |
| ------------- | -------------------------------------------------------- |
| Encapsulation | Data aur methods ko combine karke controlled access dena |
| Abstraction   | Internal details hide karna                              |
| Inheritance   | Existing features reuse karna                            |
| Polymorphism  | Multiple forms mein behavior provide karna               |

### Easy Trick to Remember

- Encapsulation = Data Protection
- Abstraction = Hiding Details
- Inheritance = Code Reuse
- Polymorphism = Multiple Forms

---

## 9. Other Important OOP Concepts

Four pillars ke alawa bhi kuch important concepts hain.

### 1. Class

Class ek blueprint hoti hai jiske through objects create hote hain.

### 2. Object

Object class ka instance hota hai.

### 3. Constructor

Constructor ek special member function hota hai jo object create hone par automatically call hota hai.

### 4. Destructor

Destructor ek special member function hota hai jo object destroy hone par automatically call hota hai.

### 5. Access Modifiers

Access modifiers decide karte hain ki class ke members ko kahan se access kiya ja sakta hai.

C++ mein:

- public
- private
- protected

In sabko hum aage detail mein padhenge.

---

## 10. OOP in Different Programming Languages

OOP concepts multiple programming languages mein use hote hain.

| Language   | OOP Support                       |
| ---------- | --------------------------------- |
| C++        | Yes                               |
| Java       | Yes                               |
| Python     | Yes                               |
| JavaScript | Yes, prototype-based object model |
| C#         | Yes                               |

### OOP in MERN Stack

MERN Stack mein JavaScript use hoti hai.

JavaScript mein classes available hain.

Example:

```javascript
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }

  login() {
    console.log(`${this.name} logged in`);
  }
}

const user1 = new User("Rahul", "rahul@gmail.com");

user1.login();
```

Output:

```text
Rahul logged in
```

MERN applications mein classes ke saath functions, objects aur modules bhi use hote hain.

OOP seekhne ka matlab ye nahi ki tumhe har JavaScript project classes mein hi likhna hai.

---

## 11. Advantages of OOP

1. Code reusability improve hoti hai.
2. Code organized rehta hai.
3. Data ko controlled access diya ja sakta hai.
4. Maintenance easier ho sakti hai.
5. Large applications manage karna easier hota hai.
6. Testing aur extension mein help milti hai.

---

## 12. Disadvantages of OOP

1. Small programs mein unnecessary complexity aa sakti hai.
2. Initial design mein time lag sakta hai.
3. Poor inheritance design code ko complex bana sakta hai.
4. Har problem ke liye OOP best solution nahi hota.
5. Overengineering ka risk hota hai.

---

## 13. Common Mistakes

1. Class aur Object ko same samajhna.
2. Encapsulation aur Abstraction ko same samajhna.
3. Inheritance ka unnecessary use karna.
4. Polymorphism ko sirf function overloading samajhna.
5. Har project mein classes compulsory samajhna.
6. OOP ko sirf four pillars tak limited samajhna.

---

## 14. Interview Questions

### Q1. What is OOP?

OOP is a programming paradigm that organizes software around objects and classes.

### Q2. What are the four pillars of OOP?

Encapsulation, Abstraction, Inheritance and Polymorphism.

### Q3. What is Encapsulation?

Combining data and related methods in a class while controlling access to data.

### Q4. What is Abstraction?

Hiding unnecessary implementation details and exposing essential functionality.

### Q5. What is Inheritance?

A mechanism through which one class can reuse features of another class.

### Q6. What is Polymorphism?

The ability to provide different behaviors through a common interface or method name.

### Q7. What are the types of Polymorphism?

- Compile-time Polymorphism
- Runtime Polymorphism

### Q8. Does JavaScript support OOP?

Yes. JavaScript supports object-oriented programming through objects and its prototype-based inheritance system. It also provides class syntax.

### Q9. What is the difference between Encapsulation and Abstraction?

Encapsulation focuses on bundling data and methods with controlled access, while abstraction focuses on hiding implementation details and exposing essential functionality.

### Q10. Is OOP always better than procedural programming?

No. The best programming approach depends on the problem and project requirements.

---

## 15. Practical Tasks

### Task 1

Real-life Car example ke liye identify karo:

- Properties
- Methods
- Class
- Object

### Task 2

Bank Account class banao jisme:

- balance private ho.
- deposit() method ho.
- withdraw() method ho.
- getBalance() method ho.

### Task 3

Animal aur Dog classes banao aur inheritance implement karo.

### Task 4

Calculator class banao aur function overloading implement karo.

### Task 5

JavaScript mein User class banao jisme:

- name
- email
- login()

hona chahiye.

---

## 16. Quick Revision

| Concept       | One-Line Meaning                                        |
| ------------- | ------------------------------------------------------- |
| OOP           | Classes aur objects based programming approach          |
| Encapsulation | Data aur methods ko combine karke access control        |
| Abstraction   | Unnecessary implementation details hide karna           |
| Inheritance   | Existing class features reuse karna                     |
| Polymorphism  | One interface, multiple behaviors                       |
| Compile-time  | Function selection compile time par                     |
| Runtime       | Function implementation runtime par decide hona         |
| Class         | Blueprint                                               |
| Object        | Class ka instance                                       |
| Constructor   | Object create hone par call hone wala special function  |
| Destructor    | Object destroy hone par call hone wala special function |

---

## 17. Topic Completion Checklist

- [ ] OOP ka meaning samajh liya.
- [ ] OOP ki need samajh li.
- [ ] Four Pillars of OOP samajh liye.
- [ ] Encapsulation samajh li.
- [ ] Abstraction samajh li.
- [ ] Inheritance samajh li.
- [ ] Polymorphism samajh liya.
- [ ] Compile-time aur Runtime Polymorphism samajh liya.
- [ ] JavaScript mein OOP ka basic idea samajh liya.
- [ ] Interview questions revise kar liye.
- [ ] Practical tasks practice kar liye.

**Topic 02 Complete – OOP Concepts Overview**
