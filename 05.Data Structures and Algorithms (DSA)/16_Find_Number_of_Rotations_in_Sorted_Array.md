# 16. Find Number of Rotations in a Sorted Array

## 1. Introduction

Jab hum kisi sorted array ko rotate karte hain, toh uske elements ki positions change ho jaati hain.

Humein find karna hota hai ki array ko kitni positions rotate kiya gaya hai.

Example:

Original Sorted Array:

```cpp
{10, 20, 30, 40, 50, 60}
```

Rotated Array:

```cpp
{40, 50, 60, 10, 20, 30}
```

Yahan array ko **3 positions right rotate** kiya gaya hai.

**Output:**

```text
Number of Rotations: 3
```

## 2. Important Concept

Rotated Sorted Array mein minimum element jis index par present hota hai, wahi number of rotations hota hai.

Example:

```cpp
arr = {40, 50, 60, 10, 20, 30};
```

Minimum element = `10`

Minimum element ka index = `3`

Therefore:

```cpp
Number of Rotations = 3;
```

**Note:** Yahan rotation ka matlab right rotation hai. Left rotation count ke liye formula alag hoga.

## 3. Binary Search Ka Logic

Hum previous topic mein minimum element ka index find karna seekh chuke hain.

Usi logic ka use karke number of rotations find kar sakte hain.

Initially:

```cpp
low = 0;
high = n - 1;
```

Middle index:

```cpp
mid = low + (high - low) / 2;
```

Conditions:

### Case 1: Left Half Unsorted Hai

```cpp
if (arr[mid] > arr[high])
```

Minimum element right half mein hoga.

```cpp
low = mid + 1;
```

### Case 2: Right Half Sorted Hai

```cpp
else
```

Minimum element middle ya left half mein hoga.

```cpp
high = mid;
```

Jab `low == high` ho jayega, wahi minimum element ka index aur number of right rotations hoga.

## 4. C++ Implementation

```cpp
#include <iostream>
using namespace std;

int countRotations(int arr[], int n) {

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

    int arr[] = {40, 50, 60, 10, 20, 30};
    int n = 6;

    cout << "Number of Rotations: "
         << countRotations(arr, n);

    return 0;
}
```

**Output:**

```text
Number of Rotations: 3
```

## 5. Dry Run

Array:

```cpp
arr = {40, 50, 60, 10, 20, 30};
```

| Step | Low | High | Mid | arr[mid] | Comparison |
| ---- | --: | ---: | --: | -------: | ---------- |
| 1    |   0 |    5 |   2 |       60 | 60 > 30    |
| 2    |   3 |    5 |   4 |       20 | 20 <= 30   |
| 3    |   3 |    4 |   3 |       10 | 10 <= 20   |

Step 1:

- `60 > 30`
- Minimum element right side mein hai.
- `low = 3`

Step 2:

- `20 <= 30`
- Minimum element middle ya left side mein hai.
- `high = 4`

Step 3:

- `10 <= 20`
- `high = 3`

Now:

```cpp
low = 3;
high = 3;
```

Therefore:

```cpp
Number of Rotations = 3;
```

## 6. Already Sorted Array

Example:

```cpp
int arr[] = {10, 20, 30, 40, 50};
```

Is array ko rotate nahi kiya gaya hai.

Minimum element index = `0`

**Output:**

```text
Number of Rotations: 0
```

## 7. Left Rotation vs Right Rotation

| Rotation Type  | Example                    | Count |
| -------------- | -------------------------- | ----: |
| Right Rotation | `{40, 50, 60, 10, 20, 30}` |     3 |
| Left Rotation  | `{40, 50, 60, 10, 20, 30}` |     3 |

Dono examples mein same array ban sakta hai, lekin original array aur direction ko samajhna zaroori hai.

Agar array length `n` hai aur right rotations `k` hain, toh equivalent left rotations:

```cpp
leftRotations = (n - k) % n;
```

Example:

```cpp
n = 6;
k = 3;

leftRotations = (6 - 3) % 6;
// 3
```

## 8. Time and Space Complexity

| Case            | Complexity |
| --------------- | ---------- |
| Best Time       | O(1)       |
| Average Time    | O(log n)   |
| Worst Time      | O(log n)   |
| Auxiliary Space | O(1)       |

Ye complexity distinct elements wale rotated sorted array ke liye hai.

**Duplicates:** Duplicate elements ke case mein worst-case time O(n) ho sakta hai.

## 9. Common Mistakes

1. Minimum element ki value ko rotation count samajhna.
2. Minimum element ka index find karna bhool jana.
3. `high = mid` ki jagah galat update karna.
4. Already sorted array mein answer `0` hota hai.
5. Right aur left rotation ko confuse karna.
6. Duplicate elements ke case mein same complexity assume karna.

## 10. Practice Questions

1. Number of Rotations ka kya meaning hai?
2. Minimum element ka index rotation count kaise batata hai?
3. Already sorted array mein rotations kitni hoti hain?
4. `low < high` condition kyun use karte hain?
5. Distinct elements ke case mein time complexity kya hai?

### Coding Practice

**Question 1:**

```cpp
int arr[] = {4, 5, 6, 7, 0, 1, 2};
```

Number of rotations find karo.

**Question 2:**

```cpp
int arr[] = {30, 40, 50, 10, 20};
```

Number of rotations find karo.

**Question 3:**

```cpp
int arr[] = {10, 20, 30, 40, 50};
```

Already sorted array ka rotation count find karo.

## 11. Quick Revision

- Rotated Sorted Array mein rotation count find karte hain.
- Minimum element ka index = Right Rotation Count.
- Binary Search use hota hai.
- `arr[mid] > arr[high]` ho toh `low = mid + 1`.
- Otherwise `high = mid`.
- Loop condition = `low < high`.
- Answer = `low`.
- Time Complexity = O(log n), distinct elements ke liye.
- Auxiliary Space = O(1).

## 12. Topic Status

- [x] Number of Rotations Introduction
- [x] Minimum Index Concept
- [x] Binary Search Logic
- [x] C++ Implementation
- [x] Dry Run
- [x] Left vs Right Rotation
- [x] Complexity Analysis
- [x] Practice Questions

**Next Topic 17:** Peak Element in an Array
