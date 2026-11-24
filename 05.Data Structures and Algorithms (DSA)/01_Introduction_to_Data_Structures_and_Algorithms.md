# 01. Introduction to Data Structures and Algorithms (DSA)

## 1. DSA kya hai?

DSA ka full form hai **Data Structures and Algorithms**.

DSA computer science ka important concept hai jisme hum seekhte hain:

1. Data ko efficiently store aur organize kaise karein.
2. Data par operations efficiently kaise perform karein.
3. Kisi problem ko solve karne ke liye best approach kaise choose karein.

**DSA = Data Structures + Algorithms**

Example: Agar humein 10 lakh students ke records mein kisi ek student ko search karna hai, toh humein aisa data structure aur algorithm choose karna chahiye jo search ko fast bana sake.

## 2. Data Structure kya hota hai?

Data Structure ek way hai jisme computer memory mein data ko organize aur store kiya jata hai, taaki us data ko efficiently access aur modify kar sakein.

Example:

```cpp
int marks[5] = {80, 75, 90, 65, 85};
```

Yahan `marks` ek Array hai jo multiple values ko ek structure mein store karta hai.

### Real-life examples

| Data Structure | Real-life Example           |
| -------------- | --------------------------- |
| Array          | Numbered seats              |
| Stack          | Plates ka pile              |
| Queue          | Ticket counter ki line      |
| Linked List    | Train ke connected coaches  |
| Tree           | Family tree                 |
| Graph          | Cities connected by roads   |
| Hash Table     | Dictionary / Contact lookup |

## 3. Algorithm kya hota hai?

Algorithm kisi problem ko solve karne ke liye step-by-step instructions ka set hota hai.

Example: Do numbers ka sum find karna.

**Steps:**

1. First number input lo.
2. Second number input lo.
3. Dono numbers add karo.
4. Result print karo.

C++ example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    int b = 20;

    int sum = a + b;

    cout << sum;

    return 0;
}
```

**Output:**

```text
30
```

Yahan addition perform karne ke steps ek simple algorithm represent karte hain.

## 4. Data Structure aur Algorithm mein Difference

| Data Structure                 | Algorithm                             |
| ------------------------------ | ------------------------------------- |
| Data organize karta hai        | Problem solve karta hai               |
| Data store karne ka method     | Steps ka sequence                     |
| Example: Array                 | Example: Binary Search                |
| Data ko manage karne mein help | Data par operations perform karta hai |

Dono ek doosre ke saath milkar efficient programs banate hain.

## 5. Types of Data Structures

Data Structures ko broadly do categories mein divide kar sakte hain:

### A. Primitive Data Structures

Basic built-in data types.

Examples in C++:

- int
- char
- float
- double
- bool

```cpp
int age = 22;
char grade = 'A';
float price = 99.5f;
double salary = 45000.75;
bool isActive = true;
```

### B. Non-Primitive Data Structures

Ye multiple values ko organize aur manage karne ke liye use hote hain.

Inhe commonly do categories mein divide karte hain:

**1. Linear Data Structures**

Data elements sequential order mein arranged hote hain.

Examples:

- Array
- Linked List
- Stack
- Queue

**2. Non-Linear Data Structures**

Data elements simple sequential order mein arranged nahi hote; hierarchical ya network-like relationships ho sakte hain.

Examples:

- Tree
- Graph

### Classification Diagram

```text
                 Data Structures
                       |
             ---------------------
             |                   |
         Primitive           Non-Primitive
                                 |
                         -----------------
                         |               |
                       Linear        Non-Linear
                         |               |
                    Array              Tree
                    Linked List       Graph
                    Stack
                    Queue
```

Note: Ye DSA learning ke liye common classification hai. Real implementations mein additional categories bhi hoti hain.

## 6. Static vs Dynamic Data Structures

| Static                        | Dynamic                                     |
| ----------------------------- | ------------------------------------------- |
| Size generally fixed hota hai | Size runtime par change ho sakta hai        |
| Example: Fixed-size Array     | Example: Linked List                        |
| Memory allocation often fixed | Memory allocation grow/shrink kar sakti hai |

Example:

```cpp
// Static size array
int arr[5] = {1, 2, 3, 4, 5};

// Dynamic size using vector
#include <vector>
vector<int> nums = {1, 2, 3};

