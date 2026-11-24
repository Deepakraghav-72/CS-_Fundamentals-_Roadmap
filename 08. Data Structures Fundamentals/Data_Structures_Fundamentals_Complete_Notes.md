# DATA STRUCTURES FUNDAMENTALS

## Complete CS Fundamentals & Interview Preparation Notes

**Language:** Easy Hinglish  
**Programming Language:** C++  
**Level:** Beginner to Advanced

---

# 1. Introduction to Data Structures

## 1.1 What is Data Structure?

Data Structure ek specific way hai jisme computer memory mein data ko organize, store aur manage kiya jata hai, taaki data ko efficiently access aur modify kar sakein.

**Example:**

Agar humein 100 students ke marks store karne hain, toh hum Array use kar sakte hain.

Agar humein data ko frequently insert aur delete karna hai, toh Linked List useful ho sakti hai.

## 1.2 Why Data Structures are Important?

1. Efficient Data Storage
2. Fast Searching
3. Fast Insertion and Deletion
4. Better Memory Management
5. Code Optimization
6. Handling Large Data
7. Efficient Algorithm Development

## 1.3 Real-Life Examples

| Data Structure | Real-Life Example              |
| -------------- | ------------------------------ |
| Array          | Students ki marks list         |
| Linked List    | Music playlist                 |
| Stack          | Browser back button            |
| Queue          | Ticket booking line            |
| Tree           | Computer file system           |
| Graph          | Social media connections       |
| Hash Table     | Dictionary                     |
| Heap           | Priority-based task scheduling |

## 1.4 Data Structure vs Algorithm

| Data Structure          | Algorithm                 |
| ----------------------- | ------------------------- |
| Data organize karta hai | Problem solve karta hai   |
| Data storage par focus  | Steps and logic par focus |
| Example: Array          | Example: Binary Search    |
| Data manage karta hai   | Data process karta hai    |

---

# 2. Types of Data Structures

Data Structures ko multiple ways mein classify kiya jata hai.

## 2.1 Primitive Data Structures

Basic built-in data types.

Examples:

- int
- char
- float
- double
- bool
- Pointer

## 2.2 Non-Primitive Data Structures

Complex data structures jo primitive types se build hote hain.

Examples:

- Array
- Linked List
- Stack
- Queue
- Tree
- Graph

## 2.3 Linear Data Structures

Jisme elements sequential order mein arrange hote hain.

Examples:

- Array
- Linked List
- Stack
- Queue

## 2.4 Non-Linear Data Structures

Jisme data sequential manner mein arrange nahi hota.

Examples:

- Tree
- Graph
- Trie

## 2.5 Static Data Structures

Jinka size generally compile time ya creation ke time fixed hota hai.

Example:

```cpp
int arr[5];
```

## 2.6 Dynamic Data Structures

Jinka size runtime par grow ya shrink ho sakta hai.

Examples:

- Linked List
- Dynamic Array (vector)
- Trees
- Graphs

**Important:** Static vs Dynamic classification allocation aur size behavior ko describe karti hai. Ye Linear vs Non-Linear classification se alag hai.

---

# 3. Abstract Data Type (ADT)

## 3.1 What is ADT?

Abstract Data Type ek logical model hai jo define karta hai ki data structure kya operations support karega, bina ye bataye ki internally operations kaise implement honge.

Example: Stack ADT

Operations:

- push()
- pop()
- top()
- isEmpty()

Stack ko Array ya Linked List dono se implement kar sakte hain.

## 3.2 ADT vs Data Structure

| ADT                               | Data Structure                          |
| --------------------------------- | --------------------------------------- |
| Logical behavior define karta hai | Actual implementation provide karta hai |
| What to do                        | How to do                               |
| Example: Stack                    | Array-based Stack                       |
| Implementation independent        | Implementation specific                 |

---

# 4. Data Structure Operations

Common operations:

1. Traversal – Elements visit karna.
2. Insertion – New element add karna.
3. Deletion – Element remove karna.
4. Searching – Element find karna.
5. Sorting – Data arrange karna.
6. Updating – Existing element modify karna.
7. Accessing – Element retrieve karna.
8. Merging – Two data structures combine karna.

## Example: Array

```cpp
int arr[5] = {10, 20, 30, 40, 50};
```

- Access: arr[2]
- Update: arr[2] = 35
- Traversal: Loop
- Searching: Linear Search
- Insertion: Elements shift karna pad sakta hai.
- Deletion: Elements shift karna pad sakta hai.

---

# 5. Time and Space Complexity

Ye Data Structures aur DSA ka sabse important foundation hai.

## 5.1 Time Complexity

Time Complexity batati hai ki input size badhne par algorithm ke operations kitni speed se grow karte hain.

Ye actual seconds measure nahi karti.

## 5.2 Space Complexity

Space Complexity batati hai ki algorithm ko input ke according kitni memory chahiye.

Ismein auxiliary space aur problem ke hisaab se input storage bhi distinguish kiya jata hai.

## 5.3 Big O Notation

Big O algorithm ki asymptotic upper bound describe karta hai.

Common complexities:

| Complexity | Name         | Example                  |
| ---------- | ------------ | ------------------------ |
| O(1)       | Constant     | Array index access       |
| O(log n)   | Logarithmic  | Binary Search            |
| O(n)       | Linear       | Linear Search            |
| O(n log n) | Linearithmic | Merge Sort               |
| O(n²)      | Quadratic    | Bubble Sort worst case   |
| O(n³)      | Cubic        | Three nested loops       |
| O(2ⁿ)      | Exponential  | Basic recursive subsets  |
| O(n!)      | Factorial    | Brute-force permutations |

## 5.4 Other Asymptotic Notations

**Big O – O(f(n))**

Asymptotic upper bound.

**Omega – Ω(f(n))**

Asymptotic lower bound.

**Theta – Θ(f(n))**

Tight asymptotic bound.

## 5.5 Best, Average and Worst Case

- Best Case: Minimum operations.
- Average Case: Expected operations for an input distribution.
- Worst Case: Maximum operations for input size n.

Example: Linear Search

| Case    | Complexity |
| ------- | ---------- |
| Best    | O(1)       |
| Average | O(n)       |
| Worst   | O(n)       |

## 5.6 O(1) Example

```cpp
int arr[5] = {10, 20, 30, 40, 50};

cout << arr[2];
```

Direct index access: O(1).

## 5.7 O(n) Example

```cpp
for(int i = 0; i < n; i++) {
    cout << i;
}
```

Loop n times: O(n).

## 5.8 O(n²) Example

```cpp
for(int i = 0; i < n; i++) {
    for(int j = 0; j < n; j++) {
        cout << i << j;
    }
}
```

