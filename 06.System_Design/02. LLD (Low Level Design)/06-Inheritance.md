# Topic 06: Inheritance (OOP)

## 1. Inheritance kya hota hai?

**Inheritance** OOP (Object-Oriented Programming) ka ek important concept hai.

Iska matlab hai ek class doosri class ke properties (variables) aur methods (functions) ko inherit kar sakti hai.

Simple language mein:

**Inheritance = Ek class ki properties aur methods ko doosri class mein reuse karna.**

Inheritance se code reusability badhti hai aur duplicate code likhne ki zaroorat kam hoti hai.

### Real-Life Example

Maan lo ek family mein:

- Parent ke paas kuch properties hain.
- Child un properties ko inherit kar sakta hai.
- Child apni additional properties bhi rakh sakta hai.

Programming mein bhi isi tarah ek class doosri class ke features inherit kar sakti hai.

---

## 2. Parent Class aur Child Class

Inheritance mein do important terms use hote hain:

### A. Parent Class (Base Class)

Jis class ki properties aur methods inherit ki jaati hain, use Parent Class ya Base Class kehte hain.

### B. Child Class (Derived Class)

Jo class doosri class se properties aur methods inherit karti hai, use Child Class ya Derived Class kehte hain.

Example:

```cpp
class Animal {
public:
    void eat() {
        cout << "Animal is eating";
    }
};

class Dog : public Animal {
};
```

Yahan:

- `Animal` Parent Class hai.
- `Dog` Child Class hai.
- `Dog`, `Animal` ka `eat()` method inherit karti hai.

---

## 3. C++ mein Inheritance ka Syntax

```cpp
class Parent {
    // Parent class members
};

class Child : access_modifier Parent {
    // Child class members
};
```

Example:

```cpp
class Animal {
};

class Dog : public Animal {
};
```

Yahan `public` inheritance mode hai.

---

## 4. Simple Inheritance Example

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
        cout << "Dog is barking" << endl;
    }
};

int main() {
    Dog d1;

    d1.eat();
    d1.bark();

    return 0;
}
```

**Output:**

```text
Animal is eating
Dog is barking
```

### Code kaise work karta hai?

1. `Animal` class mein `eat()` method hai.
2. `Dog` class, `Animal` ko inherit karti hai.
3. `Dog` ka object `d1` create hota hai.
4. `d1.eat()` Parent Class ka inherited method call karta hai.
5. `d1.bark()` Child Class ka apna method call karta hai.

Isse code reuse hota hai.

---

## 5. Types of Inheritance

C++ mein inheritance ke 5 common types hote hain:

1. Single Inheritance
2. Multiple Inheritance
3. Multilevel Inheritance
4. Hierarchical Inheritance
5. Hybrid Inheritance

### A. Single Inheritance

Jab ek Child Class sirf ek Parent Class se inherit karti hai, toh use Single Inheritance kehte hain.

Diagram:

```text
Parent
  |
  v
Child
```

Example:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "Eating";
    }
};

class Dog : public Animal {
};

int main() {
    Dog d1;
    d1.eat();

    return 0;
}
```

Output:

```text
Eating
```

### B. Multiple Inheritance

Jab ek Child Class do ya do se zyada Parent Classes se inherit karti hai, toh use Multiple Inheritance kehte hain.

Diagram:

```text
Parent1    Parent2
    \       /
     \     /
      Child
```

Example:

```cpp
#include <iostream>
using namespace std;

class Father {
public:
    void fatherProperty() {
        cout << "Father property" << endl;
    }
};

class Mother {
public:
    void motherProperty() {
        cout << "Mother property" << endl;
    }
};

class Child : public Father, public Mother {
};

int main() {
    Child c1;

    c1.fatherProperty();
    c1.motherProperty();

    return 0;
}
```

Output:

```text
Father property
Mother property
```

### C. Multilevel Inheritance

Jab ek class doosri class se inherit karti hai aur teesri class us child class se inherit karti hai, toh use Multilevel Inheritance kehte hain.

Diagram:

```text
Grandparent
     |
     v
   Parent
     |
     v
    Child
```

Example:

```cpp
#include <iostream>
using namespace std;

class Grandparent {
public:
    void property() {
        cout << "Grandparent property" << endl;
    }
};

class Parent : public Grandparent {
};

class Child : public Parent {
};

int main() {
    Child c1;

    c1.property();

    return 0;
}
```

Output:

```text
Grandparent property
```

Yahan `Child` indirectly `Grandparent` ka method bhi access kar sakti hai.

### D. Hierarchical Inheritance

Jab multiple Child Classes ek hi Parent Class se inherit karti hain, toh use Hierarchical Inheritance kehte hain.

