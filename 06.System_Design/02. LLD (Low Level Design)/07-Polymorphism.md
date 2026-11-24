# Topic 07: Polymorphism (OOP)

## 1. Polymorphism kya hota hai?

**Polymorphism** OOP (Object-Oriented Programming) ka ek important concept hai.

Polymorphism ka meaning hota hai:

- Poly = Many (Bahut saare)
- Morphism = Forms (Roop)

Simple language mein:

**Polymorphism = One Interface, Many Forms.**

Matlab ek hi function, method ya interface different situations mein different behavior perform kar sakta hai.

### Real-Life Example

Maan lo tumhare paas ek person hai.

Wahi person:

- Ghar par son hota hai.
- Office mein employee hota hai.
- School mein student ho sakta hai.

Person ek hi hai, lekin situation ke according role change ho raha hai.

Programming mein bhi ek hi function ya interface different behavior show kar sakta hai.

---

## 2. Polymorphism ke Types

C++ mein Polymorphism ke 2 main types hote hain:

1. Compile-Time Polymorphism
2. Runtime Polymorphism

Diagram:

```text
              Polymorphism
                    |
          ---------------------
          |                   |
          v                   v
   Compile-Time           Runtime
   Polymorphism         Polymorphism
          |                   |
    -------------        -------------
    |           |        |           |
 Function   Operator   Function   Virtual
Overloading Overloading Overriding Functions
```

---

## 3. Compile-Time Polymorphism

Jab compiler compilation ke time decide karta hai ki kaunsa function ya operator execute hoga, toh use Compile-Time Polymorphism kehte hain.

C++ mein iske common examples hain:

1. Function Overloading
2. Operator Overloading

### A. Function Overloading

Jab ek hi class mein same name ke multiple functions hote hain, lekin unke parameters different hote hain, toh use Function Overloading kehte hain.

Parameters mein difference ho sakta hai:

- Number of parameters.
- Parameter types.
- Parameters ka order.

**Note:** Sirf return type change karne se function overloading nahi hoti.

### Example 1: Different Number of Parameters

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
    Calculator calc;

    cout << calc.add(10, 20) << endl;
    cout << calc.add(10, 20, 30) << endl;

    return 0;
}
```

**Output:**

```text
30
60
```

### Explanation

- `add(10, 20)` mein 2 arguments hain, isliye first function call hota hai.
- `add(10, 20, 30)` mein 3 arguments hain, isliye second function call hota hai.

Same function name `add()`, lekin different behavior.

### Example 2: Different Data Types

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
};

int main() {
    Calculator calc;

    cout << calc.add(10, 20) << endl;
    cout << calc.add(10.5, 20.5) << endl;

    return 0;
}
```

**Output:**

```text
30
31
```

Yahan compiler arguments ke data types ke according function select karta hai.

---

## 4. Operator Overloading

C++ mein hum operators ko user-defined classes ke liye special behavior de sakte hain.

Is process ko Operator Overloading kehte hain.

Example:

Hum `+` operator ko two objects add karne ke liye overload kar sakte hain.

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

### Explanation

- `n1` ki value 10 hai.
- `n2` ki value 20 hai.
- `n1 + n2` par overloaded `operator+()` call hota hai.
- Result ka new object `n3` create hota hai.
- `n3.value` 30 print karta hai.

**Important:** C++ mein kuch operators overload nahi kiye ja sakte, jaise `::`, `.`, `.*`, `?:` aur `sizeof`.

---

## 5. Runtime Polymorphism

Jab program execute hote waqt decide hota hai ki kaunsa function call hoga, toh use Runtime Polymorphism kehte hain.

C++ mein Runtime Polymorphism achieve karne ke liye:

- Inheritance
- Function Overriding
- Virtual Functions

ka use kiya jata hai.

### Function Overriding

Jab Child Class Parent Class ke inherited function ko apni implementation ke saath redefine karti hai, toh use Function Overriding kehte hain.

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

**Output:**

```text
Dog barks
```

Yahan Dog class ne Parent class ke `sound()` method ko override kiya hai.

---

## 6. Virtual Function kya hota hai?

C++ mein `virtual` keyword kisi member function ko virtual banata hai.

Jab hum base class ke pointer ya reference ke through derived class ka overridden function call karte hain, toh virtual function runtime par correct function select karne mein help karta hai.

