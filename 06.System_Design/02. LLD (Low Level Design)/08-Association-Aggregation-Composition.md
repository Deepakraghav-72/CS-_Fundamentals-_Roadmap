# Association, Aggregation & Composition

## 1. Introduction

OOP (Object-Oriented Programming) mein objects ek-dusre ke saath relationship bana sakte hain.

Example:

- Teacher students ko teach karta hai.
- Department mein teachers hote hain.
- House mein rooms hote hain.

In relationships ko mainly 3 categories mein samjha jata hai:

1. Association
2. Aggregation
3. Composition

Ye teeno objects ke beech relationship ko represent karte hain.

---

## 2. Association

### Definition

Association ka matlab hai ki do independent objects ek-dusre ke saath connected hain ya ek-dusre ka use karte hain.

**Simple language:** Ek object doosre object ke saath kaam karta hai, lekin dono independently exist kar sakte hain.

### Real-life example

Teacher aur Student:

- Teacher student ko padhata hai.
- Student teacher se padhta hai.
- Teacher ke exist karne ke liye student ka hona zaroori nahi.
- Student ke exist karne ke liye teacher ka hona zaroori nahi.

Dono independently exist kar sakte hain.

### JavaScript example

```javascript
class Student {
  constructor(name) {
    this.name = name;
  }
}

class Teacher {
  constructor(name) {
    this.name = name;
  }

  teach(student) {
    console.log(`${this.name} is teaching ${student.name}`);
  }
}

const student1 = new Student("Rahul");
const teacher1 = new Teacher("Amit");

teacher1.teach(student1);
```

**Output:**

```text
Amit is teaching Rahul
```

### Code kaise work kar raha hai?

1. `Student` class banayi.
2. `Teacher` class banayi.
3. Dono ke independent objects create kiye.
4. `teach()` method mein student object pass kiya.
5. Teacher ne student object ka use kiya.

Yahan Teacher aur Student ka Association hai.

### Association ke types

**1. One-to-One**

Ek object ka relationship doosre ek object ke saath.

Example: Person aur Passport (simple conceptual example).

**2. One-to-Many**

Ek object ka relationship multiple objects ke saath.

Example: Ek teacher multiple students ko padha sakta hai.

**3. Many-to-Many**

Multiple objects ka relationship multiple objects ke saath.

Example: Students aur Courses. Ek student multiple courses le sakta hai aur ek course mein multiple students ho sakte hain.

---

## 3. Aggregation

### Definition

Aggregation ek special type ka Association hai.

Ismein ek object doosre objects ko apne andar logically contain karta hai, lekin contained objects independently exist kar sakte hain.

**Simple language:** Ek object ke paas doosre objects hote hain, lekin un objects ki life us par depend nahi karti.

### Real-life example

Department aur Teacher:

- Ek college mein multiple departments ho sakte hain.
- Ek department mein multiple teachers ho sakte hain.
- Agar department close ho jaye, toh teacher ka existence khatam nahi hota.
- Teacher kisi doosre department mein bhi kaam kar sakta hai.

Isliye ye Aggregation ka example hai.

### JavaScript example

```javascript
class Teacher {
  constructor(name) {
    this.name = name;
  }
}

class Department {
  constructor(name, teachers) {
    this.name = name;
    this.teachers = teachers;
  }

  showTeachers() {
    this.teachers.forEach((teacher) => {
      console.log(teacher.name);
    });
  }
}

const teacher1 = new Teacher("Amit");
const teacher2 = new Teacher("Rahul");

const department1 = new Department("Computer Science", [teacher1, teacher2]);

department1.showTeachers();
```

**Output:**

```text
Amit
Rahul
```

### Code kaise work kar raha hai?

1. Teacher class banayi.
2. Department class banayi.
3. Teacher ke objects separately create kiye.
4. Un objects ko Department ke constructor mein pass kiya.
5. Department ne teachers ke references store kar liye.

Important point:

Teachers department ke bahar bhi exist kar sakte hain.

Yahi Aggregation hai.

### Aggregation ki important baatein