Total operations approximately n × n: O(n²).

## 5.9 O(log n) Example

```cpp
while(n > 1) {
    n = n / 2;
}
```

Har iteration mein input half ho raha hai: O(log n).

## 5.10 Important Complexity Rules

1. Constants ignore karte hain: O(2n) = O(n).
2. Lower-order terms ignore karte hain: O(n² + n) = O(n²).
3. Consecutive loops generally add hote hain.
4. Nested loops generally multiply hote hain.
5. Input ko repeatedly half karne par logarithmic complexity aa sakti hai.
6. Worst-case complexity important hoti hai, lekin average aur amortized complexity bhi samajhni chahiye.

---

# 6. Array

## 6.1 What is an Array?

Array ek linear data structure hai jo same data type ke elements ko contiguous memory locations mein store karta hai.

Example:

```cpp
int arr[5] = {10, 20, 30, 40, 50};
```

## 6.2 Array Features

- Same data type.
- Contiguous memory.
- Index-based access.
- Zero-based indexing in C++.
- Fixed size for built-in arrays.

## 6.3 Array Indexing

```cpp
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
```

Last index = n - 1.

## 6.4 Array Operations Complexity

| Operation                          | Complexity |
| ---------------------------------- | ---------- |
| Access by index                    | O(1)       |
| Update by index                    | O(1)       |
| Search (unsorted)                  | O(n)       |
| Search (sorted, binary search)     | O(log n)   |
| Insert at end (if space available) | O(1)       |
| Insert at beginning                | O(n)       |
| Delete at beginning                | O(n)       |
| Delete at arbitrary position       | O(n)       |

## 6.5 Array Traversal

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30, 40, 50};

    for(int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
10 20 30 40 50
```

## 6.6 Advantages

- Fast random access.
- Simple implementation.
- Cache-friendly contiguous storage.
- Useful for fixed-size collections.

## 6.7 Disadvantages

- Built-in array ka size fixed hota hai.
- Insertion/deletion expensive ho sakta hai.
- Same type elements store karta hai.
- Large fixed arrays memory waste kar sakte hain.

## 6.8 1D and 2D Arrays

1D Array:

```cpp
int arr[3] = {10, 20, 30};
```

2D Array:

```cpp
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

2D array matrix aur table data represent karne ke liye useful hai.

## 6.9 Row-Major Order

C++ multidimensional arrays row-major order mein store hote hain.

Matlab pehli row ke elements pehle store honge, phir next row.

## 6.10 Dynamic Array – Vector

C++ STL ka vector dynamic array hai.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v;

    v.push_back(10);
    v.push_back(20);
    v.push_back(30);

    cout << v[1];

    return 0;
}
```

Output:

```text
20
```

Important functions:

- push_back()
- pop_back()
- size()
- capacity()
- empty()
- clear()
- at()
- front()
- back()

**Important:** Vector ka end insertion amortized O(1) hota hai. Kabhi-kabhi reallocation ke karan ek insertion O(n) ho sakta hai.

---

# 7. Strings

## 7.1 What is a String?

String characters ka sequence hoti hai.

C++ mein commonly `std::string` use hoti hai.

```cpp
string name = "Rahul";
```

## 7.2 String Operations

- Length
- Concatenation
- Comparison
- Searching
- Substring
- Insertion
- Deletion
- Character access

Example:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string name = "Rahul";

    cout << name.length() << endl;
    cout << name[0];

    return 0;
}
```

Output:

```text
5
R
```

## 7.3 Important String Functions

| Function  | Purpose               |
| --------- | --------------------- |
| length()  | String length         |
| size()    | Number of characters  |
| substr()  | Substring             |
| find()    | Search substring      |
| append()  | Add text at end       |
| insert()  | Insert text           |
| erase()   | Remove characters     |
| compare() | Compare strings       |
| empty()   | Check empty string    |
| clear()   | Remove all characters |

## 7.4 C-Style String vs C++ String

| C-Style String           | std::string        |
| ------------------------ | ------------------ |
| Character array          | String class       |
| Null terminator required | Internally managed |
| Manual handling          | Convenient methods |
| `strlen()`               | `length()`         |

Example:

```cpp
char name[] = "Rahul";
string city = "Delhi";
```

---

# 8. Linked List

## 8.1 What is a Linked List?

Linked List ek linear data structure hai jisme elements nodes ke form mein store hote hain.

Har node mein generally:

- Data
- Next node ka pointer

hota hai.

Array ke unlike, Linked List nodes ko contiguous memory mein store karna necessary nahi hota.

## 8.2 Node Structure

```cpp
struct Node {
    int data;
    Node* next;
};
```

## 8.3 Linked List Structure

```text
Head
 |
 v
[10|next] -> [20|next] -> [30|null]
```

## 8.4 Types of Linked List

### 1. Singly Linked List

Har node next node ko point karta hai.

```text
10 -> 20 -> 30 -> NULL
```

### 2. Doubly Linked List

Har node mein previous aur next pointer hota hai.

```text
NULL <- 10 <-> 20 <-> 30 -> NULL
```

### 3. Circular Singly Linked List

Last node first node ko point karta hai.

```text
10 -> 20 -> 30
^           |
|___________|
```

### 4. Circular Doubly Linked List

Previous aur next links circular hote hain.

## 8.5 Singly Linked List Implementation

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;

    Node(int value) {
        data = value;
        next = nullptr;
    }
};

int main() {
    Node* head = new Node(10);

    head->next = new Node(20);
    head->next->next = new Node(30);

    Node* temp = head;

    while(temp != nullptr) {
        cout << temp->data << " ";
        temp = temp->next;
    }

    // Cleanup
    while(head != nullptr) {
        Node* temp = head;
        head = head->next;
        delete temp;
    }

    return 0;
}
```

Output:

```text
10 20 30
```

## 8.6 Linked List Operations

1. Traversal
2. Insertion at beginning
3. Insertion at end
4. Insertion at position
5. Deletion at beginning
6. Deletion at end
7. Searching
8. Reversing

## 8.7 Complexity

| Operation                          | Singly Linked List |
| ---------------------------------- | ------------------ |
| Access by index                    | O(n)               |
| Search                             | O(n)               |
| Insert at head                     | O(1)               |
| Delete at head                     | O(1)               |
| Insert after known node            | O(1)               |
| Delete after known previous node   | O(1)               |
| Insert at end without tail pointer | O(n)               |
| Insert at end with tail pointer    | O(1)               |

## 8.8 Advantages

- Dynamic size.
- Efficient insertion/deletion at known positions.
- No contiguous memory requirement.
- Useful for implementing stacks and queues.

## 8.9 Disadvantages

- No direct random access.
- Extra pointer memory required.
- Pointer handling complex.
- Cache locality generally worse than arrays.

## 8.10 Array vs Linked List

| Array                 | Linked List                   |
| --------------------- | ----------------------------- |
| Contiguous storage    | Non-contiguous nodes          |
| Random access O(1)    | Access O(n)                   |
| Insertion can be O(n) | Known-position insertion O(1) |
| Fixed built-in size   | Dynamic size                  |
| Better cache locality | Extra pointer memory          |

---

# 9. Stack

## 9.1 What is Stack?

Stack ek linear data structure hai jo LIFO principle follow karta hai.

LIFO = Last In First Out.

Matlab jo element last mein insert hua, woh sabse pehle remove hoga.

Real-life example: Plates ka stack.

## 9.2 Stack Operations

1. push() – Element add karna.
2. pop() – Top element remove karna.
3. top() – Top element access karna.
4. empty() – Check empty.
5. size() – Number of elements.

## 9.3 Stack Diagram

```text
      TOP
       |
     [30]
     [20]
     [10]