Example:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {
        cout << "Animal sound" << endl;
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

    Animal* ptr = &d1;

    ptr->sound();

    return 0;
}
```

**Output:**

```text
Dog barks
```

### Ye kaise work karta hai?

1. `Animal` Parent Class hai.
2. `Dog` Child Class hai.
3. `Dog` ne `sound()` override kiya hai.
4. `Animal* ptr` base class ka pointer hai.
5. Pointer `Dog` object ko point kar raha hai.
6. `sound()` virtual hai, isliye runtime par Dog ka function call hota hai.

Is behavior ko Dynamic Dispatch kehte hain.

---

## 7. Virtual Function ke bina kya hota hai?

Agar base class ka function virtual nahi hai, toh base class pointer ke through function call karne par base class ka function select hota hai.

Example:

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void sound() {
        cout << "Animal sound" << endl;
    }
};

class Dog : public Animal {
public:
    void sound() {
        cout << "Dog barks" << endl;
    }
};

int main() {
    Dog d1;

    Animal* ptr = &d1;

    ptr->sound();

    return 0;
}
```

**Output:**

```text
Animal sound
```

Yahan base class ka function call hua kyunki `sound()` virtual nahi tha.

---

## 8. Compile-Time vs Runtime Polymorphism

| Compile-Time                        | Runtime                                    |
| ----------------------------------- | ------------------------------------------ |
| Compilation ke time selection       | Execution ke time selection                |
| Static binding                      | Dynamic binding                            |
| Function overloading                | Function overriding with virtual functions |
| Operator overloading                | Virtual function dispatch                  |
| Generally inheritance required nahi | Inheritance commonly use hoti hai          |

**Note:** Function overriding ka naam aur behavior runtime polymorphism se associated hai, lekin C++ mein actual dynamic dispatch ke liye virtual function zaroori hota hai.

---

## 9. Polymorphism in JavaScript

JavaScript mein bhi Polymorphism implement kar sakte hain.

### A. Method Overriding

```javascript
class Animal {
  sound() {
    console.log("Animal makes sound");
  }
}

class Dog extends Animal {
  sound() {
    console.log("Dog barks");
  }
}

class Cat extends Animal {
  sound() {
    console.log("Cat meows");
  }
}

const dog = new Dog();
const cat = new Cat();

dog.sound();
cat.sound();
```

**Output:**

```text
Dog barks
Cat meows
```

Yahan:

- `Animal` parent class hai.
- `Dog` aur `Cat` child classes hain.
- Dono ne `sound()` method override kiya hai.
- Same method name different behavior perform kar raha hai.

### B. Duck Typing

JavaScript dynamically typed language hai.

Isliye different objects same method provide kar sakte hain, chahe unka common parent class hona zaroori na ho.

Example:

```javascript
const dog = {
  sound() {
    console.log("Dog barks");
  },
};

const cat = {
  sound() {
    console.log("Cat meows");
  },
};

function makeSound(animal) {
  animal.sound();
}

makeSound(dog);
makeSound(cat);
```

**Output:**

```text
Dog barks
Cat meows
```

Yahan function ko sirf itna chahiye ki object mein `sound()` method available ho.

Is approach ko Duck Typing kehte hain.

---

## 10. Polymorphism in MERN Stack

MERN applications mein Polymorphism ka practical use ho sakta hai.

### A. Backend – Payment System

Maan lo application mein different payment methods hain:

- UPI
- Card
- Wallet

Sabke paas `pay()` method ho sakta hai.

```javascript
class UPI {
  pay(amount) {
    console.log(`UPI payment: ${amount}`);
  }
}

class Card {
  pay(amount) {
    console.log(`Card payment: ${amount}`);
  }
}

function processPayment(paymentMethod, amount) {
  paymentMethod.pay(amount);
}

processPayment(new UPI(), 500);
processPayment(new Card(), 1000);
```

**Output:**

```text
UPI payment: 500
Card payment: 1000
```

Same `processPayment()` function different payment objects ke saath work kar raha hai.

### B. React Components

React mein same component different props ke according different UI show kar sakta hai.

Example:

```jsx
function Button({ type }) {
  if (type === "primary") {
    return <button>Submit</button>;
  }

  if (type === "danger") {
    return <button>Delete</button>;
  }

  return <button>Click</button>;
}
```

Use:

```jsx
<Button type="primary" />
<Button type="danger" />
```

Same component different props ke according different output deta hai.

**Note:** Ye polymorphic behavior ka practical example hai; React props-based rendering ko C++ ke virtual function mechanism ke exactly same nahi samajhna chahiye.

---

## 11. Advantages of Polymorphism

