# Topic 05 – Space Complexity Analysis in C++

## 1. Space Complexity kya hoti hai?

Space Complexity batati hai ki kisi algorithm ko execute karne ke liye kitni memory required hoti hai.

Jab hum DSA mein kisi algorithm ko analyze karte hain, toh Time Complexity ke saath Space Complexity bhi check karte hain.

**Example:**

```cpp
int a = 10;
int b = 20;
int sum = a + b;
```

Yahan 3 integer variables memory use kar rahe hain.

**Space Complexity: O(1)**

## 2. Space Complexity ke Types

Space ko samajhne ke liye do important concepts hain:

1. Input Space
2. Auxiliary Space

### A. Input Space

Input Space woh memory hoti hai jo input data store karne ke liye use hoti hai.

Example:

```cpp
int arr[5] = {10, 20, 30, 40, 50};
```

Array mein 5 integers store hain.

Input Space = O(n)

### B. Auxiliary Space

Auxiliary Space woh extra memory hoti hai jo algorithm input ke alawa use karta hai.

Example:

```cpp
int a = 10;
int b = 20;

int sum = a + b;
```

Extra variables ki memory constant hai.

Auxiliary Space = O(1)

## 3. O(1) – Constant Space

Jab algorithm input size badhne par bhi fixed extra memory use karta hai.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 5;
    int sum = 0;

    for (int i = 1; i <= n; i++) {
        sum += i;
    }

    cout << sum;

    return 0;
}
```

Yahan variables ki sankhya fixed hai.

**Auxiliary Space: O(1)**

## 4. O(n) – Linear Space

Jab input size ke according extra memory increase hoti hai.

Example:

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int n = 5;

    vector<int> arr(n);

    for (int i = 0; i < n; i++) {
        arr[i] = i + 1;
    }

    return 0;
}
```

Vector mein n elements store ho rahe hain.

**Auxiliary Space: O(n)**

## 5. O(n²) – Quadratic Space

Jab memory use input size ke square ke according increase hoti hai.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int n = 3;
    int arr[3][3];

    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            arr[i][j] = i + j;
        }
    }

    return 0;
}
```

Total elements = n × n

**Space Complexity: O(n²)**

## 6. Recursion mein Space Complexity

Recursion mein function baar-baar khud ko call karta hai.

Har function call ke liye Call Stack mein memory use hoti hai.

Example:

```cpp
#include <iostream>
using namespace std;

void print(int n) {
    if (n == 0) {
        return;
    }

    cout << n << endl;
    print(n - 1);
}

int main() {
    print(5);
    return 0;
}
```

Yahan maximum n recursive calls stack mein ho sakti hain.

**Auxiliary Space: O(n)**

## 7. Loop vs Recursion – Space Complexity

| Loop                                       | Recursion                           |
| ------------------------------------------ | ----------------------------------- |
| Generally fixed extra memory               | Function call stack use hota hai    |
| Often O(1) auxiliary space                 | Often O(n) auxiliary space          |
| Call stack recursion jaisa grow nahi karta | Calls ke saath stack grow karta hai |

Note: Har recursion O(n) nahi hoti. Space maximum simultaneously active recursive calls par depend karti hai.

## 8. Time Complexity vs Space Complexity

| Time Complexity                | Space Complexity                     |
| ------------------------------ | ------------------------------------ |
| Execution operations ki growth | Memory usage ki growth               |
| Algorithm kitna work karta hai | Algorithm kitni memory use karta hai |
| O(n), O(n²) etc.               | O(1), O(n) etc.                      |

## 9. Space Complexity Calculate karne ke Rules

1. Fixed number of variables = O(1)
2. Array of n elements = O(n)
3. 2D array of n × n = O(n²)
4. Recursion stack of n calls = O(n)
5. Fixed-size extra array = O(1) with respect to input size.
6. Auxiliary Space aur Input Space ko alag samjho.

## 10. Common Mistakes

- Time Complexity aur Space Complexity ko same samajhna.
- Input Space ko Auxiliary Space samajhna.
- Recursion ki stack memory ignore karna.
- Har loop ko O(n) Space samajhna.
- Fixed-size array ko automatically O(n) samajhna.

## 11. Practice Questions

1. Space Complexity kya hoti hai?
2. Input Space aur Auxiliary Space mein difference kya hai?
3. 5 integer variables ki Space Complexity kya hogi?
4. n elements wale array ki Space Complexity kya hogi?
5. n × n matrix ki Space Complexity kya hogi?
6. Recursion mein Call Stack kya hota hai?
7. Loop aur Recursion ki Space Complexity mein kya difference hai?

## Quick Revision

- Space Complexity = Memory usage growth.
- Input Space = Input store karne ki memory.
- Auxiliary Space = Extra memory.
- O(1) = Constant Space.
- O(n) = Linear Space.
- O(n²) = Quadratic Space.
- Recursion = Call Stack memory.

## Topic Status

**Topic 05 – Completed**

**Next Topic 06:** Arrays – Introduction and Basics in C++.
