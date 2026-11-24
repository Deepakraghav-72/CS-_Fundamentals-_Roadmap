# 15. Find Minimum Element in Rotated Sorted Array

## 1. Introduction

Rotated Sorted Array mein minimum element find karna hota hai.

Example:

Original Sorted Array:

```cpp
{10, 20, 30, 40, 50, 60, 70}
```

Rotated Array:

```cpp
{40, 50, 60, 70, 10, 20, 30}
```

Is array mein minimum element `10` hai.

**Output:**

```text
Minimum Element: 10
```

## 2. Problem Statement

Humein ek rotated sorted array diya hota hai.

Humein usmein minimum value find karni hoti hai.

**Important:** Is topic mein hum distinct elements wale rotated sorted array ko consider kar rahe hain.

## 3. Binary Search Ka Logic

Initially:

```cpp
low = 0;
high = n - 1;
```

Har step mein middle index calculate karenge:

```cpp
mid = low + (high - low) / 2;
```

Ab `arr[mid]` ko `arr[high]` se compare karenge.

### Case 1: Middle Element Greater Than Last Element

```cpp
if (arr[mid] > arr[high])
```

Minimum element right side mein hoga.

```cpp
low = mid + 1;
```

### Case 2: Middle Element Less Than or Equal to Last Element

```cpp
else
```

Minimum element middle position ya left side mein ho sakta hai.

```cpp
high = mid;
```

### Loop Condition

```cpp
while (low < high)
```

Jab `low == high` ho jayega, wahi minimum element ka index hoga.

## 4. C++ Implementation

```cpp
#include <iostream>
using namespace std;

int findMinimum(int arr[], int n) {

    int low = 0;
    int high = n - 1;

    while (low < high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] > arr[high]) {
            low = mid + 1;
        }
        else {
            high = mid;
        }
    }

    return arr[low];
}

int main() {

    int arr[] = {40, 50, 60, 70, 10, 20, 30};
    int n = 7;

    cout << "Minimum Element: "
         << findMinimum(arr, n);

    return 0;
}
```

**Output:**

```text
Minimum Element: 10
```

## 5. Dry Run

Array:

```cpp
arr = {40, 50, 60, 70, 10, 20, 30};
```

| Step | Low | High | Mid | arr[mid] | Comparison |
| ---- | --: | ---: | --: | -------: | ---------- |
| 1    |   0 |    6 |   3 |       70 | 70 > 30    |
| 2    |   4 |    6 |   5 |       20 | 20 <= 30   |
| 3    |   4 |    5 |   4 |       10 | 10 <= 20   |

Step 1:

- `70 > 30`
- Minimum right side mein hai.
- `low = 4`

Step 2:

- `20 <= 30`
- Minimum middle ya left side mein hai.
- `high = 5`

Step 3:

- `10 <= 20`
- `high = 4`

Ab:

```cpp
low = 4;
high = 4;
```

Minimum element:

```cpp
arr[4] = 10;
```

**Answer: 10**

## 6. Agar Array Rotate Nahi Hua Ho?

Example:

```cpp
int arr[] = {10, 20, 30, 40, 50};
```

Ye already sorted array hai.

Algorithm ke according minimum element first position par milega.

**Output:**

```text
Minimum Element: 10
```

## 7. Minimum Element Ka Index Find Karna

Agar value ki jagah index chahiye, toh function mein:

```cpp
return arr[low];
```

ki jagah:

```cpp
return low;
```

use karo.

Example:

```cpp
int index = findMinimumIndex(arr, n);
```

Result:

```text
Minimum Element Index: 4
```

## 8. C++ Code – Minimum Index

```cpp
#include <iostream>
using namespace std;

int findMinimumIndex(int arr[], int n) {

    int low = 0;
    int high = n - 1;

    while (low < high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] > arr[high]) {
            low = mid + 1;
        }
        else {
            high = mid;
        }
    }

    return low;
}

int main() {

    int arr[] = {40, 50, 60, 70, 10, 20, 30};
    int n = 7;

    int index = findMinimumIndex(arr, n);

    cout << "Minimum Element: " << arr[index] << endl;
    cout << "Minimum Element Index: " << index;

    return 0;
}
```

**Output:**

```text
Minimum Element: 10
Minimum Element Index: 4
```

## 9. Time and Space Complexity

| Case            | Complexity |
| --------------- | ---------- |
| Best Time       | O(1)       |
| Average Time    | O(log n)   |
| Worst Time      | O(log n)   |
| Auxiliary Space | O(1)       |

Ye complexity distinct elements wale rotated sorted array ke liye hai.

**Duplicate elements:** Duplicates hone par worst-case time complexity O(n) tak ja sakti hai.

## 10. Common Mistakes

1. `while (low < high)` ki jagah galat loop condition use karna.
2. `high = mid` ki jagah `high = mid - 1` karna. Is algorithm mein `mid` minimum ho sakta hai, isliye use range mein rakhna zaroori hai.
3. `arr[mid]` ko `arr[high]` se compare karne ke bajay galat element compare karna.
4. Minimum value aur minimum index ko confuse karna.
5. Empty array par function call karna. Is code mein non-empty array required hai.
6. Duplicate elements ke liye distinct-element algorithm ko bina modification use karna.

## 11. Practice Questions

1. Rotated Sorted Array kya hota hai?
2. Minimum element find karne ke liye Binary Search kyun use karte hain?
3. `arr[mid] > arr[high]` hone par kya karenge?
4. `arr[mid] <= arr[high]` hone par kya karenge?
5. Loop `low == high` hone par kyun stop hota hai?
6. Distinct elements ke case mein time complexity kya hai?

### Coding Practice

**Question 1:**

```cpp
int arr[] = {4, 5, 6, 7, 0, 1, 2};
```

Minimum element find karo.

**Question 2:**

```cpp
int arr[] = {30, 40, 50, 10, 20};
```

Minimum element ka index find karo.

**Question 3:**

```cpp
int arr[] = {10, 20, 30, 40, 50};
```

Already sorted array mein minimum element find karo.

## 12. Quick Revision

- Rotated Sorted Array mein minimum element find karna hota hai.
- Modified Binary Search use hota hai.
- `mid` ko `high` se compare karte hain.
- Agar `arr[mid] > arr[high]`, toh `low = mid + 1`.
- Otherwise `high = mid`.
- Loop condition: `low < high`.
- Minimum index = `low`.
- Minimum value = `arr[low]`.
- Time Complexity = O(log n), distinct elements ke liye.
- Auxiliary Space = O(1).

## 13. Topic Status

- [x] Minimum Element Introduction
- [x] Binary Search Logic
- [x] C++ Implementation
- [x] Dry Run
- [x] Minimum Index
- [x] Complexity Analysis
- [x] Common Mistakes
- [x] Practice Questions

**Next Topic 16:** Find the Number of Rotations in a Rotated Sorted Array
