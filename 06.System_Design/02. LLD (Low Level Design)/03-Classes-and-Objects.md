# Topic 03: Classes & Objects

## 1. Introduction

OOP (Object-Oriented Programming) mein do bahut important concepts hote hain:

1. Class
2. Object

Class aur Object ki help se hum real-world entities ko programming mein represent kar sakte hain.

Example:

Real world mein:

- Car
- Student
- Employee
- Mobile
- Bank Account

Ye sab entities hain.

Programming mein inhe classes aur objects ke through represent kar sakte hain.

---

## 2. What is a Class?

### Definition

Class ek user-defined data type ya blueprint hoti hai jiske through hum objects create karte hain.

Simple language mein:

**Class ek design ya blueprint hoti hai jo batati hai ki object ke paas kaunsa data aur behavior hoga.**

### Real-Life Example

Maan lo tum ek Car banana chahte ho.

Car ke andar kuch properties hongi:

- Brand
- Color
- Model
- Speed

Aur kuch behaviors honge:

- Start
- Stop
- Accelerate
- Brake

Hum in sabka blueprint ek Car class mein define kar sakte hain.

### C++ Syntax

```cpp
class ClassName {
public:
    // Data Members

    // Member Functions
};
```

### Example

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
    return 0;
}
```

Yahan:

- `class` = Class declare karne ka keyword.
- `Car` = Class ka naam.
- `brand` = Data member.
- `color` = Data member.
- `start()` = Member function.

Abhi humne sirf class ka blueprint banaya hai. Object create nahi kiya.

---

## 3. What is an Object?

### Definition

Object ek class ka instance hota hai.

Simple language mein:

**Class ke blueprint se banne wali actual entity ko Object kehte hain.**

### Example

Maan lo Car ek class hai.

Us class se hum multiple cars ke objects bana sakte hain:

- car1
- car2
- car3

Har object ki properties alag ho sakti hain.

```text
             Car Class
          (Blueprint)
                |
       +--------+--------+
       |        |        |
       v        v        v
     car1     car2     car3
     BMW      Audi     Tata
```

### C++ Example

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string brand;
    string color;
};

int main() {

    Car car1;

    car1.brand = "BMW";
    car1.color = "Black";

    cout << car1.brand << endl;
    cout << car1.color << endl;

    return 0;
}
```

Output:

```text
BMW
Black
```

Yahan:

- `Car` = Class.
- `car1` = Object.
- `brand` aur `color` = Object ke data members.

---

## 4. Multiple Objects from One Class

Ek class se multiple objects create kar sakte hain.

Har object apni alag values store kar sakta hai.

### Example

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

    Student s3;
    s3.name = "Rohit";
    s3.age = 22;

    cout << s1.name << " " << s1.age << endl;
    cout << s2.name << " " << s2.age << endl;
    cout << s3.name << " " << s3.age << endl;

    return 0;
}
```

Output:

```text
Rahul 20
Aman 21
Rohit 22
```

### Important

Ek class se jitne required hon utne objects create kiye ja sakte hain, subject to available memory and other resource limits.

Har object ke non-static data members ki apni separate values hoti hain.

---

## 5. Data Members and Member Functions

Class ke andar mainly do cheezein define ki ja sakti hain:

1. Data Members
2. Member Functions

### A. Data Members

Data members class ke andar declare kiye gaye variables hote hain.

Ye object ki properties ya state represent karte hain.

Example:

```cpp
class Student {
public:
    string name;
    int age;
    float marks;
};
```

Yahan:

- name
- age
- marks

Data members hain.

### B. Member Functions

Member functions class ke andar defined ya declared functions hote hain.

Ye object ka behavior represent karte hain.

Example:

```cpp
class Student {
public:
    void study() {
        cout << "Student is studying";
    }
};
```

Yahan `study()` member function hai.

### Complete Example

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;
    int age;

    void introduce() {
        cout << "My name is " << name << endl;
        cout << "My age is " << age;
    }
};

int main() {

    Student s1;

    s1.name = "Rahul";
    s1.age = 20;

    s1.introduce();

    return 0;
}
```

Output:

```text
My name is Rahul
My age is 20
```

---

## 6. How to Access Class Members?

C++ mein object ke through public members ko access karne ke liye dot (`.`) operator use karte hain.

### Syntax

```cpp
objectName.memberName;
```

### Example

```cpp
Student s1;

s1.name = "Rahul";

s1.introduce();
```

Yahan:

- `s1.name` data member access karta hai.
- `s1.introduce()` member function call karta hai.

### Arrow Operator (`->`)