- Ye HAS-A relationship hai.
- Whole object aur part objects independently exist kar sakte hain.
- Part object ka ownership necessarily whole ke paas nahi hota.
- Part object doosre objects ke saath bhi share ho sakta hai.

---

## 4. Composition

### Definition

Composition bhi Association ka ek strong form hai.

Ismein ek object doosre objects ko strongly own karta hai. Part object ka lifecycle whole object ke ownership se connected hota hai.

**Simple language:** Ek object apne parts ka owner hota hai aur un parts ko apne andar manage karta hai.

### Real-life example

House aur Room:

- House ke andar rooms hote hain.
- Hum is design mein rooms ko house ke parts ke roop mein create karte hain.
- House object destroy hone par uske owned room objects bhi destroy ho jaate hain.

Ye Composition ka example hai.

### JavaScript example

```javascript
class Room {
  constructor(name) {
    this.name = name;
  }

  showRoom() {
    console.log(`${this.name} room`);
  }
}

class House {
  constructor() {
    this.rooms = [
      new Room("Bedroom"),
      new Room("Kitchen"),
      new Room("Bathroom"),
    ];
  }

  showRooms() {
    this.rooms.forEach((room) => {
      room.showRoom();
    });
  }
}

const house1 = new House();

house1.showRooms();
```

**Output:**

```text
Bedroom room
Kitchen room
Bathroom room
```

### Code kaise work kar raha hai?

1. Room class banayi.
2. House class banayi.
3. House ke constructor ke andar Room objects create kiye.
4. House ne un objects ko apne andar manage kiya.
5. Rooms ko separately constructor ke bahar se pass nahi kiya.

Yahan House aur Room ke beech Composition relationship model ki gayi hai.

**Important JavaScript point:**

JavaScript mein garbage collection hoti hai. Sirf House variable delete karne se rooms turant destroy honge, ye guarantee nahi hai. Agar kisi doosre reference se room accessible hai, toh woh exist kar sakta hai.

Composition yahan ownership/design relationship ko represent karta hai. JavaScript mein object destruction ka exact time garbage collector decide karta hai.

---

## 5. Association vs Aggregation vs Composition

| Feature              | Association          | Aggregation                 | Composition                             |
| -------------------- | -------------------- | --------------------------- | --------------------------------------- |
| Meaning              | General relationship | Weak HAS-A                  | Strong HAS-A                            |
| Ownership            | Necessary nahi       | Weak/no exclusive ownership | Strong ownership                        |
| Lifetime dependency  | Nahi                 | Nahi                        | Owned part ka lifecycle whole se linked |
| Objects independent? | Yes                  | Yes                         | Designed ownership mein usually no      |
| Example              | Teacher-Student      | Department-Teacher          | House-Room                              |

### Easy trick to remember

- **Association:** Objects connected hain.
- **Aggregation:** Ek object ke paas doosre objects hain, par dono independent hain.
- **Composition:** Ek object apne parts ka owner hai.

---

## 6. UML Notation

UML ka full form hai:

**Unified Modeling Language**

UML diagrams ka use software system ke structure aur relationships ko visually represent karne ke liye hota hai.

Association, Aggregation aur Composition ke UML symbols alag hote hain.

### 1. Association

Do classes ke beech simple straight line.

```text
Teacher ---------------- Student
```

### 2. Aggregation

Hollow diamond (khali diamond) whole side par hota hai.

```text
Department ◇---------- Teacher
```

Yahan Department whole hai aur Teacher part hai.

### 3. Composition

Filled diamond (bhara hua diamond) whole side par hota hai.

```text
House ◆---------------- Room
```

Yahan House whole hai aur Room part hai.

**Yaad rakho:** Diamond hamesha whole/owner side par hota hai.

### Multiplicity

Multiplicity batati hai ki ek object ka kitne objects ke saath relationship ho sakta hai.

| Symbol | Meaning          |
| ------ | ---------------- |
| `1`    | Exactly one      |
| `0..1` | Zero ya one      |
| `0..*` | Zero ya multiple |
| `1..*` | At least one     |

Example:

```text
Department 1 ◇-------- 0..* Teacher
```

Meaning:

