# 13. Count Occurrences of an Element in a Sorted Array

## 1. Introduction

Count Occurrences ka matlab hai kisi array mein ek particular element kitni baar present hai, ye find karna.

Example:

```cpp
int arr[] = {10, 20, 20, 20, 30, 40, 50};
int target = 20;
```

Yahan `20` total 3 baar present hai.

**Output:**

```text
Occurrences: 3
```

## 2. Count Occurrences Using Binary Search

Sorted array mein occurrences count karne ke liye hum First Occurrence aur Last Occurrence find kar sakte hain.

**Formula:**

```cpp
count = lastOccurrence - firstOccurrence + 1;
```

Example:

```cpp
firstOccurrence = 1;
lastOccurrence = 3;

count = 3 - 1 + 1;
// 3
```

Agar element nahi milta, toh count `0` hoga.

## 3. C++ Implementation

```cpp
#include <iostream>
using namespace std;

int firstOccurrence(int arr[], int n, int target) {

    int low = 0;
    int high = n - 1;
    int ans = -1;

    while (low <= high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] == target) {
            ans = mid;
            high = mid - 1;
        }
        else if (target < arr[mid]) {
            high = mid - 1;
        }
        else {
            low = mid + 1;
        }
    }

    return ans;
}

int lastOccurrence(int arr[], int n, int target) {

    int low = 0;
    int high = n - 1;
    int ans = -1;

    while (low <= high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] == target) {
            ans = mid;
            low = mid + 1;
        }
        else if (target < arr[mid]) {
            high = mid - 1;
        }
        else {
            low = mid + 1;
        }
    }

    return ans;
}

int countOccurrences(int arr[], int n, int target) {

    int first = firstOccurrence(arr, n, target);

    if (first == -1) {
        return 0;
    }

    int last = lastOccurrence(arr, n, target);

    return last - first + 1;
}

int main() {

    int arr[] = {10, 20, 20, 20, 30, 40, 50};
    int n = 7;

    int target = 20;

    cout << "Occurrences: "
         << countOccurrences(arr, n, target);

    return 0;
}
```

**Output:**

```text
Occurrences: 3
```

## 4. Dry Run

Array:

```cpp
arr = {10, 20, 20, 20, 30, 40, 50};
target = 20;
```

First Occurrence:

```text
Index = 1
```

Last Occurrence:

```text
Index = 3
```

Formula:

```cpp
count = last - first + 1;

count = 3 - 1 + 1;

count = 3;
```

**Final Answer: 3**

## 5. Count Occurrences Using STL

C++ STL mein `equal_range()` bhi use kar sakte hain.

Ye sorted range mein target element ki first position aur uske baad wali position return karta hai.

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main() {

    int arr[] = {10, 20, 20, 20, 30, 40, 50};
    int n = 7;

    int target = 20;

    auto range = equal_range(arr, arr + n, target);

    int count = range.second - range.first;

    cout << "Occurrences: " << count;

    return 0;
}
```

**Output:**

```text
Occurrences: 3
```

`equal_range()` sorted range par use hota hai.

## 6. Time and Space Complexity

| Method                     | Time Complexity | Auxiliary Space |
| -------------------------- | --------------- | --------------- |
| Linear Counting            | O(n)            | O(1)            |
| First + Last Binary Search | O(log n)        | O(1)            |
| STL `equal_range()`        | O(log n)        | O(1)            |

Binary Search method large sorted arrays ke liye efficient hai.

## 7. Common Mistakes

1. Binary Search ke liye sorted array zaroori hai.
2. Frequency formula mein `+1` lagana mat bhoolna.
3. Element absent ho toh `0` return karna hai.
4. `first == -1` check kiye bina formula calculate mat karo.
5. Index aur element value ko confuse mat karo.
6. `equal_range()` use karte waqt `<algorithm>` header include karo.

## 8. Practice Questions

1. Count Occurrences ka kya meaning hai?
2. First aur Last Occurrence ka use kyun karte hain?
3. Frequency calculate karne ka formula kya hai?
4. Element absent ho toh count kya hoga?
5. Binary Search se counting ki time complexity kya hai?
6. C++ STL ka `equal_range()` kya karta hai?

### Coding Practice

**Question 1:**

```cpp
int arr[] = {1, 2, 2, 2, 3, 4, 5};
int target = 2;
```

Occurrences count karo.

**Question 2:**

```cpp
int arr[] = {5, 5, 5, 5, 10, 20};
int target = 5;
```

Occurrences count karo.

**Question 3:**

```cpp
int arr[] = {10, 20, 30, 40, 50};
int target = 25;
```

Element absent hone par `0` return karo.

## 9. Quick Revision

- Count Occurrences = Element kitni baar present hai.
- Sorted array par Binary Search use kar sakte hain.
- First Occurrence = Pehla index.
- Last Occurrence = Aakhri index.
- Formula = `last - first + 1`.
- Element absent ho toh answer `0`.
- Binary Search Time Complexity = O(log n).
- Auxiliary Space = O(1).

## 10. Topic Status

- [x] Count Occurrences Introduction
- [x] First and Last Occurrence Logic
- [x] C++ Implementation
- [x] Dry Run
- [x] STL `equal_range()`
- [x] Time and Space Complexity
- [x] Practice Questions

**Next Topic 14:** Search in Rotated Sorted Array
