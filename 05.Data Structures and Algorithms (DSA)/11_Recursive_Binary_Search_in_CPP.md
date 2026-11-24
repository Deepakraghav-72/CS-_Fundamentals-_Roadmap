# 11. Recursive Binary Search in C++

## 1. Recursion Kya Hai?

Recursion ek programming technique hai jisme function apne aap ko call karta hai.

Example:

```cpp
void fun() {
    fun();
}
```

Isme function baar-baar khud ko call karega. Isliye recursion mein **Base Case** hona zaroori hai, warna infinite calls ho sakti hain.

## 2. Recursive Binary Search Kya Hai?

Recursive Binary Search mein Binary Search ka logic recursion ki help se implement kiya jata hai.

Har function call mein:

- Middle element check hota hai.
- Target chhota ho toh left half mein recursive call hoti hai.
- Target bada ho toh right half mein recursive call hoti hai.
- Element milne par index return hota hai.

**Condition:** Array sorted hona chahiye.

## 3. Recursive Binary Search ke Important Parts

### A. Base Case

Base Case recursion ko stop karta hai.

```cpp
if (low > high) {
    return -1;
}
```

Agar `low > high` ho gaya, iska matlab element nahi mila.

### B. Middle Index

```cpp
int mid = low + (high - low) / 2;
```

Middle element ka index calculate karta hai.

### C. Recursive Calls

Target chhota ho:

```cpp
return binarySearch(arr, low, mid - 1, target);
```

Target bada ho:

```cpp
return binarySearch(arr, mid + 1, high, target);
```

## 4. Recursive Binary Search in C++

```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int low, int high, int target) {

    // Base Case
    if (low > high) {
        return -1;
    }

    // Middle Index
    int mid = low + (high - low) / 2;

    // Element Found
    if (arr[mid] == target) {
        return mid;
    }

    // Search Left Half
    else if (target < arr[mid]) {
        return binarySearch(arr, low, mid - 1, target);
    }

    // Search Right Half
    else {
        return binarySearch(arr, mid + 1, high, target);
    }
}

int main() {

    int arr[] = {10, 20, 30, 40, 50, 60, 70};
    int n = 7;

    int target = 50;

    int result = binarySearch(arr, 0, n - 1, target);

    if (result != -1) {
        cout << "Element found at index: " << result;
    }
    else {
        cout << "Element not found";
    }

    return 0;
}
```

**Output:**

```text
Element found at index: 4
```

## 5. Recursive Binary Search Ka Dry Run

Array:

```cpp
arr = {10, 20, 30, 40, 50, 60, 70};
```

Target = `50`

| Call | Low | High | Mid | arr[mid] |
| ---- | --: | ---: | --: | -------: |
| 1    |   0 |    6 |   3 |       40 |
| 2    |   4 |    6 |   5 |       60 |
| 3    |   4 |    4 |   4 |       50 |

Third call mein target mil gaya.

**Result = Index 4**

## 6. Base Case Samjho

Agar target array mein present nahi hai, toh recursive calls search range ko chhota karti rahengi.

Jab:

```cpp
low > high
```

ho jayega, function `-1` return karega.

Isse recursion stop ho jayega.

## 7. Time and Space Complexity

| Case            | Complexity |
| --------------- | ---------- |
| Best Time       | O(1)       |
| Average Time    | O(log n)   |
| Worst Time      | O(log n)   |
| Auxiliary Space | O(log n)   |

**Space Complexity:** Recursive calls ke liye call stack use hota hai. Worst case mein O(log n) stack space lagti hai.

## 8. Iterative vs Recursive Binary Search

| Feature         | Iterative  | Recursive      |
| --------------- | ---------- | -------------- |
| Technique       | Loop       | Function calls |
| Uses            | while loop | Recursion      |
| Time Complexity | O(log n)   | O(log n)       |
| Auxiliary Space | O(1)       | O(log n)       |
| Extra stack     | Nahi       | Haan           |
| Code            | Loop-based | Function-based |

## 9. Common Mistakes

1. Sorted array ke bina Binary Search use karna.
2. Base Case bhool jana.
3. Left half mein `mid - 1` ki jagah `mid` use karna.
4. Right half mein `mid + 1` ki jagah `mid` use karna.
5. Recursive function ka return value return na karna.
6. `low` aur `high` ki initial values galat dena.

## 10. Practice Questions

1. Recursion kya hoti hai?
2. Base Case ka kya kaam hai?
3. Recursive Binary Search mein function kitni baar call ho sakta hai?
4. `low > high` hone par kya return karte hain?
5. Recursive aur Iterative Binary Search mein kya difference hai?
6. Recursive Binary Search ki space complexity kya hai?

### Coding Practice

**Question 1:** Recursive Binary Search se array mein `30` search karo.

```cpp
int arr[] = {10, 20, 30, 40, 50};
```

**Question 2:** Target `100` search karo aur element na milne par `-1` return karo.

**Question 3:** User se array ka target input lekar Recursive Binary Search perform karo.

## 11. Quick Revision

- Recursion mein function khud ko call karta hai.
- Base Case recursion ko stop karta hai.
- Recursive Binary Search sorted array par work karta hai.
- Har call mein search range half ho jati hai.
- Left search: `low` same, `high = mid - 1`.
- Right search: `low = mid + 1`, `high` same.
- Best Time Complexity = O(1).
- Average/Worst Time Complexity = O(log n).
- Auxiliary Space Complexity = O(log n).

## 12. Topic Status

- [x] Recursion Introduction
- [x] Base Case
- [x] Recursive Binary Search Algorithm
- [x] C++ Implementation
- [x] Dry Run
- [x] Time and Space Complexity
- [x] Iterative vs Recursive
- [x] Practice Questions

**Next Topic 12:** First and Last Occurrence of an Element in a Sorted Array