- Ek Department mein zero ya multiple Teachers ho sakte hain.
- Har Teacher ka is model mein ek Department se relationship hai.

---

## 7. Association vs Inheritance

Ye dono concepts alag hain.

### Inheritance

Inheritance ka matlab hai IS-A relationship.

Example:

```text
Car IS-A Vehicle
Dog IS-A Animal
```

### Association

Association ka matlab hai objects ke beech relationship ya HAS-A/uses relationship.

Example:

```text
Car HAS-A Engine
Teacher teaches Student
```

| Inheritance                | Association                     |
| -------------------------- | ------------------------------- |
| IS-A relationship          | Objects ke beech relationship   |
| Parent-child classes       | Independent classes connected   |
| `extends` use ho sakta hai | Object references use hote hain |

**Important:** HAS-A relationship ko inheritance se represent nahi karna chahiye. Iske liye Association, Aggregation ya Composition use karo.

---

## 8. C++ Examples

### Association in C++

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;

    Student(string n) {
        name = n;
    }
};

class Teacher {
public:
    void teach(Student& student) {
        cout << "Teaching " << student.name;
    }
};

int main() {
    Student s1("Rahul");
    Teacher t1;

    t1.teach(s1);

    return 0;
}
```

**Output:**

```text
Teaching Rahul
```

Teacher student ko reference ke through use kar raha hai. Student aur Teacher independently exist karte hain.

### Aggregation in C++

```cpp
#include <iostream>
using namespace std;

class Teacher {
public:
    string name;

    Teacher(string n) {
        name = n;
    }
};

class Department {
private:
    Teacher& teacher;

public:
    Department(Teacher& t) : teacher(t) {}

    void showTeacher() {
        cout << teacher.name;
    }
};

int main() {
    Teacher t1("Amit");

    {
        Department d1(t1);
        d1.showTeacher();
    }

    return 0;
}
```

**Output:**

```text
Amit
```

Teacher object Department ke bahar create hua hai aur Department uska reference store karta hai.

**Important lifetime rule:** `Teacher` object ko `Department` se zyada time tak exist karna chahiye. Agar Teacher pehle destroy ho gaya aur Department us reference ko use kare, toh undefined behavior ho sakta hai.

### Composition in C++

```cpp
#include <iostream>
using namespace std;

class Room {
public:
    Room() {
        cout << "Room created\n";
    }

    ~Room() {
        cout << "Room destroyed\n";
    }
};

class House {
private:
    Room room;

public:
    House() {
        cout << "House created\n";
    }

    ~House() {
        cout << "House destroyed\n";
    }
};