Diagram:

```text
       Parent
       /    \
      v      v
   Child1  Child2
```

Example:

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
};

class Cat : public Animal {
};

int main() {
    Dog d1;
    Cat c1;

    d1.eat();
    c1.eat();

    return 0;
}
```

Output:

```text
Animal is eating
Animal is eating
```

### E. Hybrid Inheritance

Jab ek program mein do ya do se zyada inheritance types combine hote hain, toh use Hybrid Inheritance kehte hain.

Example diagram:

```text
       A
      / \
     B   C
      \ /
       D
```

Is structure mein Diamond Problem aa sakti hai.

C++ mein virtual inheritance ka use karke Diamond Problem ko solve kiya ja sakta hai.

---

## 6. Access Modes in Inheritance

C++ mein inheritance ke 3 access modes hote hain:

1. Public Inheritance
2. Protected Inheritance
3. Private Inheritance

Ye decide karte hain ki Parent Class ke inherited members Child Class mein kis access level par available honge.

### Access Mode Table

| Parent Member | Public Inheritance       | Protected Inheritance    | Private Inheritance      |
| ------------- | ------------------------ | ------------------------ | ------------------------ |
| Public        | Public                   | Protected                | Private                  |
| Protected     | Protected                | Protected                | Private                  |
| Private       | Directly accessible nahi | Directly accessible nahi | Directly accessible nahi |

**Important:** Parent class ke private members derived class mein exist karte hain, lekin derived class unhe directly access nahi kar sakti. Unhe parent ke accessible public/protected methods ke through use kiya ja sakta hai.

### Example: Public Inheritance

```cpp
class Parent {
public:
    int x = 10;
};

class Child : public Parent {
};
```

Yahan `x` Child class mein public rahega.

### Example: Protected Inheritance

```cpp
class Parent {
public:
    int x = 10;
};

class Child : protected Parent {
};
```

Yahan Parent ka public member `x`, Child mein protected ho jayega.

### Example: Private Inheritance

```cpp
class Parent {
public:
    int x = 10;
};

class Child : private Parent {
};
```

Yahan Parent ka public member `x`, Child mein private ho jayega.

---

## 7. Constructor in Inheritance

Jab Child Class ka object create hota hai, toh pehle Parent Class ka constructor execute hota hai, uske baad Child Class ka constructor.

Example:

```cpp
#include <iostream>
using namespace std;

class Parent {
public:
    Parent() {
        cout << "Parent Constructor" << endl;
    }
};

class Child : public Parent {
public:
    Child() {
        cout << "Child Constructor" << endl;
    }
};

int main() {
    Child c1;

    return 0;
}
```

Output:

```text
Parent Constructor
Child Constructor
```

### Parameterized Parent Constructor

Agar Parent Class mein parameterized constructor hai, toh Child Class ke constructor se initializer list ke through usko call kar sakte hain.

```cpp
#include <iostream>
using namespace std;

class Parent {
public:
    Parent(int x) {
        cout << "Parent value: " << x << endl;
    }
};

class Child : public Parent {
public:
    Child() : Parent(100) {
        cout << "Child Constructor" << endl;
    }
};

int main() {
    Child c1;

    return 0;
}
```

Output:

```text
Parent value: 100
Child Constructor
```

---

## 8. Function Overriding in Inheritance

Jab Child Class Parent Class ke function ko apni implementation ke saath redefine karti hai, toh use Function Overriding kehte hain.

Runtime polymorphism ke liye C++ mein base class function ko `virtual` declare karna important hota hai.

Example:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal makes sound" << endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "Dog barks" << endl;
    }
};

int main() {
    Dog d1;

    d1.sound();

    return 0;
}
```

Output:

```text
Dog barks
```

Yahan:

- `Animal` Parent Class hai.
- `Dog` Child Class hai.
- `Dog` ne `sound()` override kiya hai.
- `override` compiler ko batata hai ki ye base class ke virtual function ko override karne ke liye hai.

---

## 9. Diamond Problem in C++

Diamond Problem Multiple Inheritance ke ek special case mein hoti hai.

Diagram:

```text
       A
      / \
     B   C
      \ /
       D
```

Yahan:

- B, A se inherit karta hai.
- C, A se inherit karta hai.
- D, B aur C dono se inherit karta hai.

Isse D ko A ki do copies mil sakti hain.

Example:

```cpp
#include <iostream>
using namespace std;

class A {
public:
    int x = 10;
};

class B : public A {
};

class C : public A {
};

class D : public B, public C {
};

int main() {
    D obj;

    // cout << obj.x; // Error: ambiguous

    cout << obj.B::x << endl;
    cout << obj.C::x << endl;

    return 0;
}
```

