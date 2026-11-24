# 14. Search in Rotated Sorted Array

## 1. Rotated Sorted Array Kya Hai?

Rotated Sorted Array ek aisa sorted array hota hai jisme elements ko kisi position se rotate kar diya jata hai.

Example – Original Sorted Array:

```cpp
{10, 20, 30, 40, 50, 60, 70}
```

Rotation ke baad:

```cpp
{40, 50, 60, 70, 10, 20, 30}
```

Array ab normal ascending order mein nahi hai, lekin iske do parts individually sorted hain.

## 2. Problem Statement

Humein ek rotated sorted array diya hota hai aur ek target element diya hota hai.

Humein target ka index find karna hota hai.

Example:

```cpp
int arr[] = {40, 50, 60, 70, 10, 20, 30};
int target = 20;
```

**Output:**

```text
Element found at index: 5
```

## 3. Normal Binary Search Kyun Work Nahi Karta?

Normal Binary Search complete sorted array par depend karta hai.

Rotated array mein complete array sorted nahi hota.

Isliye humein modified Binary Search use karna padta hai.

**Important:** Har step mein middle element ke basis par check karte hain ki left half sorted hai ya right half.

## 4. Search Karne Ka Logic

Initially:

```cpp
low = 0;
high = n - 1;
```

Har step mein:

```cpp
mid = low + (high - low) / 2;
```

### Case 1: Target Middle Element Hai

```cpp
if (arr[mid] == target)
```

Target mil gaya, `mid` return karo.

### Case 2: Left Half Sorted Hai

```cpp
if (arr[low] <= arr[mid])
```

Ab check karo target left half mein hai ya nahi:

```cpp
if (arr[low] <= target && target < arr[mid])
```

Agar hai toh:

```cpp
high = mid - 1;
```

Otherwise:

```cpp
low = mid + 1;
```

### Case 3: Right Half Sorted Hai

Agar left half sorted nahi hai, toh right half sorted hoga.

Check karo target right half mein hai ya nahi:

```cpp
if (arr[mid] < target && target <= arr[high])
```

Agar hai toh:

```cpp
low = mid + 1;
```

Otherwise:

```cpp
high = mid - 1;
```

## 5. C++ Implementation

Ye implementation distinct elements wale rotated sorted array ke liye hai.

```cpp
#include <iostream>
using namespace std;

int searchRotated(int arr[], int n, int target) {

    int low = 0;
    int high = n - 1;

    while (low <= high) {

        int mid = low + (high - low) / 2;

        // Target found
        if (arr[mid] == target) {
            return mid;
        }

        // Left half is sorted
        if (arr[low] <= arr[mid]) {

            if (arr[low] <= target && target < arr[mid]) {
                high = mid - 1;
            }
            else {
                low = mid + 1;
            }
        }

        // Right half is sorted
        else {

            if (arr[mid] < target && target <= arr[high]) {
                low = mid + 1;
            }
            else {
                high = mid - 1;
            }
        }
    }

    return -1;
}

int main() {

    int arr[] = {40, 50, 60, 70, 10, 20, 30};
    int n = 7;

    int target = 20;

    int result = searchRotated(arr, n, target);

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
Element found at index: 5
```

## 6. Dry Run

Array:

```cpp
arr = {40, 50, 60, 70, 10, 20, 30};
target = 20;
```

| Step | Low | High | Mid | arr[mid] |
| ---- | --: | ---: | --: | -------: |
| 1    |   0 |    6 |   3 |       70 |
| 2    |   4 |    6 |   5 |       20 |

Step 1:

- `arr[0] <= arr[3]`
- `40 <= 70`, so left half sorted hai.
- Target 20 left half mein nahi hai.
- `low = mid + 1 = 4`.

Step 2:

- `mid = 5`
- `arr[5] = 20`
- Target mil gaya.

**Answer: Index 5**

## 7. Time and Space Complexity

| Case            | Complexity |
| --------------- | ---------- |
| Best Time       | O(1)       |
| Average Time    | O(log n)   |
| Worst Time      | O(log n)   |
| Auxiliary Space | O(1)       |

Ye complexity distinct elements wale rotated sorted array ke liye hai.

## 8. Important Note: Duplicate Elements

Agar array mein duplicate elements present hain, toh kabhi-kabhi ye identify karna difficult ho sakta hai ki kaunsa half sorted hai.

Example:

```cpp
{2, 2, 2, 3, 4, 2}
```

Duplicates ke case mein modified logic ki zaroorat hoti hai. Worst-case time complexity O(n) tak ho sakti hai.

## 9. Common Mistakes

1. Rotated array par normal Binary Search use karna.
2. Left aur right sorted half identify na karna.
3. Target range check mein `<=` aur `<` conditions galat lagana.
4. `mid` calculate karne ka safe formula use na karna.
5. Element absent hone par `-1` return na karna.
6. Duplicate elements wale case ko distinct elements wale code se solve karne ki koshish karna.

## 10. Practice Questions

1. Rotated Sorted Array kya hota hai?
2. Normal Binary Search directly kyun work nahi karta?
3. Sorted left half kaise identify karte hain?
4. Agar left half sorted nahi hai toh kya assume karte hain?
5. Distinct elements ke case mein worst-case time complexity kya hai?
6. Duplicate elements hone par worst-case complexity kya ho sakti hai?

### Coding Practice

**Question 1:**

```cpp
int arr[] = {4, 5, 6, 7, 0, 1, 2};
int target = 0;
```

Target ka index find karo.

**Question 2:**

```cpp
int arr[] = {30, 40, 50, 10, 20};
int target = 50;
```

Target ka index find karo.

**Question 3:**

```cpp
int arr[] = {40, 50, 60, 10, 20, 30};
int target = 100;
```

Target absent hone par `-1` return karo.

## 11. Quick Revision

- Rotated Sorted Array ek sorted array ko rotate karke banta hai.
- Ismein do individually sorted halves ho sakte hain.
- Modified Binary Search use hota hai.
- Har step mein sorted half identify karte hain.
- Target sorted half mein ho toh usmein search karo.
- Otherwise doosre half mein search karo.
- Distinct elements: O(log n) time.
- Duplicate elements: Worst case O(n).
- Iterative Auxiliary Space: O(1).

## 12. Topic Status

- [x] Rotated Sorted Array Introduction
- [x] Problem Statement
- [x] Modified Binary Search Logic
- [x] C++ Implementation
- [x] Dry Run
- [x] Complexity Analysis
- [x] Duplicate Elements Note
- [x] Practice Questions

**Next Topic 15:** Find Minimum Element in Rotated Sorted Array