```

## 9.4 Stack Using STL

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<int> st;

    st.push(10);
    st.push(20);
    st.push(30);

    cout << st.top() << endl;

    st.pop();

    cout << st.top();

    return 0;
}
```

Output:

```text
30
20
```

## 9.5 Stack Complexity

| Operation | Complexity |
| --------- | ---------- |
| Push      | O(1)       |
| Pop       | O(1)       |
| Top       | O(1)       |
| Empty     | O(1)       |
| Size      | O(1)       |

## 9.6 Stack Applications

- Function calls.
- Recursion.
- Undo/Redo.
- Browser history.
- Parentheses matching.
- Expression evaluation.
- Backtracking.
- DFS traversal.

## 9.7 Stack Overflow and Underflow

**Stack Overflow:** Fixed-capacity stack mein full hone ke baad push karna.

**Stack Underflow:** Empty stack se pop/top access karna.

---

# 10. Queue

## 10.1 What is Queue?

Queue ek linear data structure hai jo FIFO principle follow karta hai.

FIFO = First In First Out.

Matlab jo element first insert hua, woh first remove hoga.

Example: Ticket counter ki line.

## 10.2 Queue Operations

- enqueue() – Insert element.
- dequeue() – Remove element.
- front() – First element.
- back() – Last element.
- empty()
- size()

## 10.3 Queue Diagram

```text
FRONT                 REAR
  |                     |
 [10] -> [20] -> [30]
```

## 10.4 Queue Using STL

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    queue<int> q;

    q.push(10);
    q.push(20);
    q.push(30);

    cout << q.front() << endl;

    q.pop();

    cout << q.front();

    return 0;
}
```

Output:

```text
10
20
```

## 10.5 Queue Complexity

| Operation | Complexity |
| --------- | ---------- |
| Enqueue   | O(1)       |
| Dequeue   | O(1)       |
| Front     | O(1)       |
| Back      | O(1)       |
| Size      | O(1)       |

## 10.6 Types of Queue

### 1. Simple Queue

FIFO order follow karta hai.

### 2. Circular Queue

Last position ke baad next available position beginning mein ho sakti hai.

Space efficiently reuse karta hai.

### 3. Priority Queue

Elements priority ke basis par process hote hain.

### 4. Deque

Double Ended Queue. Dono ends se insertion aur deletion possible hai.

## 10.7 Circular Queue

Circular Queue mein last index ke baad index dobara zero par aa sakta hai.

Common formula:

```cpp
rear = (rear + 1) % capacity;
```

Fixed-size circular queue mein full condition commonly:

```cpp
(rear + 1) % capacity == front
```

Empty condition implementation par depend karti hai. Commonly front = -1 use kiya jata hai.

## 10.8 Deque

Deque = Double Ended Queue.

Important STL functions:

- push_front()
- push_back()
- pop_front()
- pop_back()
- front()
- back()

## 10.9 Stack vs Queue

| Stack                          | Queue                   |
| ------------------------------ | ----------------------- |
| LIFO                           | FIFO                    |
| One main insertion/removal end | Separate front and rear |
| push/pop                       | enqueue/dequeue         |
| Example: Undo                  | Example: Waiting line   |

---

# 11. Hashing and Hash Table

## 11.1 What is Hashing?

Hashing ek technique hai jisme key ko hash function ke through hash value/index mein convert kiya jata hai.

Isse searching, insertion aur deletion efficient ho sakte hain.

## 11.2 Hash Function

Hash function key ko table index mein map karta hai.

Example:

```text
h(key) = key % 10
```

Agar key = 25:

```text
25 % 10 = 5
```

Index = 5.

## 11.3 Hash Table

Hash Table key-value pairs store karne wali data structure hai.

## 11.4 Collision

Jab two different keys same index par map ho jaati hain, use collision kehte hain.

Example:

```text
25 % 10 = 5
35 % 10 = 5
```

Dono ka index same hai.

## 11.5 Collision Resolution Techniques

### 1. Separate Chaining

Same index par linked list ya another bucket structure use hota hai.

### 2. Open Addressing

Collision par table ke andar another empty slot search kiya jata hai.

Types:

- Linear Probing
- Quadratic Probing
- Double Hashing

## 11.6 Load Factor

Load Factor = Number of stored elements / Hash Table capacity.

\[
\alpha = \frac{n}{m}
\]

Where:

- n = Number of keys
- m = Number of buckets/slots

High load factor collisions increase kar sakta hai.

## 11.7 Hash Table Complexity

| Operation | Average | Worst |
| --------- | ------- | ----- |
| Search    | O(1)    | O(n)  |
| Insert    | O(1)    | O(n)  |
| Delete    | O(1)    | O(n)  |

## 11.8 Hashing in C++ STL

### unordered_map

```cpp
#include <iostream>
#include <unordered_map>
using namespace std;

int main() {
    unordered_map<string, int> marks;

    marks["Rahul"] = 90;
    marks["Aman"] = 85;

    cout << marks["Rahul"];

    return 0;
}
```

### unordered_set

Unique elements store karta hai.

```cpp
unordered_set<int> s;