Output:

```text
10
10
```

`obj.x` ambiguous hai, kyunki compiler ko samajh nahi aata ki B ke through inherited `x` use kare ya C ke through.

### Virtual Inheritance se Solution

```cpp
#include <iostream>
using namespace std;

class A {
public:
    int x = 10;
};

class B : virtual public A {
};

class C : virtual public A {
};

class D : public B, public C {
};

int main() {
    D obj;

    cout << obj.x;

    return 0;
}
```

Output:

```text
10
```

Virtual inheritance ensure karta hai ki D ko shared base class A ki ek common subobject mile.

---

## 10. Inheritance in JavaScript

JavaScript mein `extends` keyword se ek class doosri class ko inherit kar sakti hai.

Example:

```javascript
class Animal {
  eat() {
    console.log("Animal is eating");
  }
}

class Dog extends Animal {
  bark() {
    console.log("Dog is barking");
  }
}

const dog = new Dog();

dog.eat();
dog.bark();
```

Output:

```text
Animal is eating
Dog is barking
```

Yahan:

- `Animal` parent class hai.
- `Dog` child class hai.
- `extends` inheritance ke liye use hota hai.

### Super Keyword

JavaScript mein `super` keyword parent class ke constructor ya methods ko call karne ke liye use hota hai.

Example:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  eat() {
    console.log(`${this.name} is eating`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);

    this.breed = breed;
  }

  showDetails() {
    console.log(this.name);
    console.log(this.breed);
  }
}

const dog = new Dog("Tommy", "Labrador");

dog.eat();
dog.showDetails();
```

Output:

```text
Tommy is eating
Tommy
Labrador
```

**Important:**

- Derived class ke constructor mein `this` use karne se pehle `super()` call karna zaroori hota hai.
- `super()` parent constructor call karta hai.
- `super.methodName()` parent class ka method call kar sakta hai.

---

## 11. Inheritance in MERN Stack

MERN Stack mein JavaScript inheritance ka use backend aur frontend dono mein ho sakta hai.

### A. Backend – Custom Error Classes

Node.js backend mein custom error classes banane ke liye inheritance useful hai.

Example:

```javascript
class AppError extends Error {
  constructor(message, statusCode) {
    super(message);

    this.statusCode = statusCode;
  }
}

class NotFoundError extends AppError {
  constructor(message) {
    super(message, 404);
  }
}

const error = new NotFoundError("User not found");

console.log(error.message);
console.log(error.statusCode);
```

Output:

```text
User not found
404
```

Yahan:

- `Error` built-in parent class hai.
- `AppError` usse inherit karti hai.
- `NotFoundError`, `AppError` se inherit karti hai.

### B. React Components

React mein class components ko inherit karne ke liye `extends React.Component` use hota tha aur ab bhi supported hai.

Example:

```jsx
import React from "react";

class Welcome extends React.Component {
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}
```

Modern React applications mein generally functional components aur Hooks prefer kiye jaate hain.

**Important:** React mein component reuse ke liye composition ko aksar inheritance se prefer kiya jata hai.

---

## 12. Advantages of Inheritance

1. **Code Reusability:** Parent class ka code reuse kar sakte hain.
2. **Less Code Duplication:** Same code baar-baar likhne ki zaroorat kam hoti hai.
3. **Easy Maintenance:** Common behavior parent class mein manage kar sakte hain.
4. **Extensibility:** Child class additional features add kar sakti hai.
5. **Polymorphism:** Runtime polymorphism implement karne mein help karta hai.

## 13. Disadvantages of Inheritance

1. Parent aur Child classes ke beech dependency badh sakti hai.
2. Deep inheritance hierarchy samajhna difficult ho sakta hai.
3. Parent class mein changes child classes ko affect kar sakte hain.
4. Galat inheritance design code ko complex bana sakta hai.
5. Multiple inheritance mein ambiguity aa sakti hai.

**Best Practice:** Inheritance tab use karo jab genuinely `IS-A` relationship ho.

Example:

- Dog IS-A Animal.
- Car IS-A Vehicle.

Sirf code reuse ke liye har jagah inheritance use mat karo. Kai situations mein Composition better hoti hai.

---

## 14. Inheritance vs Composition

| Inheritance                                | Composition                                       |
| ------------------------------------------ | ------------------------------------------------- |
| IS-A relationship                          | HAS-A relationship                                |
| Ek class doosri class se inherit karti hai | Ek class doosri class ka object contain karti hai |
| Parent ke behavior ko inherit karte hain   | Doosre object ki functionality use karte hain     |
| Example: Dog IS-A Animal                   | Car HAS-A Engine                                  |

### Example of Composition

```cpp
#include <iostream>
using namespace std;

