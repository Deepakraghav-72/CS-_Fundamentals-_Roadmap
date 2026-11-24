# OBJECT-ORIENTED PROGRAMMING (OOPS)

## Complete Notes – CS Fundamentals & Interview Preparation

**Language:** Easy Hinglish  
**Programming Language:** C++  
**Level:** Beginner to Advanced

---

# 1. Introduction to OOPS

## 1.1 What is OOPS?

OOPS ka full form Object-Oriented Programming System hai.

OOPS ek programming approach hai jisme program ko objects aur classes ke through organize kiya jata hai.

Objects ke andar data (attributes) aur functions (methods) hote hain.

**Example:**

Ek Car ke paas:

- Data: Color, Brand, Speed
- Functions: Start(), Stop(), Accelerate()

Yahan Car ek class ho sakti hai aur uski individual cars objects ho sakti hain.

## 1.2 Why OOPS?

OOPS use karne ke important reasons:

1. Code Reusability – Existing code ko dobara use kar sakte hain.
2. Data Security – Data ko unauthorized access se protect kar sakte hain.
3. Modularity – Program ko smaller components mein divide kar sakte hain.
4. Maintainability – Code ko update aur maintain karna easy hota hai.
5. Flexibility – Polymorphism se same interface ke different implementations bana sakte hain.
6. Scalability – Large applications ko organize karna easy hota hai.

## 1.3 Procedural Programming vs OOPS

| Procedural Programming                    | OOPS                                          |
| ----------------------------------------- | --------------------------------------------- |
| Functions par focus                       | Objects par focus                             |
| Top-down approach commonly                | Bottom-up approach commonly                   |
| Data aur functions separate ho sakte hain | Data aur methods class mein combine hote hain |
| Data security comparatively limited       | Encapsulation se better control               |
| Code reuse functions ke through           | Inheritance aur composition ke through        |
| Example: C                                | Example: C++, Java                            |

**Important:** C procedural programming language hai, jabki C++ procedural aur object-oriented dono programming styles support karti hai.

---

# 2. Class and Object

## 2.1 What is a Class?

Class ek user-defined data type ya blueprint hoti hai jiske through objects create kiye jaate hain.

Class mein:

- Data Members
- Member Functions

hote hain.

## 2.2 What is an Object?

Object class ka instance hota hai.

Object ke paas:

- State – Object ka data.
- Behavior – Object ke functions.
- Identity – Object ki unique identity.

## 2.3 Class and Object Example

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;
    int age;

    void display() {
        cout << name << endl;
        cout << age << endl;
    }
};

int main() {
    Student s1;

    s1.name = "Rahul";
    s1.age = 22;

    s1.display();

    return 0;
}
```

**Output:**

```text
Rahul
22
```

**Explanation:**

- Student = Class
- s1 = Object
- name, age = Data Members
- display() = Member Function

## 2.4 State, Behavior and Identity

| Concept  | Meaning                   | Example               |
| -------- | ------------------------- | --------------------- |
| State    | Object ka data            | Car color = Red       |
| Behavior | Object kya kar sakta hai  | Start, Stop           |
| Identity | Object ki unique identity | Particular car object |

## 2.5 How are objects created?

```cpp
Student s1;
Student s2;
```

Yahan do different objects create hue hain.

Dono objects ke data independent hote hain.

## 2.6 Memory Allocation

- Class define karne se individual object ka memory allocate nahi hota.
- Object create hone par uske non-static data members ke liye memory allocate hoti hai.
- Member functions generally object-wise duplicate nahi hote; unka code shared hota hai.
- Static data members class ke saath associated hote hain.

**Interview Question:** Class aur Object mein difference?

**Answer:** Class ek blueprint hai, jabki object us blueprint ka actual instance hai.

---

# 3. Four Pillars of OOPS

OOPS ke four major pillars hain:

1. Encapsulation
2. Abstraction
3. Inheritance
4. Polymorphism

Inhe detail mein samajhna bahut important hai.

---

# 4. Encapsulation

## 4.1 What is Encapsulation?

Encapsulation ka matlab data aur methods ko ek single unit (class) mein combine karna aur data access ko control karna hai.

Ismein data ko generally private rakha jata hai aur public methods ke through controlled access diya jata hai.

## 4.2 Example

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

**Output:**

```text
1500
```

## 4.3 How Encapsulation Works?

- balance private hai.
- Outside code directly balance modify nahi kar sakta.
- deposit() controlled modification provide karta hai.
- getBalance() balance read karne deta hai.

## 4.4 Advantages

1. Data Protection
2. Controlled Access
3. Better Maintainability
4. Improved Code Organization
5. Validation of Data

## 4.5 Getter and Setter

Getter: Private data ko read karne ke liye.

Setter: Private data ko modify karne ke liye.

```cpp
class Student {
private:
    int age;

public:
    void setAge(int a) {
        if (a > 0) {
            age = a;
        }
    }