Jab object pointer ke through members access karte hain, tab arrow operator use hota hai.

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

    Student* ptr = &s1;

    cout << ptr->name;

    return 0;
}
```

Output:

```text
Rahul
```

`ptr->name` ka equivalent hai `(*ptr).name`.

---

## 7. Access Modifiers in Class

Access modifiers decide karte hain ki class ke members ko kahan se access kiya ja sakta hai.

C++ mein 3 main access modifiers hote hain:

1. Public
2. Private
3. Protected

### A. Public

Public members ko class ke bahar bhi access kiya ja sakta hai, subject to object access.

```cpp
class Student {
public:
    string name;
};
```

### B. Private

Private members ko directly class ke bahar access nahi kar sakte.

```cpp
class Student {
private:
    int age;
};
```

### C. Protected

Protected members ko class ke andar aur derived classes mein access kiya ja sakta hai. Non-friend outside code unhe directly access nahi kar sakta.

```cpp
class Student {
protected:
    int marks;
};
```

### Difference

| Public                        | Private                                     | Protected                              |
| ----------------------------- | ------------------------------------------- | -------------------------------------- |
| Outside class accessible      | Outside class directly accessible nahi      | Outside class directly accessible nahi |
| Derived class mein accessible | Derived class mein directly accessible nahi | Derived class mein accessible          |
| General public access         | Internal controlled access                  | Inheritance ke liye useful             |

**Important:** C++ mein `class` ke members ka default access modifier `private` hota hai. `struct` mein default access `public` hota hai.

---

## 8. Class vs Object

| Class                      | Object                            |
| -------------------------- | --------------------------------- |
| Blueprint hoti hai         | Class ka instance hota hai        |
| Data type define karti hai | Actual entity represent karta hai |
| Members define karti hai   | Members ki values hold karta hai  |
| Logical design             | Memory mein actual instance       |
| Example: Car               | Example: car1                     |

### Easy Example

```cpp
class Car {
public:
    string brand;
};

int main() {
    Car car1;
    car1.brand = "BMW";
}
```

Yahan:

- `Car` = Class.
- `car1` = Object.

---

## 9. Memory Allocation in Class and Object

Ye concept bahut important hai.

Class define karne se generally har non-static data member ke liye object wali memory allocate nahi hoti.

Jab object create hota hai, tab us object ke non-static data members ke liye memory space milti hai.

### Example

```cpp
class Student {
public:
    int age;
    float marks;
};

int main() {
    Student s1;
    Student s2;
}
```

Yahan:

- `s1` ka apna `age` aur `marks` hai.
- `s2` ka apna `age` aur `marks` hai.

Dono objects ki values independently change ho sakti hain.

**Note:** Actual object size compiler, alignment, padding aur class ke members par depend karta hai. Isliye hamesha sirf members ke sizes ko add karke exact size assume nahi karna chahiye.

---

## 10. Static Data Members

Static data member class se belong karta hai, individual objects ki separate copy nahi hoti.

Sabhi objects usi shared static member ko access karte hain.

### Example

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    static int count;
};

int Student::count = 0;

int main() {

    Student s1;
    Student s2;

    Student::count = 10;

    cout << s1.count << endl;
    cout << s2.count;

    return 0;
}
```

Output:

```text
10
10
```

Yahan `count` ki ek shared copy hai.

**Note:** C++ mein traditional static data member ko class ke bahar define karna hota hai, jaise `int Student::count = 0;`. C++17 se `inline static` members bhi use kar sakte hain.

---

## 11. Constructor – Basic Introduction

Constructor ek special member function hota hai jo object create hone par automatically call hota hai.

Constructor ka naam class ke naam jaisa hota hai.

Iska koi return type nahi hota.

### Example

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    Student() {
        cout << "Constructor Called";
    }
};

int main() {

    Student s1;

    return 0;
}
```

Output:

```text
Constructor Called
```

Constructor ko hum next topic mein detail mein padhenge.

---

## 12. Destructor – Basic Introduction

Destructor ek special member function hota hai jo object destroy hone par automatically call hota hai.

C++ mein destructor ka naam class ke naam se pehle tilde (`~`) lagakar likhte hain.

### Example

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    ~Student() {
        cout << "Destructor Called";
    }
};

int main() {

    Student s1;

    return 0;
}
```

Output:

```text
Destructor Called
```

Local object ka destructor scope end hone par automatically call hota hai.

Destructor ko bhi aage detail mein padhenge.

---

## 13. Class and Object in JavaScript

JavaScript mein bhi classes aur objects use kar sakte hain.

### Example

```javascript
class Student {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  introduce() {
    console.log(`My name is ${this.name}`);
    console.log(`My age is ${this.age}`);
  }
}

const s1 = new Student("Rahul", 20);

s1.introduce();
```

Output:

```text
My name is Rahul
My age is 20
```

### Explanation