s.insert(10);
s.insert(20);
s.insert(10);
```

Only two unique elements stored.

**Important:** unordered_map average O(1) operations provide karta hai, guaranteed O(1) nahi.

---

# 12. Trees

## 12.1 What is a Tree?

Tree ek non-linear hierarchical data structure hai jo nodes aur edges se milkar banta hai.

## 12.2 Important Tree Terminology

**Node:** Data store karne wala element.

**Root:** Topmost node.

**Parent:** Jiska child ho.

**Child:** Parent se connected lower node.

**Leaf Node:** Jiska koi child nahi.

**Sibling:** Same parent ke children.

**Edge:** Two nodes ke beech connection.

**Degree of Node:** Node ke children ki number.

**Depth:** Root se node tak edges ki count.

**Height:** Node se deepest leaf tak longest downward path ki edges ki count.

**Subtree:** Kisi node aur uske descendants se bana tree.

**Forest:** Multiple separate trees ka collection.

## 12.3 Tree Structure

```text
          10
         /  \
        20   30
       / \
      40  50
```

- Root = 10
- Children of 10 = 20, 30
- Leaf nodes = 40, 50, 30
- Parent of 40 = 20

## 12.4 Important Properties of Trees

For a non-empty tree:

- With n nodes, edges = n - 1.
- A tree is connected and acyclic.
- A binary tree has at most two children per node.

For a binary tree:

- Maximum nodes at level L (root at level 0) = 2^L.
- Maximum nodes in height h (measured in edges) = 2^(h+1) - 1.
- Minimum height for n nodes = ceil(log2(n+1)) - 1.

---

# 13. Binary Tree

## 13.1 What is Binary Tree?

Binary Tree ek tree hai jisme each node ke maximum two children ho sakte hain.

- Left Child
- Right Child

## 13.2 Types of Binary Tree

### 1. Full Binary Tree

Har node ke either zero ya exactly two children hote hain.

### 2. Complete Binary Tree

Last level ko chhodkar all levels completely filled hote hain aur last level left to right fill hota hai.

### 3. Perfect Binary Tree

All internal nodes ke exactly two children hote hain aur all leaf nodes same level par hote hain.

### 4. Balanced Binary Tree

Height reasonably balanced hoti hai. Exact balance condition tree type par depend karti hai.

### 5. Skewed Binary Tree

Har node ka only one child hota hai.

## 13.3 Binary Tree Node in C++

```cpp
struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = nullptr;
        right = nullptr;
    }
};
```

## 13.4 Binary Tree Traversals

Traversal ka matlab tree ke nodes ko specific order mein visit karna.

Four important traversals:

### 1. Inorder

Left → Root → Right.

### 2. Preorder

Root → Left → Right.

### 3. Postorder

Left → Right → Root.

### 4. Level Order

Level by level traversal.

Example Tree:

```text
        1
       / \
      2   3
     / \
    4   5
```

| Traversal   | Output    |
| ----------- | --------- |
| Inorder     | 4 2 5 1 3 |
| Preorder    | 1 2 4 5 3 |
| Postorder   | 4 5 2 3 1 |
| Level Order | 1 2 3 4 5 |

## 13.5 Traversal Code

```cpp
#include <iostream>
#include <queue>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = right = nullptr;
    }
};