    int getAge() {
        return age;
    }
};
```

**Interview Question:** Encapsulation ka main purpose kya hai?

**Answer:** Data aur methods ko ek unit mein combine karna aur controlled access provide karna.

---

# 5. Abstraction

## 5.1 What is Abstraction?

Abstraction ka matlab unnecessary implementation details ko hide karna aur user ko sirf essential functionality show karna hai.

**Real-life Example:**

ATM use karte waqt:

- Hum PIN enter karte hain.
- Amount select karte hain.
- Cash withdraw karte hain.

Humein ATM ke internal processing details nahi pata hoti.

Yahi abstraction hai.

## 5.2 Abstraction in C++

C++ mein abstraction achieve karne ke common ways:

1. Classes
2. Access Specifiers
3. Abstract Classes
4. Pure Virtual Functions

## 5.3 Abstract Class Example

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() = 0;
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks";
    }
};

int main() {
    Dog d;
    d.sound();

    return 0;
}
```

**Output:**

```text
Dog barks
```

## 5.4 Pure Virtual Function

Jis virtual function ko `= 0` assign kiya jata hai, use pure virtual function kehte hain.

```cpp
virtual void sound() = 0;
```

## 5.5 Abstract Class

Jis class mein at least one pure virtual function ho, woh abstract class hoti hai.

Important:

- Abstract class ka direct object create nahi kar sakte.
- Abstract class ka pointer ya reference bana sakte hain.
- Derived class ko pure virtual function implement karna hota hai agar woh concrete class banna chahti hai.

## 5.6 Interface in C++

C++ mein Java jaisa separate `interface` keyword nahi hota.

Pure abstract class ko interface ki tarah use kiya ja sakta hai.

## 5.7 Advantages of Abstraction

- Complexity reduce hoti hai.
- Implementation details hidden rehti hain.
- Code maintainable hota hai.
- User ko essential features milte hain.

---

# 6. Encapsulation vs Abstraction

| Encapsulation                         | Abstraction                              |
| ------------------------------------- | ---------------------------------------- |
| Data aur methods ko combine karta hai | Implementation details hide karta hai    |
| Access control par focus              | Essential functionality par focus        |
| Private, public, protected            | Abstract classes, pure virtual functions |
| How data is protected                 | What functionality is exposed            |

**Interview Tip:** Encapsulation aur Abstraction same nahi hain.

---

# 7. Inheritance

## 7.1 What is Inheritance?

Inheritance ek OOPS feature hai jisme ek class doosri class ke accessible members ko inherit karti hai.

Existing class = Parent/Base Class

New class = Child/Derived Class

## 7.2 Example

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "Eating..." << endl;
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Barking...";
    }
};

int main() {
    Dog d;

    d.eat();
    d.bark();

    return 0;
}
```

**Output:**

```text
Eating...
Barking...
```

Yahan Dog class ne Animal class ko inherit kiya hai.

## 7.3 Types of Inheritance

C++ mein five major inheritance types hain.

### 1. Single Inheritance

Ek derived class ek base class ko inherit karti hai.

```cpp
class A {
public:
    void show() {}
};

class B : public A {
};
```

Structure:

```text
A
|
B
```

### 2. Multilevel Inheritance

Ek class doosri class ko inherit karti hai aur teesri class us derived class ko inherit karti hai.

```cpp
class A {};
class B : public A {};
class C : public B {};
```

Structure:

```text
A
|
B
|
C
```

### 3. Multiple Inheritance

Ek derived class multiple base classes ko inherit karti hai.

```cpp
class A {};
class B {};

class C : public A, public B {};
```

Structure:

```text
A     B
 \   /
   C
```

### 4. Hierarchical Inheritance

Ek base class se multiple derived classes inherit karti hain.

```cpp
class Animal {};

class Dog : public Animal {};
class Cat : public Animal {};
```

Structure:

```text
    Animal
    /    \
  Dog    Cat
```

### 5. Hybrid Inheritance

Do ya zyada inheritance types ko combine karna Hybrid Inheritance kehlata hai.

Example: Multiple + Multilevel Inheritance.

## 7.4 Access Modes in Inheritance

C++ mein inheritance ke three access modes hain:

1. Public
2. Protected
3. Private

| Base Class Member | Public Inheritance       | Protected Inheritance    | Private Inheritance      |
| ----------------- | ------------------------ | ------------------------ | ------------------------ |
| Public            | Public                   | Protected                | Private                  |
| Protected         | Protected                | Protected                | Private                  |
| Private           | Directly accessible nahi | Directly accessible nahi | Directly accessible nahi |

**Important:**

- Private members inherit hone wale object ka part ho sakte hain, lekin derived class unhe directly access nahi kar sakti.
- Public inheritance mein public members public hi rehte hain.
- Protected members derived class ke andar accessible hote hain.

## 7.5 Advantages of Inheritance

1. Code Reusability
2. Reduced Code Duplication
3. Better Organization
4. Extensibility
5. Supports Runtime Polymorphism

## 7.6 Disadvantages of Inheritance

- Tight coupling ho sakti hai.
- Deep inheritance hierarchy difficult hoti hai.
- Parent class changes child classes ko affect kar sakte hain.
- Multiple inheritance mein ambiguity aa sakti hai.

---

# 8. Polymorphism

## 8.1 What is Polymorphism?

Polymorphism ka meaning hai One Name, Many Forms.

Ismein same function name ya interface different situations mein different behavior perform kar sakta hai.

Polymorphism ke two major types hain:

1. Compile-Time Polymorphism
2. Runtime Polymorphism

## 8.2 Compile-Time Polymorphism

Function call ka resolution compile time par hota hai.

Common examples:

- Function Overloading
- Operator Overloading

### A. Function Overloading

Same class mein same function name ke multiple functions define karna, lekin parameters different hone chahiye.

Parameters differ kar sakte hain:

- Number of parameters
- Type of parameters
- Order of parameter types

Example:

```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
};