1. **Flexibility:** Same interface ke through different implementations use kar sakte hain.
2. **Code Reusability:** Common code ko reuse kar sakte hain.
3. **Maintainability:** New implementations add karna easy ho sakta hai.
4. **Extensibility:** Existing code ko har baar modify kiye bina new behavior add kar sakte hain.
5. **Loose Coupling:** Interface-based design se classes ki direct dependency kam ho sakti hai.

## 12. Disadvantages of Polymorphism

1. Code beginners ke liye difficult ho sakta hai.
2. Runtime polymorphism mein dynamic dispatch ka extra overhead ho sakta hai.
3. Galat inheritance design complexity badha sakta hai.
4. Debugging kabhi-kabhi difficult ho sakti hai.

---

## 13. Common Mistakes

1. Function overloading aur overriding ko same samajhna.
2. Sirf return type change karke overloading karne ki koshish karna.
3. C++ runtime polymorphism mein `virtual` bhool jana.
4. `override` ka galat use karna.
5. Base class pointer aur derived object ka relation samajh na paana.
6. Compile-time aur runtime polymorphism confuse karna.
7. JavaScript Duck Typing ko inheritance samajhna.

---

## 14. Interview Questions and Answers

### Q1. What is Polymorphism?

Polymorphism is an OOP concept in which the same interface or function can represent different behaviors.

### Q2. What are the types of Polymorphism in C++?

Compile-Time Polymorphism and Runtime Polymorphism.

### Q3. What is Function Overloading?

Defining multiple functions with the same name but different parameter lists.

### Q4. Can we overload functions by changing only the return type?

No. The parameter list must be different.

### Q5. What is Function Overriding?

When a derived class provides its own implementation of an inherited virtual function.

### Q6. What is a Virtual Function?

A member function declared with the `virtual` keyword in a base class, which supports runtime dynamic dispatch.

### Q7. What is Dynamic Binding?

Selecting the appropriate overridden function at runtime.

### Q8. What is Operator Overloading?

Giving a user-defined meaning to an operator for class objects.

### Q9. What is Duck Typing?

A programming approach in which an object's suitability depends on the methods or properties it provides rather than its declared type.

### Q10. What is the difference between Overloading and Overriding?

Overloading uses the same function name with different parameter lists, while overriding provides a derived class implementation of an inherited virtual function.

---

## 15. Practice Tasks

### Task 1: Function Overloading

Ek `Calculator` class banao:

- `add(int, int)`
- `add(int, int, int)`
- `add(double, double)`

Teeno functions call karo.

### Task 2: Function Overriding

- Parent class `Animal` banao.
- Virtual method `sound()` banao.
- Child classes `Dog` aur `Cat` banao.
- Dono apna sound print karein.

### Task 3: Runtime Polymorphism

- Parent class `Shape` banao.
- Virtual method `area()` banao.
- Child classes `Circle` aur `Rectangle` banao.
- Base class pointer se dono objects ke area calculate karo.

### Task 4: Operator Overloading

Ek `Number` class banao:

- Private integer variable.
- Constructor.
- `+` operator overload karo.
- Do objects add karke result print karo.

### Task 5: JavaScript Polymorphism

- `EmailNotification` aur `SMSNotification` objects banao.
- Dono mein `send()` method rakho.
- Ek common function se dono ka `send()` call karo.

---

## 16. Quick Revision

| Concept              | Meaning                                          |
| -------------------- | ------------------------------------------------ |
| Polymorphism         | One Interface, Many Forms                        |
| Compile-Time         | Compiler selection                               |
| Runtime              | Execution-time dynamic dispatch                  |
| Function Overloading | Same name, different parameters                  |
| Operator Overloading | Operators ko custom behavior dena                |
| Function Overriding  | Child class mein inherited method redefine karna |
| Virtual Function     | Runtime dispatch support                         |
| Dynamic Binding      | Runtime par function selection                   |
| Duck Typing          | Required methods ke basis par object use karna   |

### One-Line Revision

**Polymorphism ka purpose same interface ya function ke through different behaviors perform karna hai.**

---

## 17. Completion Checklist

- [ ] Polymorphism ka meaning samajh liya.
- [ ] Compile-Time Polymorphism samajh liya.
- [ ] Runtime Polymorphism samajh liya.
- [ ] Function Overloading samajh li.
- [ ] Operator Overloading samajh li.
- [ ] Function Overriding samajh li.
- [ ] Virtual Functions samajh liye.
- [ ] Dynamic Binding samajh li.
- [ ] JavaScript Duck Typing samajh li.
- [ ] MERN examples samajh liye.
- [ ] Interview questions revise kar liye.
- [ ] Practice tasks complete kar liye.

**Topic 07 – Polymorphism Complete.**