void inorder(Node* root) {
    if(root == nullptr) return;

    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

void preorder(Node* root) {
    if(root == nullptr) return;

    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}

void postorder(Node* root) {
    if(root == nullptr) return;

    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}

void levelOrder(Node* root) {
    if(root == nullptr) return;

    queue<Node*> q;
    q.push(root);

    while(!q.empty()) {
        Node* current = q.front();
        q.pop();

        cout << current->data << " ";

        if(current->left) q.push(current->left);
        if(current->right) q.push(current->right);
    }
}
```

## 13.6 Traversal Complexity

All four traversals:

- Time: O(n)
- Recursive DFS auxiliary stack: O(h)
- Level order auxiliary queue: O(w), where w is maximum tree width.

---

# 14. Binary Search Tree (BST)

## 14.1 What is BST?

Binary Search Tree ek binary tree hai jisme ordering property follow hoti hai.

For every node:

- Left subtree keys are smaller than node key.
- Right subtree keys are greater than node key.

Duplicates ka behavior implementation-specific ho sakta hai.

## 14.2 BST Example

```text
         50
        /  \
       30   70
      / \   / \
     20 40 60 80
```

## 14.3 BST Operations

1. Search
2. Insert
3. Delete
4. Minimum
5. Maximum
6. Traversal

## 14.4 BST Complexity

| Operation | Average Balanced | Worst Skewed |
| --------- | ---------------- | ------------ |
| Search    | O(log n)         | O(n)         |
| Insert    | O(log n)         | O(n)         |
| Delete    | O(log n)         | O(n)         |

## 14.5 BST Search Code

```cpp
Node* search(Node* root, int key) {
    if(root == nullptr || root->data == key) {
        return root;
    }

    if(key < root->data) {
        return search(root->left, key);
    }

    return search(root->right, key);
}
```

## 14.6 BST Insertion Code

```cpp
Node* insert(Node* root, int key) {
    if(root == nullptr) {
        return new Node(key);
    }

    if(key < root->data) {
        root->left = insert(root->left, key);
    }
    else if(key > root->data) {
        root->right = insert(root->right, key);
    }

    return root;
}
```

## 14.7 BST Deletion – Three Cases

1. Leaf node: Directly delete.
2. One child: Child ko parent se connect kar do.
3. Two children: Inorder successor ya predecessor se replace karke required deletion perform karo.

**Important:** BST ka inorder traversal sorted order provide karta hai.

---

# 15. Balanced Trees and AVL Tree

## 15.1 Why Balanced Trees?

Normal BST skewed ho sakta hai aur operations O(n) tak slow ho sakte hain.

Balanced trees height control karte hain.

## 15.2 AVL Tree

AVL Tree ek self-balancing Binary Search Tree hai.

Har node ka balance factor:

\[
BF = Height(Left) - Height(Right)
\]

AVL tree mein har node ke liye balance factor -1, 0 ya +1 hota hai.

## 15.3 AVL Rotations

Four common cases:

1. LL Case – Right Rotation.
2. RR Case – Left Rotation.
3. LR Case – Left Rotation, then Right Rotation.
4. RL Case – Right Rotation, then Left Rotation.

## 15.4 AVL Complexity

| Operation | Complexity |
| --------- | ---------- |
| Search    | O(log n)   |
| Insert    | O(log n)   |
| Delete    | O(log n)   |

## 15.5 Red-Black Tree

Red-Black Tree ek self-balancing BST hai jo nodes ko Red ya Black color assign karke balance constraints maintain karta hai.

Search, Insert and Delete: O(log n).

C++ STL `map` and `set` commonly Red-Black Tree-based implementations use karte hain.

---

# 16. Heap

## 16.1 What is Heap?

Heap ek specialized complete binary tree hai jo heap property follow karta hai.

## 16.2 Types of Heap

### Max Heap

Parent node ki value children se greater than or equal hoti hai.

Root par maximum element hota hai.

### Min Heap

Parent node ki value children se less than or equal hoti hai.

Root par minimum element hota hai.

## 16.3 Heap Example

Max Heap:

```text
        50
       /  \
      30   40
     / \
    10  20
```

## 16.4 Array Representation

Zero-based indexing:

- Parent = (i - 1) / 2
- Left Child = 2*i + 1
- Right Child = 2*i + 2

## 16.5 Heap Complexity

| Operation                | Complexity |
| ------------------------ | ---------- |
| Access root              | O(1)       |
| Insert                   | O(log n)   |
| Extract root             | O(log n)   |
| Build Heap               | O(n)       |
| Search arbitrary element | O(n)       |

## 16.6 Priority Queue in C++

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    priority_queue<int> pq;

    pq.push(10);
    pq.push(50);
    pq.push(30);

    cout << pq.top();

    return 0;
}
```

Output:

```text
50
```

Min Heap:

```cpp
priority_queue<int, vector<int>, greater<int>> pq;
```

---

# 17. Graphs

## 17.1 What is a Graph?

Graph ek non-linear data structure hai jisme vertices (nodes) aur edges (connections) hote hain.

Mathematically:

G = (V, E)

- V = Set of vertices.
- E = Set of edges.

## 17.2 Graph Example

```text
A ----- B
|       |
|       |
C ----- D
```

## 17.3 Graph Terminology

**Vertex:** Graph ka node.

**Edge:** Two vertices ka connection.

**Adjacent Vertices:** Directly connected vertices.

**Degree:** Undirected graph mein vertex se connected edges ki count.

**In-degree:** Directed graph mein incoming edges ki count.

**Out-degree:** Directed graph mein outgoing edges ki count.

**Path:** Vertices ka connected sequence.

**Cycle:** A path that starts and ends at the same vertex without repeating other vertices.

**Connected Graph:** Har pair of vertices ke beech path exist karta hai.

**Component:** Maximum connected subgraph.

**Weighted Graph:** Edges par weight/cost hota hai.

## 17.4 Types of Graph

1. Directed Graph
2. Undirected Graph
3. Weighted Graph
4. Unweighted Graph
5. Connected Graph
6. Disconnected Graph
7. Cyclic Graph
8. Acyclic Graph
9. Complete Graph
10. Bipartite Graph
11. DAG (Directed Acyclic Graph)

## 17.5 Directed vs Undirected Graph

| Directed             | Undirected              |
| -------------------- | ----------------------- |
| Edges have direction | Edges have no direction |
| A → B                | A — B                   |
| In-degree/out-degree | Degree                  |

## 17.6 Graph Representation

### 1. Adjacency Matrix

2D matrix use hoti hai.

If edge exists, commonly 1 store karte hain; otherwise 0.

Space Complexity: O(V²).

### 2. Adjacency List

Har vertex ke neighbors store hote hain.

Space Complexity: O(V + E).

### 3. Edge List

Edges ki list store karte hain.

Space Complexity: O(E), plus vertex metadata if required.

## 17.7 Graph Representation Comparison

| Representation   | Space  | Edge Check   |
| ---------------- | ------ | ------------ |
| Adjacency Matrix | O(V²)  | O(1)         |
| Adjacency List   | O(V+E) | O(degree(u)) |
| Edge List        | O(E)   | O(E)         |

---

# 18. Graph Traversals

## 18.1 BFS (Breadth First Search)

BFS graph traversal algorithm hai jo level-by-level nodes visit karta hai.

BFS Queue use karta hai.

Applications:

- Unweighted shortest path.
- Level-wise traversal.
- Connected components.
- Social network distance.

### BFS Code

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void BFS(int start, vector<vector<int>>& adj, int n) {
    vector<bool> visited(n, false);

    queue<int> q;

    visited[start] = true;
    q.push(start);

    while(!q.empty()) {
        int node = q.front();
        q.pop();

        cout << node << " ";

        for(int neighbor : adj[node]) {
            if(!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}
```

Time Complexity: O(V + E) using adjacency list.

## 18.2 DFS (Depth First Search)

DFS graph mein ek path par depth tak explore karta hai, phir backtrack karta hai.

DFS Stack ya Recursion use karta hai.

Applications:

- Cycle detection.
- Connected components.
- Path exploration.
- Topological sorting.
- Backtracking problems.

### DFS Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void DFS(int node, vector<vector<int>>& adj,
         vector<bool>& visited) {

    visited[node] = true;

    cout << node << " ";

    for(int neighbor : adj[node]) {
        if(!visited[neighbor]) {
            DFS(neighbor, adj, visited);
        }
    }
}
```

Time Complexity: O(V + E) using adjacency list.

**Important:** Disconnected graph mein all components traverse karne ke liye har unvisited vertex se BFS/DFS start karna hota hai.

---

# 19. Trie

## 19.1 What is Trie?

Trie ek tree-based data structure hai jo strings aur prefixes efficiently store aur search karne ke liye use hota hai.

Isse Prefix Tree bhi kehte hain.

## 19.2 Applications

- Autocomplete.
- Dictionary.
- Spell checking.
- Prefix searching.
- Word suggestions.

## 19.3 Trie Complexity

Agar word ki length L hai:

- Insert: O(L)
- Search: O(L)
- Prefix Search: O(L)

Assuming constant-time child lookup.

Space usage stored characters aur child representation par depend karta hai.

---

# 20. Disjoint Set Union (DSU)

## 20.1 What is DSU?

DSU ek data structure hai jo elements ko disjoint (non-overlapping) sets mein manage karta hai.

Isse Union-Find bhi kehte hain.

## 20.2 Main Operations

**Find:** Element kis set ka representative belong karta hai, find karta hai.

**Union:** Two sets ko combine karta hai.

## 20.3 Optimizations

1. Path Compression.
2. Union by Rank.
3. Union by Size.

In optimizations ke saath amortized time almost O(1) hota hai, formally O(α(n)) per operation.

## 20.4 Applications

- Connected components.
- Kruskal's Minimum Spanning Tree.
- Cycle detection in undirected graphs.
- Network connectivity.

---

# 21. Searching Algorithms

## 21.1 What is Searching?

Searching ka matlab data structure mein required element find karna.

## 21.2 Linear Search

Elements ko one by one check karte hain.

```cpp
int linearSearch(int arr[], int n, int key) {
    for(int i = 0; i < n; i++) {
        if(arr[i] == key) {
            return i;
        }
    }

    return -1;
}
```

Complexity:

- Best: O(1)
- Average: O(n)
- Worst: O(n)

## 21.3 Binary Search

Sorted data par search space repeatedly half karta hai.

```cpp
int binarySearch(int arr[], int n, int key) {
    int low = 0;
    int high = n - 1;

    while(low <= high) {
        int mid = low + (high - low) / 2;

        if(arr[mid] == key) {
            return mid;
        }
        else if(arr[mid] < key) {
            low = mid + 1;
        }
        else {
            high = mid - 1;
        }
    }

    return -1;
}
```

Complexity:

- Best: O(1)
- Average: O(log n)
- Worst: O(log n)

**Important:** Binary Search ke liye data par required sorted/order condition honi chahiye aur efficient random access generally useful hota hai.

## 21.4 Linear vs Binary Search

| Linear Search                | Binary Search                         |
| ---------------------------- | ------------------------------------- |
| Sorted data required nahi    | Sorted data required                  |
| O(n) worst                   | O(log n) worst                        |
| Sequential checking          | Search space half                     |
| Linked list ke liye possible | Linked list par generally inefficient |

---

# 22. Sorting Algorithms

## 22.1 What is Sorting?

Data ko ascending ya descending order mein arrange karna sorting kehlata hai.

## 22.2 Bubble Sort

Adjacent elements compare aur swap karta hai.

```cpp
void bubbleSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        bool swapped = false;

        for(int j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }

        if(!swapped) break;
    }
}
```

Complexity:

- Best: O(n) with optimized flag.
- Average: O(n²).
- Worst: O(n²).
- Space: O(1).

## 22.3 Selection Sort

Har pass mein minimum element find karke correct position par place karta hai.

Complexity:

- Best: O(n²).
- Average: O(n²).
- Worst: O(n²).
- Space: O(1).

## 22.4 Insertion Sort

Elements ko sorted portion mein correct position par insert karta hai.

Complexity:

- Best: O(n).
- Average: O(n²).
- Worst: O(n²).
- Space: O(1).

## 22.5 Merge Sort

Divide and Conquer technique use karta hai.

Steps:

1. Array divide karo.
2. Subarrays sort karo.
3. Merge karo.

Complexity:

- Best: O(n log n).
- Average: O(n log n).
- Worst: O(n log n).
- Auxiliary Space: O(n) for standard array implementation.

## 22.6 Quick Sort

Pivot choose karta hai aur partitioning ke through smaller/larger elements arrange karta hai.

Complexity:

- Best: O(n log n).
- Average: O(n log n).
- Worst: O(n²).
- Auxiliary stack: Average O(log n), worst O(n).

## 22.7 Heap Sort

Heap data structure use karke sorting perform karta hai.

Complexity:

- Best: O(n log n).
- Average: O(n log n).
- Worst: O(n log n).
- Auxiliary Space: O(1) for standard in-place implementation.

## 22.8 Counting Sort

Integer keys ko limited range mein count karke sorting karta hai.

Complexity:

- Time: O(n + k).
- Space: O(n + k) for common stable implementation.

Where k = key range.

## 22.9 Sorting Comparison Table

| Algorithm | Best       | Average    | Worst      |
| --------- | ---------- | ---------- | ---------- |
| Bubble    | O(n)       | O(n²)      | O(n²)      |
| Selection | O(n²)      | O(n²)      | O(n²)      |
| Insertion | O(n)       | O(n²)      | O(n²)      |
| Merge     | O(n log n) | O(n log n) | O(n log n) |
| Quick     | O(n log n) | O(n log n) | O(n²)      |
| Heap      | O(n log n) | O(n log n) | O(n log n) |
| Counting  | O(n+k)     | O(n+k)     | O(n+k)     |

## 22.10 Stable vs Unstable Sorting

**Stable Sorting:** Equal-key elements ka original relative order preserve hota hai.

Common stable examples:

- Bubble Sort
- Insertion Sort
- Merge Sort
- Counting Sort (standard stable version)

Common unstable examples:

- Selection Sort
- Quick Sort
- Heap Sort

**Important:** Stability implementation par depend kar sakti hai.

## 22.11 In-Place Sorting

Jo sorting algorithm generally constant auxiliary memory use karta hai, use in-place sorting kehte hain.

Examples:

- Bubble Sort
- Selection Sort
- Insertion Sort
- Heap Sort

---

# 23. Recursion

## 23.1 What is Recursion?

Recursion ek programming technique hai jisme function khud ko call karta hai.

## 23.2 Two Main Parts

1. Base Case – Recursion stop karne ki condition.
2. Recursive Case – Function ka khud ko call karna.

## 23.3 Example: Factorial

```cpp
int factorial(int n) {
    if(n == 0 || n == 1) {
        return 1;
    }

    return n * factorial(n - 1);
}
```

factorial(5):

```text
5 × 4 × 3 × 2 × 1 = 120
```

Time: O(n).

Auxiliary recursion stack: O(n).

## 23.4 Types of Recursion

- Direct Recursion
- Indirect Recursion
- Tail Recursion
- Non-Tail Recursion
- Linear Recursion
- Tree Recursion

## 23.5 Recursion vs Iteration

| Recursion               | Iteration                             |
| ----------------------- | ------------------------------------- |
| Function self-call      | Loops                                 |
| Call stack use hota hai | Generally less auxiliary memory       |
| Elegant for trees       | Often efficient for simple repetition |
| Stack overflow risk     | Infinite loop risk                    |

---

# 24. C++ STL – Standard Template Library

STL C++ ki library hai jo ready-made containers, algorithms aur iterators provide karti hai.

## 24.1 Main Components

1. Containers
2. Algorithms
3. Iterators
4. Function Objects (Functors)

## 24.2 Important Containers

| Container      | Purpose                    | Main Complexity               |
| -------------- | -------------------------- | ----------------------------- |
| vector         | Dynamic array              | Random access O(1)            |
| array          | Fixed-size array           | Random access O(1)            |
| list           | Doubly linked list         | Known-position insertion O(1) |
| forward_list   | Singly linked list         | Known-position insertion O(1) |
| stack          | LIFO                       | Push/pop O(1)                 |
| queue          | FIFO                       | Push/pop O(1)                 |
| deque          | Double-ended queue         | End operations O(1)           |
| priority_queue | Heap-based priority access | Top O(1)                      |
| set            | Unique sorted keys         | Search O(log n)               |
| multiset       | Sorted duplicate keys      | Search O(log n)               |
| map            | Sorted key-value pairs     | Search O(log n)               |
| multimap       | Sorted duplicate keys      | Search O(log n)               |
| unordered_set  | Hash-based unique keys     | Average O(1)                  |
| unordered_map  | Hash-based key-value pairs | Average O(1)                  |

## 24.3 Important STL Algorithms

Header:

```cpp
#include <algorithm>
```

Examples:

```cpp
sort(v.begin(), v.end());

reverse(v.begin(), v.end());

binary_search(v.begin(), v.end(), 20);

auto it = find(v.begin(), v.end(), 30);

int mx = *max_element(v.begin(), v.end());

int mn = *min_element(v.begin(), v.end());
```

Other useful algorithms:

- lower_bound()
- upper_bound()
- count()
- accumulate() (header `<numeric>`)
- next_permutation()
- unique()
- remove()

## 24.4 Iterators

Iterator ek object hai jo container ke elements ko access/traverse karne mein help karta hai.

Common types:

- Input Iterator
- Output Iterator
- Forward Iterator
- Bidirectional Iterator
- Random Access Iterator
- Contiguous Iterator

Examples:

```cpp
vector<int> v = {10, 20, 30};

for(auto it = v.begin(); it != v.end(); it++) {
    cout << *it << " ";
}
```

---

# 25. Choosing the Right Data Structure

| Requirement                     | Suitable Data Structure |
| ------------------------------- | ----------------------- |
| Fast index access               | Array / Vector          |
| Frequent insertion at beginning | Linked List             |
| LIFO processing                 | Stack                   |
| FIFO processing                 | Queue                   |
| Priority-based processing       | Priority Queue          |
| Fast average key lookup         | Hash Table              |
| Sorted key storage              | Map / Set               |
| Hierarchical data               | Tree                    |
| Ordered fast search             | Balanced BST            |
| Prefix searching                | Trie                    |
| Network relationships           | Graph                   |
| Connected components            | DSU                     |

**Important:** Best data structure use case, memory constraints aur required operations par depend karta hai.

---

# 26. Amortized Analysis

## 26.1 What is Amortized Analysis?

Amortized Analysis multiple operations ki sequence ka average cost analyze karta hai, even when individual operations ki cost different ho.

Example: Vector push_back()

Most insertions O(1) hoti hain, lekin capacity full hone par reallocation aur copying/moving ke karan O(n) lag sakta hai.

Long sequence mein push_back amortized O(1) hota hai.

## 26.2 Three Common Methods

1. Aggregate Method
2. Accounting Method
3. Potential Method

---

# 27. Memory Management Basics

## 27.1 Stack Memory

Function calls aur local automatic variables commonly stack storage use karte hain.

## 27.2 Heap Memory

Dynamic memory allocation generally free store/heap se hota hai.

Example:

```cpp
int* p = new int(10);

delete p;
```

## 27.3 Memory Leak

Jab dynamically allocated memory release nahi hoti aur uska usable reference lose ho jata hai, memory leak ho sakti hai.

## 27.4 Dangling Pointer

Jab pointer kisi aisi memory ko point kare jo release ho chuki ho, use dangling pointer kehte hain.

## 27.5 Null Pointer

Jo pointer kisi valid object ko point nahi karta, use null pointer keh sakte hain.

Modern C++:

```cpp
int* p = nullptr;
```

## 27.6 new vs delete

- new: Dynamic object allocation.
- delete: Single dynamically allocated object release.

For arrays:

```cpp
int* arr = new int[5];

delete[] arr;
```

**Important:** Modern C++ mein raw new/delete ke badle vector aur smart pointers prefer karne chahiye.

---

# 28. Important Data Structures Interview Questions

## Basic Questions

**Q1. What is a Data Structure?**

A method of organizing and storing data efficiently.

**Q2. Why do we use Data Structures?**

For efficient storage, access, searching, insertion and deletion.

**Q3. What are linear data structures?**

Structures where elements are organized sequentially, such as arrays and linked lists.

**Q4. What are non-linear data structures?**

Structures where elements have hierarchical or network relationships, such as trees and graphs.

**Q5. What is an ADT?**

A logical model defining data and supported operations independently of implementation.

**Q6. What is time complexity?**

How an algorithm's operation count grows with input size.

**Q7. What is space complexity?**

How memory requirements grow with input size.

**Q8. What is Big O?**

Asymptotic upper bound notation.

## Array and Linked List Questions

**Q9. Why is array access O(1)?**

Because the address of an element can be calculated directly using its index.

**Q10. Why is linked list access O(n)?**

Because nodes must be traversed sequentially.

**Q11. Array vs Linked List?**

Array supports fast random access; linked lists support efficient insertion/deletion at known positions.

**Q12. What is a doubly linked list?**

A linked list where each node stores previous and next pointers.

**Q13. What is a circular linked list?**

A linked list where the last node connects back to the first node.

## Stack and Queue Questions

**Q14. What is LIFO?**

Last In First Out.

**Q15. What is FIFO?**

First In First Out.

**Q16. Stack vs Queue?**

Stack follows LIFO; Queue follows FIFO.

**Q17. What is stack overflow?**

Trying to insert into a full fixed-capacity stack.

**Q18. What is circular queue?**

A queue that reuses freed positions through circular indexing.

## Hashing Questions

**Q19. What is hashing?**

Mapping keys to hash values or table positions.

**Q20. What is collision?**

Two different keys mapping to the same hash location.

**Q21. What is load factor?**

Number of stored keys divided by hash table capacity.

**Q22. Average search complexity in hash table?**

O(1).

**Q23. Worst-case search complexity?**

O(n).

## Tree Questions

**Q24. What is a tree?**

A connected acyclic hierarchical structure.

**Q25. What is a binary tree?**

A tree where each node has at most two children.

**Q26. What is BST?**

A binary search tree following an ordering property.

**Q27. What is a leaf node?**

A node without children.

**Q28. What is tree height?**

Longest downward path from a node to a leaf, measured in edges under the common convention.

**Q29. What is inorder traversal?**

Left, Root, Right.

**Q30. Which traversal gives sorted output in BST?**

Inorder traversal.

**Q31. What is AVL Tree?**

A self-balancing Binary Search Tree.

**Q32. What is Heap?**

A complete binary tree satisfying heap property.

## Graph Questions

**Q33. What is a graph?**

A collection of vertices and edges.

**Q34. What is BFS?**

Breadth First Search, generally using a queue.

**Q35. What is DFS?**

Depth First Search, generally using recursion or stack.

**Q36. BFS and DFS complexity?**

O(V + E) using adjacency lists.

**Q37. What is a directed graph?**

A graph whose edges have directions.

**Q38. What is a weighted graph?**

A graph whose edges have associated weights.

**Q39. What is a cycle?**

A path that returns to its starting vertex.

**Q40. What is DAG?**

Directed Acyclic Graph.

## Sorting and Searching Questions

**Q41. Which search is best for sorted arrays?**

Binary Search, with O(log n) time.

**Q42. What is Merge Sort complexity?**

O(n log n) in best, average and worst cases.

**Q43. What is Quick Sort worst-case complexity?**

O(n²).

**Q44. Which sorting algorithm is stable?**

Examples include Merge Sort and Insertion Sort.

**Q45. What is in-place sorting?**

Sorting using very little auxiliary memory, commonly O(1).

## Advanced Questions

**Q46. What is amortized complexity?**

Average cost per operation over a sequence of operations.

**Q47. What is a Trie?**

A tree-based prefix data structure.

**Q48. What is DSU?**

Disjoint Set Union, also called Union-Find.

**Q49. What is path compression?**

An optimization that makes nodes point closer to the set representative.

**Q50. What is a priority queue?**

An ADT where elements are accessed according to priority.

**Q51. What is a balanced tree?**

A tree that maintains controlled height for efficient operations.

**Q52. What is a complete binary tree?**

All levels except possibly the last are full, and the last level fills from left to right.

**Q53. What is a perfect binary tree?**

All internal nodes have exactly two children and all leaves are at the same level.

**Q54. What is a memory leak?**

Allocated memory that is no longer properly reachable or released.

**Q55. What is a dangling pointer?**

A pointer referring to an object whose lifetime has ended.

---

# 29. Tricky Interview Questions

**Q1. Is Array a primitive data structure?**

No. In the common classification, Array is a non-primitive linear data structure.

**Q2. Is Linked List stored in contiguous memory?**

No. Nodes can be located at different memory locations.

**Q3. Can binary search work on an unsorted array?**

Not correctly in its standard form. Required sorted ordering is necessary.

**Q4. Is every binary tree a BST?**

No. BST is a special type of binary tree.

**Q5. Is every BST balanced?**

No.

**Q6. Is every complete binary tree a perfect binary tree?**

No.

**Q7. Is every full binary tree perfect?**

No.

**Q8. Can a graph have cycles?**

Yes. Graphs can be cyclic or acyclic.

**Q9. Can a tree contain a cycle?**

No. A tree is acyclic.

**Q10. Can a graph be disconnected?**

Yes.

**Q11. Does BFS always give the shortest path?**

For unweighted graphs, BFS gives the shortest path in terms of number of edges from the source.

**Q12. Does DFS always give the shortest path?**

No.

**Q13. Is hash table searching always O(1)?**

No. O(1) is average/expected under suitable assumptions; worst case can be O(n).

**Q14. Is vector insertion at the end always O(1)?**

No. It is amortized O(1); an individual reallocation can cost O(n).

**Q15. Is a priority queue always FIFO?**

No. Elements are processed by priority.

**Q16. Is a stack a non-linear data structure?**

No. Stack is linear.

**Q17. Is a queue linear?**

Yes.

**Q18. Is Heap the same as Heap Memory?**

No. Heap data structure and heap memory are different concepts.

**Q19. Is O(n) always faster than O(log n)?**

For sufficiently large input sizes, O(log n) grows more slowly than O(n), but actual performance also depends on constants and implementation.

**Q20. Can a linked list use binary search?**

It can perform the comparisons conceptually, but without efficient random access, the standard binary search advantage is generally lost.

---

# 30. Quick Revision Table

| Concept        | Quick Revision                       |
| -------------- | ------------------------------------ |
| Data Structure | Organize and manage data             |
| ADT            | Logical data model                   |
| Array          | Contiguous elements                  |
| Vector         | Dynamic array                        |
| String         | Character sequence                   |
| Linked List    | Nodes connected by pointers          |
| Stack          | LIFO                                 |
| Queue          | FIFO                                 |
| Deque          | Both-end operations                  |
| Hashing        | Key-to-index mapping                 |
| Collision      | Same hash location                   |
| Tree           | Hierarchical structure               |
| Binary Tree    | Maximum two children                 |
| BST            | Ordered binary tree                  |
| AVL            | Self-balancing BST                   |
| Heap           | Complete binary tree + heap property |
| Graph          | Vertices + Edges                     |
| BFS            | Queue-based traversal                |
| DFS            | Stack/recursion-based traversal      |
| Trie           | Prefix tree                          |
| DSU            | Union-Find                           |
| Linear Search  | O(n)                                 |
| Binary Search  | O(log n)                             |
| Merge Sort     | O(n log n)                           |
| Quick Sort     | Average O(n log n)                   |
| Big O          | Asymptotic upper bound               |
| Amortized      | Sequence-based average cost          |
| STL            | Standard Template Library            |

---

# 31. Final Interview Preparation Checklist

## Fundamentals

- [ ] Data Structures Definition
- [ ] Importance and Applications
- [ ] Linear vs Non-Linear
- [ ] Static vs Dynamic
- [ ] Primitive vs Non-Primitive
- [ ] ADT
- [ ] Basic Operations

## Complexity

- [ ] Time Complexity
- [ ] Space Complexity
- [ ] Big O, Omega, Theta
- [ ] Best, Average, Worst Case
- [ ] Amortized Analysis

## Linear Data Structures

- [ ] Arrays
- [ ] Strings
- [ ] Vectors
- [ ] Singly Linked List
- [ ] Doubly Linked List
- [ ] Circular Linked List
- [ ] Stack
- [ ] Queue
- [ ] Circular Queue
- [ ] Deque

## Non-Linear Data Structures

- [ ] Hash Table
- [ ] Binary Tree
- [ ] Tree Traversals
- [ ] BST
- [ ] AVL Tree
- [ ] Red-Black Tree
- [ ] Heap
- [ ] Graph
- [ ] BFS
- [ ] DFS
- [ ] Trie
- [ ] DSU

## Algorithms

- [ ] Linear Search
- [ ] Binary Search
- [ ] Bubble Sort
- [ ] Selection Sort
- [ ] Insertion Sort
- [ ] Merge Sort
- [ ] Quick Sort
- [ ] Heap Sort
- [ ] Counting Sort

## C++ Concepts

- [ ] STL Containers
- [ ] STL Algorithms
- [ ] Iterators
- [ ] Pointers
- [ ] Dynamic Memory
- [ ] Memory Leaks
- [ ] Smart Pointers

---

# FINAL INTERVIEW ADVICE

Data Structures ko sirf definitions padhkar complete mat samajhna.

Har important data structure ke liye:

1. Definition explain karo.
2. Diagram draw karo.
3. C++ implementation likho.
4. Operations perform karo.
5. Time and Space Complexity batao.
6. Real-world application explain karo.
7. Interview questions solve karo.

**Final Goal:** Kisi bhi interviewer ke saamne explain kar pao ki kaunsa data structure kab, kyun aur kaise use karna chahiye.
