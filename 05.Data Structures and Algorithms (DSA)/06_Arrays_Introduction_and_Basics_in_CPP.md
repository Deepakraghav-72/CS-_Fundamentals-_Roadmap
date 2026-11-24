# Topic 06 – Arrays: Introduction and Basics in C++

## 1. Array kya hota hai?

Array ek data structure hai jo multiple values ko ek hi variable name ke andar store karta hai.

Array mein generally same data type ke elements store hote hain.

Example:

```cpp
int marks[5] = {80, 90, 75, 85, 95};
```

Yahan:

- `int` = Data Type
- `marks` = Array Name
- `5` = Array Size
- Values = Array Elements

## 2. Array ki zaroorat kyu hoti hai?

Maan lo humein 5 students ke marks store karne hain.

Array ke bina:

```cpp
int marks1 = 80;
int marks2 = 90;
int marks3 = 75;
int marks4 = 85;
int marks5 = 95;
```

Array ke saath:

```cpp
int marks[5] = {80, 90, 75, 85, 95};
```

Array se code short aur manageable ho jata hai.

## 3. Array Declaration

Array declare karne ka syntax:

```cpp
data_type array_name[array_size];
```

Example:

```cpp
int numbers[5];
float prices[10];
char letters[4];
```

## 4. Array Initialization

Array ko values assign karna Initialization kehlata hai.

Example:

```cpp
int arr[5] = {10, 20, 30, 40, 50};
```

Compiler size automatically bhi calculate kar sakta hai:

```cpp
int arr[] = {10, 20, 30, 40, 50};
```

Yahan array size automatically 5 ho jayega.

## 5. Array Indexing

Array mein har element ka ek index number hota hai.

Index hamesha 0 se start hota hai.

Example:

```cpp
int arr[5] = {10, 20, 30, 40, 50};
```

| Index | Value |
| ----- | ----- |
| 0     | 10    |
| 1     | 20    |
| 2     | 30    |
| 3     | 40    |
| 4     | 50    |

Important:

- First Index = 0
- Last Index = n - 1

## 6. Array Elements Access karna

Array ke elements ko index ki help se access karte hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    cout << arr[0] << endl;
    cout << arr[2] << endl;
    cout << arr[4] << endl;

    return 0;
}
```

Output:

```text
10
30
50
```

## 7. Array Elements Modify karna

Array ke kisi bhi element ki value change kar sakte hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    arr[2] = 100;

    cout << arr[2];

    return 0;
}
```

Output:

```text
100
```

## 8. Array ko Loop se Print karna

Array ke saare elements print karne ke liye loop use karte hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
10 20 30 40 50
```

## 9. Array Size Calculate karna

C++ mein array ka total size bytes mein calculate kar sakte hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    int size = sizeof(arr) / sizeof(arr[0]);

    cout << size;

    return 0;
}
```

Output:

```text
5
```

Explanation:

- `sizeof(arr)` = Array ka total size in bytes.
- `sizeof(arr[0])` = Ek element ka size in bytes.
- Total bytes / One element bytes = Number of elements.

Note: Yeh technique actual built-in arrays ke liye hai, `vector` ke liye nahi.

## 10. Array ki Memory Representation

Array ke elements memory mein contiguous locations par store hote hain.

Example:

```cpp
int arr[4] = {10, 20, 30, 40};
```

Conceptual representation:

| Index | Value |
| ----- | ----- |
| 0     | 10    |
| 1     | 20    |
| 2     | 30    |
| 3     | 40    |

Isi wajah se array mein index se element access karna O(1) hota hai.

## 11. Array ki Time Complexity

| Operation       | Time Complexity |
| --------------- | --------------- |
| Access by Index | O(1)            |
| Update by Index | O(1)            |
| Traversal       | O(n)            |
| Linear Search   | O(n)            |

## 12. Array ke Advantages

1. Multiple values ek variable mein store kar sakte hain.
2. Index ki help se fast access hota hai.
3. Loops ke saath easily use kar sakte hain.
4. Data ko organize karna easy hota hai.
5. Contiguous memory allocation hoti hai.

## 13. Array ke Disadvantages

1. Normal fixed-size array ka size declaration ke baad change nahi hota.
2. Same data type ke elements store hote hain.
3. Insertion aur deletion mein shifting ki zaroorat pad sakti hai.
4. Invalid index access karna undefined behavior cause kar sakta hai.

## 14. Common Mistakes

- Array indexing ko 1 se start samajhna.
- Array ke size se bahar access karna.
- Array declaration mein size galat dena.
- Loop mein `i <= n` likhna jab condition `i < n` honi chahiye.
- Array ke last index ko n samajhna, jabki woh n - 1 hota hai.

## 15. Practice Questions

1. Array kya hota hai?
2. Array indexing kis number se start hoti hai?
3. 10 elements wale array ka last index kya hoga?
4. Array declaration ka syntax likho.
5. Array ke third element ko access kaise karenge?
6. Array ke elements ko loop se print karo.
7. Array ka total size kaise calculate karenge?
8. Array mein element access karne ki Time Complexity kya hai?

## Quick Revision

- Array = Same data type ke multiple elements.
- Indexing = 0 se start.
- Last Index = n - 1.
- Access = O(1).
- Traversal = O(n).
- Update = O(1).
- Array elements contiguous memory mein store hote hain.

## Topic Status

**Topic 06 – Completed**

**Next Topic 07:** Types of Arrays – 1D, 2D and Multidimensional Arrays in C++.