int main() {
    Calculator c;

    cout << c.add(2, 3) << endl;
    cout << c.add(2.5, 3.5) << endl;
    cout << c.add(1, 2, 3);

    return 0;
}
```

**Output:**

```text
5
6
6
```

**Important Interview Point:**

Sirf return type change karne se function overloading nahi hoti.

Invalid example:

```cpp
int show();
double show();
```

### B. Operator Overloading

C++ mein existing operators ko user-defined types ke liye customize kar sakte hain.

Example:

```cpp
#include <iostream>
using namespace std;

class Number {
public:
    int value;

    Number(int v) {
        value = v;
    }

    Number operator+(Number obj) {
        return Number(value + obj.value);
    }
};

int main() {
    Number n1(10);
    Number n2(20);

    Number n3 = n1 + n2;

    cout << n3.value;

    return 0;
}
```

**Output:**

```text
30
```

**Important Operator Overloading Rules:**

- At least one operand user-defined type ka hona chahiye.
- New operators create nahi kar sakte.
- Operator precedence change nahi kar sakte.
- Operator associativity change nahi kar sakte.
- Kuch operators overload nahi hote.

Common non-overloadable operators:

- `::`
- `.`
- `.*`
- `?:`
- `sizeof`

---

# 9. Runtime Polymorphism

Runtime par function ka actual implementation decide hota hai.

C++ mein runtime polymorphism primarily virtual functions aur overriding ke through achieve hota hai.

## 9.1 Function Overriding

Jab derived class base class ke virtual function ko apne implementation ke saath redefine karti hai, use overriding kehte hain.

Example:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal sound";
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks";
    }
};

int main() {
    Dog d;
    Animal* ptr = &d;

    ptr->sound();

    return 0;
}
```

**Output:**

```text
Dog barks
```

## 9.2 Virtual Function

Virtual function base class mein declare kiya gaya function hota hai jo derived class mein override ho sakta hai.

`virtual` keyword runtime polymorphism enable karta hai.

## 9.3 Dynamic Binding

Jab function call ka actual implementation runtime par decide hota hai, use dynamic binding ya late binding kehte hain.

## 9.4 Static Binding vs Dynamic Binding

| Static Binding             | Dynamic Binding        |
| -------------------------- | ---------------------- |
| Compile time               | Runtime                |
| Early binding              | Late binding           |
| Non-virtual calls commonly | Virtual function calls |
| Resolution compile time    | Resolution runtime     |

## 9.5 Function Overloading vs Overriding

| Overloading               | Overriding                            |
| ------------------------- | ------------------------------------- |
| Same function name        | Same virtual function signature       |
| Different parameter lists | Compatible signature in derived class |
| Usually same class        | Base and derived class                |
| Compile-time polymorphism | Runtime polymorphism                  |
| Inheritance required nahi | Inheritance required                  |

**Important:** C++ mein overriding ke liye base function ka virtual hona runtime polymorphism ke liye important hai. `override` keyword compiler ko override intention verify karne deta hai.

---

# 10. Constructors

## 10.1 What is a Constructor?

Constructor ek special member function hai jo object create hone par automatically call hota hai.

Properties:

- Name class ke same hota hai.
- Return type nahi hota.
- Object initialization ke liye use hota hai.
- Overload ho sakta hai.

## 10.2 Default Constructor

Jis constructor ko zero arguments ke saath call kiya ja sakta hai, woh default constructor kehlata hai.

```cpp
class Student {
public:
    Student() {
        cout << "Default Constructor";
    }
};
```

## 10.3 Parameterized Constructor

Jis constructor mein parameters pass kiye jaate hain.

```cpp
class Student {
public:
    int age;

    Student(int a) {
        age = a;
    }
};
```

## 10.4 Copy Constructor

Ek existing object se new object initialize karne wala constructor copy constructor kehlata hai.

Typical signature:

```cpp
ClassName(const ClassName& obj);
```

Example:

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    int age;

    Student(int a) {
        age = a;
    }

    Student(const Student& obj) {
        age = obj.age;
    }
};