class Engine {
public:
    void start() {
        cout << "Engine started";
    }
};

class Car {
private:
    Engine engine;

public:
    void startCar() {
        engine.start();
    }
};

int main() {
    Car car;

    car.startCar();

    return 0;
}
```

Output:

```text
Engine started
```

Yahan Car ke paas Engine hai. Isliye ye Composition ka example hai.

---

## 15. Common Mistakes

1. Parent aur Child Class ko confuse karna.
2. `extends` aur `super` ka galat use karna.
3. C++ mein private parent members ko directly access karne ki koshish karna.
4. Inheritance access modes ko confuse karna.
5. JavaScript derived constructor mein `super()` call karna bhool jana.
6. Har code reuse situation mein inheritance use karna.
7. Diamond Problem ko ignore karna.
8. C++ mein runtime overriding ke liye base method ko `virtual` banana bhool jana.

---

## 16. Interview Questions and Answers

### Q1. What is Inheritance?

Inheritance is an OOP concept in which one class acquires accessible properties and methods of another class.

### Q2. What is a Parent Class?

The class whose members are inherited is called the Parent or Base Class.

### Q3. What is a Child Class?

The class that inherits from another class is called the Child or Derived Class.

### Q4. What are the types of Inheritance in C++?

Single, Multiple, Multilevel, Hierarchical and Hybrid Inheritance.

### Q5. What is Multiple Inheritance?

When one child class inherits from two or more parent classes, it is called Multiple Inheritance.

### Q6. What is Multilevel Inheritance?

When a class inherits from another derived class, it is called Multilevel Inheritance.

### Q7. What is the Diamond Problem?

It is an ambiguity problem that can occur when a class inherits from two classes that share the same base class.

### Q8. How can we solve the Diamond Problem in C++?

We can use Virtual Inheritance.

### Q9. What is the use of `super` in JavaScript?

It is used to call the parent class constructor or parent class methods.

### Q10. What is the difference between Inheritance and Composition?

Inheritance represents an IS-A relationship, while Composition represents a HAS-A relationship.

---

## 17. Practice Tasks

### Task 1: Animal Inheritance

- Parent class: `Animal`
- Method: `eat()`
- Child class: `Dog`
- Method: `bark()`
- Dono methods call karo.

### Task 2: Multilevel Inheritance

- Class A mein `showA()` banao.
- Class B, A se inherit kare.
- Class C, B se inherit kare.
- C ke object se `showA()` call karo.

### Task 3: Multiple Inheritance

- Class `Father` mein `fatherProperty()` banao.
- Class `Mother` mein `motherProperty()` banao.
- Class `Child` dono se inherit kare.
- Child object se dono methods call karo.

### Task 4: Function Overriding

- Parent class `Animal` banao.
- Virtual method `sound()` banao.
- Child classes `Dog` aur `Cat` banao.
- Dono apna sound implement karein.

### Task 5: JavaScript Inheritance

- Parent class `User` banao.
- Constructor mein `name` set karo.
- Child class `Admin` banao.
- `extends` aur `super()` use karo.
- Admin ka name print karo.

---

## 18. Quick Revision

| Concept      | Meaning                                   |
| ------------ | ----------------------------------------- |
| Inheritance  | Existing class ke features inherit karna  |
| Parent Class | Base Class                                |
| Child Class  | Derived Class                             |
| Single       | One parent, one child                     |
| Multiple     | Multiple parents, one child               |
| Multilevel   | Grandparent → Parent → Child              |
| Hierarchical | One parent, multiple children             |
| Hybrid       | Multiple inheritance types ka combination |
| `extends`    | JavaScript inheritance keyword            |
| `super()`    | Parent constructor call                   |
| `virtual`    | C++ runtime polymorphism support          |
| Composition  | HAS-A relationship                        |
| Inheritance  | IS-A relationship                         |

### One-Line Revision

**Inheritance ka purpose existing class ke accessible properties aur methods ko reuse karke new class banana hai.**

---

## 19. Completion Checklist

- [ ] Inheritance ka meaning samajh liya.
- [ ] Parent aur Child class samajh li.
- [ ] C++ inheritance syntax samajh liya.
- [ ] Five types of inheritance samajh liye.
- [ ] Access modes samajh liye.
- [ ] Constructor execution order samajh liya.
- [ ] Function overriding samajh li.
- [ ] Diamond Problem aur Virtual Inheritance samajh liya.
- [ ] JavaScript `extends` aur `super()` samajh liya.
- [ ] MERN examples samajh liye.
- [ ] Inheritance vs Composition samajh liya.
- [ ] Practice tasks complete kar liye.

**Topic 06 – Inheritance Complete.**