int main() {
    House h1;

    return 0;
}
```

**Output:**

```text
Room created
House created
House destroyed
Room destroyed
```

Yahan Room, House ka member object hai. House destroy hone par uska Room member bhi automatically destroy hota hai.

---

## 9. MERN Stack Mein Practical Use

MERN Stack mein:

- MongoDB
- Express.js
- React.js
- Node.js

In concepts ka use application ka structure design karne mein hota hai.

### Association Example

User aur Post:

- User posts create karta hai.
- Post ka author User hota hai.
- Dono ko independently model kiya ja sakta hai.

### Aggregation Example

Team aur Players:

- Ek team multiple players ko refer kar sakti hai.
- Players alag documents ya objects ke roop mein exist kar sakte hain.
- Team change hone par player ka record delete karna zaroori nahi.

### Composition Example

Order aur OrderItems:

- Ek order ke andar us order ke items store kiye ja sakte hain.
- Agar OrderItems sirf us Order ke parts hain, toh unhe order ke saath manage karna Composition-style design ho sakta hai.
- Lekin real application mein Order aur OrderItems ko alag collections mein rakhne par deletion aur lifecycle rules explicitly implement karne padte hain.

**Important:** MongoDB mein embedded document ya separate collection choose karna automatically UML Composition/Aggregation decide nahi karta. Actual ownership aur lifecycle rules design par depend karte hain.

---

## 10. Advantages and Disadvantages

### Association

**Advantages:**

- Classes independent rehti hain.
- Flexible relationship hota hai.
- Objects ko reuse kar sakte hain.

**Disadvantages:**

- Relationship manage karna padta hai.
- Complex systems mein dependencies badh sakti hain.

### Aggregation

**Advantages:**

- Objects independently reuse ho sakte hain.
- Whole-part relationship clearly represent hota hai.
- Flexible ownership model hota hai.

**Disadvantages:**

- Object references aur lifetimes manage karne padte hain.
- Reference invalid hone ka risk ho sakta hai.

### Composition

**Advantages:**

- Ownership clear hoti hai.
- Whole object apne parts ko manage karta hai.
- Code structure organized ho sakta hai.

**Disadvantages:**

- Components tightly connected ho sakte hain.
- Parts ko independently reuse karna difficult ho sakta hai.
- Ownership rules carefully design karne padte hain.

---

## 11. Common Mistakes

1. Aggregation aur Composition ko same samajhna.
2. Association ko inheritance samajhna.
3. Ye assume karna ki Aggregation mein part object kabhi share nahi ho sakta.
4. Composition ka matlab har language mein automatic immediate destruction samajhna.
5. UML diamond ko part side par draw karna.
6. C++ reference ki lifetime ko ignore karna.
7. MongoDB embedded documents ko automatically Composition maan lena.

---

## 12. Interview Questions and Answers

**Q1. What is Association?**

Association do independent objects ke beech general relationship hai.

**Q2. What is Aggregation?**

Aggregation ek weak HAS-A relationship hai jisme part object independently exist kar sakta hai.

**Q3. What is Composition?**

Composition ek strong ownership-based HAS-A relationship hai jisme whole apne parts ka lifecycle manage karta hai.

**Q4. What is the main difference between Aggregation and Composition?**

Aggregation mein part independently exist kar sakta hai. Composition mein part ka lifecycle whole ke ownership se strongly connected hota hai.

**Q5. What is the UML symbol for Aggregation?**

Hollow diamond.

**Q6. What is the UML symbol for Composition?**

Filled diamond.

**Q7. Which side contains the diamond in UML?**

Whole/owner side.

**Q8. Is Association an IS-A relationship?**

No. IS-A relationship Inheritance represent karta hai.

**Q9. Can Aggregation objects exist independently?**

Yes.

**Q10. Give one example of Composition.**

House aur uske owned Rooms.

---

## 13. Practice Tasks

### Task 1: Association

Do classes banao:

- Doctor
- Patient

Doctor ke andar `treat()` method banao jo Patient ka naam print kare.

### Task 2: Aggregation

Do classes banao:

- Player
- Team

Player ka object separately create karo aur Team ke constructor mein pass karo.

### Task 3: Composition

Do classes banao:

- Engine
- Car

Car class ke andar Engine ka member object create karo.

### Task 4: UML

In relationships ke UML diagrams banao:

- Teacher-Student
- Department-Teacher
- House-Room

Har diagram mein correct symbol aur multiplicity show karo.

---

## 14. Quick Revision

| Concept     | Easy Meaning           | Example            |
| ----------- | ---------------------- | ------------------ |
| Association | Objects connected hain | Teacher-Student    |
| Aggregation | Weak HAS-A             | Department-Teacher |
| Composition | Strong ownership HAS-A | House-Room         |
| Inheritance | IS-A                   | Car-Vehicle        |

### One-line Revision

- Association = General relationship.
- Aggregation = Weak whole-part relationship.
- Composition = Strong whole-part ownership.
- Inheritance = IS-A relationship.
- Hollow diamond = Aggregation.
- Filled diamond = Composition.
- Diamond = Whole/owner side.

---

## 15. Topic Completion Checklist

- [ ] Association samajh liya.
- [ ] Aggregation samajh liya.
- [ ] Composition samajh liya.
- [ ] Teeno ke differences samajh liye.
- [ ] UML symbols samajh liye.
- [ ] Multiplicity samajh li.
- [ ] Inheritance aur Association ka difference samajh liya.
- [ ] C++ examples practice kar liye.
- [ ] MERN examples samajh liye.
- [ ] Practice tasks complete kar liye.

**Topic 08 Complete: Association, Aggregation & Composition**