int main() {
    Student s1(22);
    Student s2 = s1;

    cout << s2.age;

    return 0;
}
```

**Output:**

```text
22
```

## 10.5 Move Constructor

Move constructor existing object ke resources ko new object mein transfer karne ke liye use hota hai.

Typical signature:

```cpp
ClassName(ClassName&& obj);
```

Isse unnecessary copying reduce ho sakti hai.

## 10.6 Constructor Overloading

Ek class mein multiple constructors different parameters ke saath define karna.

```cpp
class Student {
public:
    Student() {}
    Student(int age) {}
    Student(string name, int age) {}
};
```

## 10.7 Constructor Initialization List

Members initialize karne ka efficient aur important way.

```cpp
class Student {
    int age;

public:
    Student(int a) : age(a) {}
};
```

Important:

- Const members ko initialization list se initialize karna hota hai.
- Reference members ko initialization list se initialize karna hota hai.
- Base class constructor initialize karne ke liye useful hai.
- Members actual initialization order declaration order hota hai, list order nahi.

---

# 11. Destructor

## 11.1 What is a Destructor?

Destructor ek special member function hai jo object destroy hone par automatically call hota hai.

Syntax:

```cpp
class Student {
public:
    ~Student() {
        cout << "Destructor Called";
    }
};
```

Properties:

- Name class ke same hota hai, lekin `~` prefix hota hai.
- Return type nahi hota.
- Parameters nahi hote.
- Ek class mein normally ek destructor hota hai.
- Resources release karne ke liye use hota hai.

## 11.2 Constructor vs Destructor

| Constructor                 | Destructor                  |
| --------------------------- | --------------------------- |
| Object initialize karta hai | Object cleanup karta hai    |
| Object creation par call    | Object destruction par call |
| Class name                  | Class name with `~`         |
| Parameters ho sakte hain    | Parameters nahi hote        |
| Overloading possible        | Overloading possible nahi   |

## 11.3 Virtual Destructor

Base class pointer ke through derived object delete karte waqt correct destruction ensure karne ke liye base class destructor ko virtual banana chahiye.

```cpp
class Base {
public:
    virtual ~Base() {
        cout << "Base Destructor\n";
    }
};

class Derived : public Base {
public:
    ~Derived() {
        cout << "Derived Destructor\n";
    }
};
```

**Important Interview Question:** Base class destructor virtual kyu hona chahiye?

**Answer:** Taaki base class pointer se derived object delete karne par derived aur base dono destructors correctly execute hon.

---

# 12. this Pointer

`this` ek special pointer hai jo current object ko refer karta hai.

Example:

```cpp
class Student {
public:
    int age;

    Student(int age) {
        this->age = age;
    }
};
```

Yahan:

- `this->age` = Current object ka data member.
- `age` = Constructor ka parameter.

Uses:

1. Current object access karna.
2. Data members aur parameters differentiate karna.
3. Current object return karna.
4. Method chaining support karna.

Important:

- `this` non-static member functions mein available hota hai.
- Static member functions mein `this` available nahi hota.

---

# 13. Static Members

## 13.1 Static Data Member

Static data member class ke sabhi objects ke beech shared hota hai.

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    static int count;

    Student() {
        count++;
    }
};

int Student::count = 0;

int main() {
    Student s1;
    Student s2;

    cout << Student::count;

    return 0;
}
```

**Output:**

```text
2
```

## 13.2 Static Member Function

Static member function class se belong karta hai, individual object se nahi.

```cpp
class Student {
public:
    static int count;

    static void show() {
        cout << count;
    }
};

int Student::count = 10;
```

Call:

```cpp
Student::show();
```

Important:

- Static function directly non-static members access nahi kar sakta.
- Static function ke paas `this` pointer nahi hota.
- Static data member sab objects ke beech shared hota hai.

---

# 14. Friend Function and Friend Class

## 14.1 Friend Function

Friend function class ka member nahi hota, lekin class ke private aur protected members access kar sakta hai.

Example:

```cpp
#include <iostream>
using namespace std;

class Student {
private:
    int marks = 90;

    friend void display(Student s);
};

void display(Student s) {
    cout << s.marks;
}

int main() {
    Student s;
    display(s);

    return 0;
}
```

**Output:**

```text
90
```

## 14.2 Friend Class

Ek class ko doosri class ka friend declare kar sakte hain.

```cpp
class A {
private:
    int x = 10;

    friend class B;
};

class B {
public:
    void show(A obj) {
        cout << obj.x;
    }
};
```

Important:

- Friendship inherited nahi hoti.
- Friendship reciprocal nahi hoti.
- Friendship transitive nahi hoti.
- Friend function class ka member nahi hota.

---

# 15. Access Specifiers

C++ mein three main access specifiers hote hain.

## 15.1 Public

Public members ko class ke bahar bhi access kar sakte hain.

## 15.2 Private

Private members ko directly class ke bahar access nahi kar sakte.

## 15.3 Protected

Protected members class aur derived classes ke andar accessible hote hain.

| Access    | Same Class | Derived Class    | Outside Class |
| --------- | ---------- | ---------------- | ------------- |
| Public    | Yes        | Yes              | Yes           |
| Protected | Yes        | Yes              | No            |
| Private   | Yes        | No direct access | No            |

**Important:**

- `class` ka default access specifier = private.
- `struct` ka default access specifier = public.

---

# 16. Association, Aggregation and Composition

Ye OOPS ke important object relationships hain.

## 16.1 Association

Association ka matlab two independent classes ke objects ke beech relationship hona.