- `class Student` = Class declaration.
- `constructor()` = Object initialize karta hai.
- `this.name` = Current object ka name.
- `new Student()` = New object create karta hai.
- `s1` = Object.

### C++ vs JavaScript

| C++                          | JavaScript                         |
| ---------------------------- | ---------------------------------- |
| `class Student`              | `class Student`                    |
| `Student s1;`                | `const s1 = new Student()`         |
| `s1.name`                    | `s1.name`                          |
| `public:` access section     | Native public class fields/methods |
| Constructor class ke naam se | `constructor()` keyword            |

JavaScript classes internally prototype-based inheritance system par work karti hain.

---

## 14. Real-World Example: Bank Account

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    int balance;

public:
    BankAccount() {
        balance = 0;
    }

    void deposit(int amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    void withdraw(int amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }

    int getBalance() {
        return balance;
    }
};

int main() {

    BankAccount account1;

    account1.deposit(5000);
    account1.withdraw(1000);

    cout << account1.getBalance();

    return 0;
}
```

Output:

```text
4000
```

### Explanation

- `BankAccount` = Class.
- `account1` = Object.
- `balance` = Private data member.
- `deposit()` = Money deposit karta hai.
- `withdraw()` = Money withdraw karta hai.
- `getBalance()` = Current balance return karta hai.

Ye class aur object ke saath encapsulation ka bhi example hai.

---

## 15. Common Mistakes

1. Class aur Object ko same samajhna.
2. Object create kiye bina non-static members access karne ki koshish karna.
3. Private member ko directly access karna.
4. `.` aur `->` operator confuse karna.
5. Constructor ko normal function samajhna.
6. Har object ke static member ki separate copy assume karna.
7. Class definition aur object creation mein difference na samajhna.

---

## 16. Interview Questions

### Q1. What is a class?

A class is a user-defined type that defines the data and behavior of its objects.

### Q2. What is an object?

An object is an instance of a class.

### Q3. Can we create multiple objects from one class?

Yes. One class can be used to create multiple objects.

### Q4. What are data members?

Variables declared inside a class are called data members.

### Q5. What are member functions?

Functions declared as members of a class are called member functions.

### Q6. What is the default access modifier of a C++ class?

Private.

### Q7. What is the difference between `.` and `->`?

`.` is used with an object, while `->` is used with a pointer to an object.

### Q8. What is a static data member?

A static data member is shared by all objects of a class.

### Q9. When is a constructor called?

It is called automatically when an object is initialized.

### Q10. What is a destructor?

A special member function that is called when an object is destroyed.

---

## 17. Practical Tasks

### Task 1: Car Class

Car class banao jisme:

- brand
- color
- model

Properties hon.

Ek `start()` method banao.

### Task 2: Student Class

Student class banao jisme:

- name
- age
- marks

Properties hon.

Ek `display()` method banao jo saari details print kare.

### Task 3: Multiple Objects

Ek Employee class banao aur uske 3 objects create karo.

Har object ke liye different:

- name
- salary
- employee ID

set karo.

### Task 4: Bank Account

BankAccount class banao jisme:

- private balance
- deposit()
- withdraw()
- getBalance()

methods hon.

### Task 5: JavaScript Practice

JavaScript mein Product class banao jisme:

- name
- price
- category

properties aur `displayProduct()` method ho.

---

## 18. Quick Revision

| Term            | Meaning                                 |
| --------------- | --------------------------------------- |
| Class           | Blueprint                               |
| Object          | Class ka instance                       |
| Data Member     | Class ke andar variable                 |
| Member Function | Class ke andar function                 |
| Public          | Outside class accessible                |
| Private         | Outside class directly accessible nahi  |
| Protected       | Derived class mein accessible           |
| Dot Operator    | Object members access karna             |
| Arrow Operator  | Pointer ke through members access karna |
| Static Member   | Class ke sabhi objects ke beech shared  |
| Constructor     | Object initialization                   |
| Destructor      | Object destruction ke time call         |

---

## 19. Topic Completion Checklist

- [ ] Class ka meaning samajh liya.
- [ ] Object ka meaning samajh liya.
- [ ] Class aur Object ka difference samajh liya.
- [ ] Multiple objects create karna seekh liya.
- [ ] Data members samajh liye.
- [ ] Member functions samajh liye.
- [ ] Dot aur Arrow operators samajh liye.
- [ ] Public, Private aur Protected ka basic idea samajh liya.
- [ ] Memory allocation ka basic concept samajh liya.
- [ ] Static data members samajh liye.
- [ ] Constructor aur Destructor ka basic introduction samajh liya.
- [ ] C++ aur JavaScript examples samajh liye.

**Topic 03 Complete – Classes & Objects**