nums.push_back(4);
```

C++ `vector` automatically size manage karta hai.

## 7. DSA kyu important hai?

1. Problem-solving skills improve hoti hain.
2. Efficient code likhna aata hai.
3. Time aur memory save hoti hai.
4. Coding interviews mein help milti hai.
5. Large data handle karna easy hota hai.
6. Software development ke fundamentals strong hote hain.

## 8. DSA ke Important Operations

Common data structure operations:

| Operation | Meaning                     |
| --------- | --------------------------- |
| Traversal | Elements ko visit karna     |
| Insertion | New element add karna       |
| Deletion  | Element remove karna        |
| Searching | Element find karna          |
| Sorting   | Data arrange karna          |
| Updating  | Existing value change karna |
| Accessing | Element retrieve karna      |

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[4] = {10, 20, 30, 40};

    // Accessing
    cout << arr[0] << endl;

    // Updating
    arr[1] = 50;

    // Traversal
    for (int i = 0; i < 4; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

**Output:**

```text
10
10 50 30 40
```

## 9. DSA aur Time Complexity ka Introduction

Time Complexity batati hai ki input size badhne par algorithm ka execution work kis rate se grow karta hai.

Example:

```cpp
for (int i = 0; i < 5; i++) {
    cout << i << endl;
}
```

Loop 5 times execute hota hai.

Agar input size `n` ho aur loop `n` times chale, toh commonly time complexity `O(n)` hoti hai.

Important complexity names:

| Complexity | Name         |
| ---------- | ------------ |
| O(1)       | Constant     |
| O(log n)   | Logarithmic  |
| O(n)       | Linear       |
| O(n log n) | Linearithmic |
| O(n²)      | Quadratic    |
| O(2ⁿ)      | Exponential  |

Inhe hum aage detail mein padhenge.

## 10. DSA mein C++ ka Role

C++ DSA ke liye popular language hai kyunki:

- Fast execution.
- STL (Standard Template Library).
- Arrays, vectors, stacks, queues, maps, sets.
- Pointers and memory management.
- Strong control over data structures.

Important C++ STL components:

| STL Component  | Use                          |
| -------------- | ---------------------------- |
| vector         | Dynamic array                |
| stack          | LIFO                         |
| queue          | FIFO                         |
| deque          | Double-ended queue           |
| set            | Unique sorted elements       |
| map            | Key-value pairs, sorted keys |
| unordered_map  | Hash-based key-value storage |
| priority_queue | Heap-based priority access   |

## 11. Common Mistakes

1. Sirf code yaad karna, logic na samajhna.
2. Time complexity ignore karna.
3. Har problem mein same data structure use karna.
4. Edge cases test na karna.
5. STL use karna seekhna, lekin underlying concepts ignore karna.
6. Practice ke bina sirf theory padhna.

## 12. Interview Questions

**Q1. DSA ka full form kya hai?**

Data Structures and Algorithms.

**Q2. Data Structure kya hai?**

Data ko organize aur store karne ka method.

**Q3. Algorithm kya hai?**

Problem solve karne ke step-by-step instructions.

**Q4. Linear Data Structure kya hai?**

Jisme elements sequential order mein arranged hote hain.

**Q5. Non-Linear Data Structure kya hai?**

Jisme elements hierarchical ya network-like relationships mein arranged hote hain.

**Q6. Array kis type ka data structure hai?**

Linear Data Structure.

**Q7. Tree kis type ka data structure hai?**

Non-Linear Data Structure.

**Q8. Static aur Dynamic Data Structure mein difference?**

Static structure ka size generally fixed hota hai; dynamic structure runtime par grow ya shrink kar sakta hai.

**Q9. C++ DSA ke liye kyu popular hai?**

Performance, STL aur memory control ke karan.

**Q10. Time Complexity kya batati hai?**

Input size ke respect mein algorithm ka computational work kaise grow karta hai.

## 13. Practical Tasks

1. C++ mein 5 integers ka array banao.
2. Array ke elements print karo.
3. Array ke kisi element ko update karo.
4. Do numbers ka sum nikalne ka algorithm likho.
5. Linear aur Non-Linear data structures ke 3-3 examples likho.
6. C++ `vector` mein `push_back()` use karke element add karo.

## 14. Quick Revision

- DSA = Data Structures + Algorithms.
- Data Structure = Data organize karne ka method.
- Algorithm = Problem solve karne ke steps.
- Primitive = int, char, float, double, bool.
- Non-Primitive = Array, Linked List, Stack, Queue, Tree, Graph.
- Linear = Sequential arrangement.
- Non-Linear = Hierarchical/network arrangement.
- Static = Generally fixed size.
- Dynamic = Runtime par size change ho sakta hai.
- Common operations = Traversal, Insertion, Deletion, Searching, Sorting.
- Time Complexity = Computational work growth.
- C++ STL = Ready-made data structures and algorithms.

## 15. MCQ Practice

**Q1. DSA ka full form kya hai?**

A. Data Software Algorithm  
B. Data Structures and Algorithms  
C. Digital System Architecture  
D. Data Storage Application

**Q2. Array kis category mein aata hai?**

A. Non-Linear  
B. Linear  
C. Primitive  
D. Graph

**Q3. Tree kis type ka data structure hai?**

A. Linear  
B. Non-Linear  
C. Primitive  
D. Static only

**Q4. Algorithm kya hota hai?**

A. Hardware  
B. Programming language  
C. Step-by-step instructions  
D. Database

**Q5. C++ mein dynamic array ke liye kya use karte hain?**

A. int  
B. vector  
C. char  
D. bool

**Q6. Stack ka real-life example kya hai?**

A. Plates ka pile  
B. Ticket line  
C. Road map  
D. Family tree

**Q7. Searching ka meaning kya hai?**

A. Data delete karna  
B. Data arrange karna  
C. Element find karna  
D. Element update karna

**Q8. O(1) ka naam kya hai?**

A. Linear  
B. Constant  
C. Quadratic  
D. Exponential

**Q9. Dynamic Data Structure ki property kya hai?**

A. Size kabhi change nahi hota  
B. Runtime par size change ho sakta hai  
C. Data store nahi karta  
D. Sirf numbers store karta hai

**Q10. DSA seekhne ka main benefit kya hai?**

A. Sirf syntax yaad karna  
B. Efficient problem-solving  
C. Computer hardware banana  
D. Internet speed badhana