Example:

Teacher teaches Student.

Dono independently exist kar sakte hain.

## 16.2 Aggregation

Aggregation weak HAS-A relationship hai.

Ek object doosre object ko use karta hai, lekin dono independently exist kar sakte hain.

Example:

Department has Teachers.

Department delete hone ke baad bhi Teacher exist kar sakta hai.

## 16.3 Composition

Composition strong HAS-A relationship hai.

Ek object doosre object ke lifecycle ka owner hota hai.

Example:

House has Rooms.

House destroy hone par uske owned Room objects bhi destroy ho sakte hain.

## 16.4 Difference

| Association          | Aggregation             | Composition                    |
| -------------------- | ----------------------- | ------------------------------ |
| General relationship | Weak HAS-A              | Strong HAS-A                   |
| Independent objects  | Independent lifecycle   | Ownership relationship         |
| Loose relationship   | Whole-part relationship | Strong whole-part relationship |

**Interview Tip:** In relationships ko UML diagrams mein bhi represent kiya jata hai.

---

# 17. IS-A vs HAS-A Relationship

## IS-A

Inheritance relationship.

Example:

Dog IS-A Animal.

```cpp
class Animal {};
class Dog : public Animal {};
```

## HAS-A

Composition ya Aggregation relationship.

Example:

Car HAS-A Engine.

**Difference:**

- IS-A = Inheritance.
- HAS-A = Object relationship through composition/aggregation.

**Interview Question:** Inheritance aur Composition mein kya difference hai?

**Answer:** Inheritance IS-A relationship represent karta hai, jabki composition HAS-A relationship represent karta hai. Composition often better flexibility aur loose coupling provide karti hai.

---

# 18. Diamond Problem

Multiple inheritance mein jab ek derived class ko same base class ki multiple copies indirectly milti hain, ambiguity create ho sakti hai.

Example:

```cpp
class A {
public:
    int x = 10;
};

class B : public A {};

class C : public A {};

class D : public B, public C {};
```

Ab:

```cpp
D obj;
// obj.x; // Ambiguous
```

Kyunki D ke through A ki two copies aa rahi hain.

## Solution: Virtual Inheritance

```cpp
class A {
public:
    int x = 10;
};

class B : virtual public A {};

class C : virtual public A {};

class D : public B, public C {};
```

Ab A ka shared virtual base subobject hota hai.

```cpp
int main() {
    D obj;
    cout << obj.x;
}
```

**Output:**

```text
10
```

---

# 19. Object Slicing

Object slicing tab hoti hai jab derived class object ko base class object mein value ke through copy kiya jata hai.

Derived-specific members slice ho jaate hain.

Example:

```cpp
class Base {
public:
    int x = 10;
};

class Derived : public Base {
public:
    int y = 20;
};

int main() {
    Derived d;
    Base b = d;
}
```

Yahan b mein sirf Base portion copy hota hai. Derived ka y member copy nahi hota.

**Important:** Base class reference ya pointer use karne se object slicing avoid ki ja sakti hai.

---

# 20. Shallow Copy vs Deep Copy

## Shallow Copy

Shallow copy mein pointer ka address copy hota hai, actual dynamically allocated data ka separate copy nahi banta.

Isse two objects same memory ko point kar sakte hain.

## Deep Copy

Deep copy mein dynamically allocated data ki separate memory create karke actual data copy kiya jata hai.

Example:

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    int* marks;

    Student(int m) {
        marks = new int(m);
    }

    Student(const Student& obj) {
        marks = new int(*obj.marks);
    }

    ~Student() {
        delete marks;
    }
};

int main() {
    Student s1(90);
    Student s2 = s1;

    *s2.marks = 80;

    cout << *s1.marks << endl;
    cout << *s2.marks;

    return 0;
}
```

**Output:**

```text
90
80
```

Yahan deep copy ke through independent memory create hui hai.

**Important Interview Point:**

Default copy constructor member-wise copy karta hai. Raw pointers ke case mein ye shallow copy create kar sakta hai.

---

# 21. Rule of Three, Five and Zero

## Rule of Three

Agar class manually resource management karti hai aur inmein se kisi ek ko define karne ki need hai, toh generally teeno consider karne chahiye:

1. Destructor
2. Copy Constructor
3. Copy Assignment Operator

## Rule of Five

C++11 mein Rule of Three ke saath two move operations add hue:

4. Move Constructor
5. Move Assignment Operator

## Rule of Zero

Aisi classes design karo jahan resource management standard library types handle karein aur custom destructor/copy/move operations ki zarurat na pade.

Example: `std::string`, `std::vector`, `std::unique_ptr`.

---

# 22. RAII (Resource Acquisition Is Initialization)

RAII ek C++ resource management technique hai.

Ismein resource acquisition object initialization ke saath hota hai aur resource release object destruction ke saath automatically hota hai.

Examples:

- File handling with streams
- `std::vector`
- `std::string`
- Smart pointers
- `std::lock_guard`

Advantages:

- Memory leaks reduce hote hain.
- Automatic cleanup.
- Exception-safe resource management.
- Manual cleanup ki need reduce hoti hai.

---

# 23. Smart Pointers

Smart pointers dynamically allocated memory ko automatically manage karne mein help karte hain.

C++ mein three main smart pointers:

## 23.1 unique_ptr

Ek resource ka exclusive ownership rakhta hai.

```cpp
#include <memory>
using namespace std;

unique_ptr<int> p = make_unique<int>(10);
```

Iska ownership normally copy nahi hota, move ho sakta hai.

## 23.2 shared_ptr

Multiple shared_ptr objects ek resource ki ownership share kar sakte hain.

```cpp
shared_ptr<int> p1 = make_shared<int>(20);
shared_ptr<int> p2 = p1;
```

Reference count track hota hai.

## 23.3 weak_ptr

Shared resource ko observe karta hai bina uski ownership increase kiye.

Ye shared_ptr circular reference problems avoid karne mein help karta hai.

| Smart Pointer | Ownership  |
| ------------- | ---------- |
| unique_ptr    | Exclusive  |
| shared_ptr    | Shared     |
| weak_ptr      | Non-owning |

---

# 24. SOLID Principles

SOLID five important object-oriented design principles hain.

## S – Single Responsibility Principle

Ek class ki ek primary responsibility honi chahiye.

Example: Invoice class invoice data handle kare aur separate EmailService email bheje.

## O – Open/Closed Principle

Software entities extension ke liye open aur modification ke liye closed honi chahiye.

Matlab new functionality add karne ke liye existing tested code ko unnecessarily modify na karna pade.

## L – Liskov Substitution Principle

Derived class objects ko base class objects ki jagah use karne par program ka expected behavior break nahi hona chahiye.

## I – Interface Segregation Principle

Clients ko aise methods implement karne ke liye force nahi karna chahiye jinki unhe need nahi hai.

## D – Dependency Inversion Principle

High-level modules ko low-level modules par directly depend nahi karna chahiye. Dono abstractions par depend karein.

**Quick Revision:**

| Principle | Meaning               |
| --------- | --------------------- |
| S         | Single Responsibility |
| O         | Open/Closed           |
| L         | Liskov Substitution   |
| I         | Interface Segregation |
| D         | Dependency Inversion  |

---

# 25. Coupling and Cohesion

## Coupling

Coupling ka matlab different classes/modules ek doosre par kitne dependent hain.

Low Coupling generally preferred hoti hai.

## Cohesion

Cohesion ka matlab ek class/module ke members kitne closely related hain.

High Cohesion generally preferred hoti hai.

**Ideal Design:**

- Low Coupling
- High Cohesion

---

# 26. Binding

Binding ka matlab function call ko actual function implementation ke saath associate karna.

Two types:

1. Static Binding – Compile time par.
2. Dynamic Binding – Runtime par.

Virtual functions dynamic binding enable karte hain.

---

# 27. Important C++ OOPS Concepts

## 27.1 Const Member Function

Const member function object ke normal data members ko modify nahi kar sakta.

```cpp
class Student {
public:
    int age = 20;

    void show() const {
        cout << age;
    }
};
```

## 27.2 Const Object

Const object ko create karne ke baad uske normal state ko modify nahi kar sakte.

Const object generally const member functions call kar sakta hai.

## 27.3 Inline Function

Inline function compiler ko function call overhead reduce karne ka suggestion deta hai.

Compiler inline request accept ya ignore kar sakta hai.

Class ke andar define kiye gaye member functions implicitly inline hote hain.

## 27.4 Nested Class

Ek class ke andar doosri class define karna nested class kehlata hai.

## 27.5 Local Class

Function ke andar declare ki gayi class local class kehlati hai.

## 27.6 Anonymous Object

Jiska naam nahi hota, use anonymous ya temporary object kaha ja sakta hai.

Example:

```cpp
class Student {};

int main() {
    Student();
}
```

## 27.7 Object Pointer

Object ka address store karne ke liye pointer use hota hai.

```cpp
Student s;
Student* ptr = &s;
```

Access:

```cpp
ptr->show();
```

`->` operator pointer ke through member access karta hai.

---

# 28. Virtual Function vs Pure Virtual Function

| Virtual Function                       | Pure Virtual Function                                   |
| -------------------------------------- | ------------------------------------------------------- |
| `virtual` keyword                      | `virtual` and `= 0`                                     |
| Base implementation ho sakti hai       | Base class mein pure virtual declaration                |
| Class concrete ho sakti hai            | At least one pure virtual function makes class abstract |
| Derived override optional ho sakta hai | Concrete derived class ko implement karna hota hai      |

---

# 29. Important OOPS Interview Differences

## 29.1 Class vs Structure in C++

| Class                       | Structure                                                            |
| --------------------------- | -------------------------------------------------------------------- |
| Default access private      | Default access public                                                |
| Default inheritance private | Default inheritance public                                           |
| Classes support OOPS        | Structures bhi member functions aur OOPS features support karte hain |

## 29.2 Overloading vs Overriding

- Overloading: Same name, different parameter list.
- Overriding: Derived class mein base virtual function ka implementation redefine karna.

## 29.3 Compile-Time vs Runtime Polymorphism

- Compile-time: Function overloading, operator overloading.
- Runtime: Virtual functions and overriding.

## 29.4 Constructor vs Normal Function

- Constructor ka name class ke same hota hai.
- Constructor ka return type nahi hota.
- Constructor object creation ke time automatically call hota hai.
- Normal function manually call hota hai.

## 29.5 Private vs Protected

- Private: Derived class directly access nahi kar sakti.
- Protected: Derived class access kar sakti hai.

## 29.6 Aggregation vs Composition

- Aggregation: Independent lifecycle.
- Composition: Strong ownership/lifecycle relationship.

---

# 30. OOPS Real-World Project Example

## Banking System

OOPS concepts ka use:

**Class:**

- BankAccount
- Customer
- Transaction

**Objects:**

- customer1
- account1
- transaction1

**Encapsulation:**

- Balance ko private rakhna.

**Abstraction:**

- User ko deposit(), withdraw() jaise methods provide karna.

**Inheritance:**

- SavingsAccount aur CurrentAccount ko BankAccount se derive karna.

**Polymorphism:**

- Different account types ke liye calculateInterest() ka different implementation.

**Composition:**

- Account ke andar transaction records manage karna.

Ye example interview mein OOPS ke real-world application explain karne ke liye useful hai.

---

# 31. Important OOPS Interview Questions with Answers

## Basic Questions

**Q1. What is OOPS?**

OOPS is a programming paradigm based on classes and objects.

**Q2. What are the four pillars of OOPS?**

Encapsulation, Abstraction, Inheritance and Polymorphism.

**Q3. What is a class?**

A class is a blueprint used to create objects.

**Q4. What is an object?**

An object is an instance of a class.

**Q5. What is encapsulation?**

Combining data and methods into one unit and controlling access to data.

**Q6. What is abstraction?**

Hiding implementation details and exposing essential functionality.

**Q7. What is inheritance?**

Acquiring accessible properties and behavior of an existing class into a derived class.

**Q8. What is polymorphism?**

One interface or name can represent different behaviors.

## Intermediate Questions

**Q9. What are the types of inheritance?**

Single, Multiple, Multilevel, Hierarchical and Hybrid.

**Q10. What is function overloading?**

Defining multiple functions with the same name but different parameter lists.

**Q11. Can we overload a function by changing only its return type?**

No.

**Q12. What is function overriding?**

Redefining a base class virtual function in a derived class.

**Q13. What is a virtual function?**

A member function that supports runtime polymorphism through dynamic dispatch.

**Q14. What is a pure virtual function?**

A virtual function declared using `= 0`.

**Q15. What is an abstract class?**

A class containing at least one pure virtual function.

**Q16. Can we create an object of an abstract class?**

No, but pointers and references can be created.

**Q17. What is a constructor?**

A special member function used to initialize objects.

**Q18. What is a destructor?**

A special member function used for object cleanup.

**Q19. What is a copy constructor?**

A constructor used to initialize an object from another object of the same class.

**Q20. What is a virtual destructor?**

A destructor declared virtual to ensure proper destruction through base-class pointers.

## Advanced Questions

**Q21. What is the diamond problem?**

Ambiguity caused by multiple inheritance when a derived class receives multiple copies of a common base class.

**Q22. How can we solve the diamond problem?**

Using virtual inheritance.

**Q23. What is the this pointer?**

A special pointer referring to the current object.

**Q24. Can static functions use this pointer?**

No.

**Q25. What is a friend function?**

A non-member function allowed to access private and protected members of a class.

**Q26. What is object slicing?**

Loss of derived-class-specific data when a derived object is copied into a base object by value.

**Q27. What is shallow copy?**

Copying member values, including pointer addresses, without duplicating pointed-to resources.

**Q28. What is deep copy?**

Creating independent copies of dynamically allocated resources.

**Q29. What is dynamic binding?**

Resolving a virtual function call at runtime.

**Q30. What is static binding?**

Resolving a function call at compile time.

**Q31. What is composition?**

A strong whole-part ownership relationship.

**Q32. What is aggregation?**

A weak whole-part relationship where objects can exist independently.

**Q33. What is the Rule of Three?**

Destructor, copy constructor and copy assignment operator.

**Q34. What is the Rule of Five?**

Rule of Three plus move constructor and move assignment operator.

**Q35. What is RAII?**

Resource Acquisition Is Initialization, a C++ resource-management technique.

**Q36. What are smart pointers?**

Objects that manage dynamically allocated resources automatically.

**Q37. What is the difference between unique_ptr and shared_ptr?**

unique_ptr provides exclusive ownership; shared_ptr provides shared ownership.

**Q38. What are SOLID principles?**

Five principles for designing maintainable object-oriented software.

**Q39. What is coupling?**

The degree of dependency between modules.

**Q40. What is cohesion?**

How closely related the responsibilities of a module are.

---

# 32. Tricky Interview Questions

**Q1. Can a constructor be virtual?**

No. Constructors cannot be virtual.

**Q2. Can a destructor be virtual?**

Yes. Virtual destructors are important in polymorphic base classes.

**Q3. Can a constructor be overloaded?**

Yes.

**Q4. Can a destructor be overloaded?**

No.

**Q5. Can static functions be virtual?**

No.

**Q6. Can a private member be inherited?**

The base-class private member remains part of the derived object, but it cannot be accessed directly by derived-class code.

**Q7. Can we overload main() in C++?**

No. The program entry point must have a valid main signature.

**Q8. Can a class have multiple constructors?**

Yes, through constructor overloading.

**Q9. Can we override a non-virtual function?**

A derived class can hide a base function with the same name, but that does not provide virtual runtime overriding.

**Q10. Does C++ support multiple inheritance?**

Yes.

**Q11. Does C++ support interfaces?**

C++ does not have a dedicated interface keyword. Pure abstract classes can serve as interfaces.

**Q12. Can an abstract class have a constructor?**

Yes. Its constructor executes when a derived-class object is created.

**Q13. Can an abstract class have normal functions?**

Yes.

**Q14. Can we create a pointer of an abstract class?**

Yes.

**Q15. What happens if a derived class does not implement a pure virtual function?**

It also remains abstract unless the function is implemented elsewhere in its inheritance hierarchy.

**Q16. Is every class an abstract data type?**

Not necessarily. A class is a language construct; an abstract data type is a conceptual data type defined by its behavior and operations.

**Q17. What is the difference between a pointer and a reference?**

A pointer stores an address and can be reassigned or null. A reference is an alias and must be initialized when declared.

**Q18. Why should we prefer composition over inheritance in some situations?**

Composition often provides more flexibility and reduces tight coupling.

---

# 33. OOPS Quick Revision

| Topic               | One-Line Revision                          |
| ------------------- | ------------------------------------------ |
| OOPS                | Programming using objects and classes      |
| Class               | Blueprint                                  |
| Object              | Instance of class                          |
| Encapsulation       | Data + Methods + Controlled Access         |
| Abstraction         | Hide implementation details                |
| Inheritance         | Reuse through base and derived classes     |
| Polymorphism        | One interface, multiple behaviors          |
| Overloading         | Same name, different parameter lists       |
| Overriding          | Derived implementation of virtual function |
| Constructor         | Initializes object                         |
| Destructor          | Cleans up object                           |
| Copy Constructor    | Initializes from another object            |
| Move Constructor    | Transfers resources                        |
| Virtual Function    | Runtime polymorphism                       |
| Pure Virtual        | `= 0`                                      |
| Abstract Class      | At least one pure virtual function         |
| this Pointer        | Current object pointer                     |
| Static Member       | Shared at class level                      |
| Friend Function     | Access to private/protected members        |
| Composition         | Strong HAS-A relationship                  |
| Aggregation         | Weak HAS-A relationship                    |
| Diamond Problem     | Multiple inheritance ambiguity             |
| Virtual Inheritance | Shares virtual base subobject              |
| Object Slicing      | Derived portion lost in base value copy    |
| Shallow Copy        | Copies pointer address                     |
| Deep Copy           | Copies actual resource                     |
| RAII                | Automatic resource management              |
| SOLID               | Five design principles                     |
| Coupling            | Module dependency                          |
| Cohesion            | Relatedness of module responsibilities     |

---

# 34. Final Interview Preparation Checklist

OOPS complete karne ke baad ye sab topics check karna:

## Fundamentals

- [ ] OOPS definition and advantages
- [ ] Procedural vs OOPS
- [ ] Class and Object
- [ ] State, Behavior and Identity
- [ ] Memory allocation

## Four Pillars

- [ ] Encapsulation
- [ ] Abstraction
- [ ] Inheritance
- [ ] Polymorphism

## Inheritance

- [ ] Five types of inheritance
- [ ] Access modes
- [ ] IS-A vs HAS-A
- [ ] Diamond problem
- [ ] Virtual inheritance

## Polymorphism

- [ ] Function overloading
- [ ] Operator overloading
- [ ] Function overriding
- [ ] Virtual function
- [ ] Pure virtual function
- [ ] Static and dynamic binding

## Object Lifecycle

- [ ] Default constructor
- [ ] Parameterized constructor
- [ ] Copy constructor
- [ ] Move constructor
- [ ] Constructor initialization list
- [ ] Destructor
- [ ] Virtual destructor

## Advanced C++

- [ ] this pointer
- [ ] Static members
- [ ] Friend function and class
- [ ] Const member function
- [ ] Shallow and deep copy
- [ ] Object slicing
- [ ] Rule of Three, Five and Zero
- [ ] RAII
- [ ] Smart pointers

## Software Design

- [ ] Association
- [ ] Aggregation
- [ ] Composition
- [ ] SOLID principles
- [ ] Coupling and Cohesion

---

# FINAL NOTE

OOPS ke liye sirf definitions yaad karna enough nahi hai.

Har concept ke liye:

1. Definition samjho.
2. C++ code khud likho.
3. Output predict karo.
4. Real-world example samjho.
5. Interview question ka answer bina notes dekhe do.

**Goal:** OOPS ke concepts ko explain karna, code mein implement karna aur interview mein confidently answer karna.
