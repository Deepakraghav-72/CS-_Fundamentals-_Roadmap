# 12. First and Last Occurrence of an Element in a Sorted Array

## 1. Introduction

Jab kisi sorted array mein same element multiple times present hota hai, toh humein us element ki:

1. First Occurrence – element ka sabse pehla index.
2. Last Occurrence – element ka sabse aakhri index.

find karna hota hai.

Is problem ko Binary Search ki help se solve kar sakte hain.

## 2. Example

```cpp
int arr[] = {10, 20, 20, 20, 30, 40, 50};
int target = 20;
```

Array mein `20` teen baar present hai.

- First Occurrence = Index 1
- Last Occurrence = Index 3

**Output:**

```text
First Occurrence: 1
Last Occurrence: 3
```

## 3. First Occurrence Ka Logic

Normal Binary Search mein element milne par hum index return kar dete hain.

Lekin First Occurrence ke liye element milne ke baad bhi left side mein search karna hota hai.

Logic:

- Agar `arr[mid] == target`, answer store karo.
- Phir left side mein search karo.
- Agar target chhota hai, left side mein search karo.
- Agar target bada hai, right side mein search karo.

### C++ Code – First Occurrence

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

int main() {

    int arr[] = {10, 20, 20, 20, 30, 40, 50};
    int n = 7;

    int target = 20;

    cout << "First Occurrence: "
         << firstOccurrence(arr, n, target);

    return 0;
}
```

**Output:**

```text
First Occurrence: 1
```

## 4. Last Occurrence Ka Logic

Last Occurrence find karne ke liye element milne ke baad right side mein search karte hain.

Logic:

- Agar `arr[mid] == target`, answer store karo.
- Phir right side mein search karo.
- Agar target chhota hai, left side mein search karo.
- Agar target bada hai, right side mein search karo.

### C++ Code – Last Occurrence

```cpp
#include <iostream>
using namespace std;

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

int main() {

    int arr[] = {10, 20, 20, 20, 30, 40, 50};
    int n = 7;

    int target = 20;

    cout << "Last Occurrence: "
         << lastOccurrence(arr, n, target);

    return 0;
}
```

**Output:**

```text
Last Occurrence: 3
```

## 5. First and Last Occurrence Together

Dono functions ko ek hi program mein use kar sakte hain.

```cpp
#include <iostream>
using namespace std;

int firstOccurrence(int arr[], int n, int target) {

    int low = 0, high = n - 1;
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

    int low = 0, high = n - 1;
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

int main() {

    int arr[] = {10, 20, 20, 20, 30, 40, 50};
    int n = 7;

    int target = 20;

    cout << "First Occurrence: "
         << firstOccurrence(arr, n, target) << endl;

    cout << "Last Occurrence: "
         << lastOccurrence(arr, n, target) << endl;

    return 0;
}
```

**Output:**

```text
First Occurrence: 1
Last Occurrence: 3
```

## 6. Total Number of Occurrences

Agar first aur last occurrence mil jaye, toh total frequency calculate kar sakte hain.

**Formula:**

```cpp
frequency = last - first + 1;
```

Example:

```cpp
first = 1;
last = 3;

frequency = 3 - 1 + 1;
// 3
```

**Output:**

```text
Total Occurrences: 3
```

Agar element nahi milta aur dono indexes `-1` hain, toh frequency `0` honi chahiye.

## 7. Time and Space Complexity

| Operation         | Time Complexity |
| ----------------- | --------------- |
| First Occurrence  | O(log n)        |
| Last Occurrence   | O(log n)        |
| Total Occurrences | O(log n)        |

**Auxiliary Space Complexity:** O(1)

Dono searches iterative Binary Search use karte hain, isliye extra space constant hoti hai.

## 8. Common Mistakes

1. Array sorted hona chahiye.
2. First occurrence mein `high = mid - 1` karna hai.
3. Last occurrence mein `low = mid + 1` karna hai.
4. `ans = -1` se initialize karna na bhoolen.
5. Frequency calculate karne se pehle check karo ki element mila hai ya nahi.
6. Index aur element value ko confuse mat karo.

## 9. Practice Questions

1. First Occurrence kya hoti hai?
2. Last Occurrence kya hoti hai?
3. First occurrence ke liye element milne par kis taraf search karte hain?
4. Last occurrence ke liye kis taraf search karte hain?
5. Total frequency ka formula kya hai?
6. Dono searches ki time complexity kya hai?

### Coding Practice

**Question 1:**

```cpp
int arr[] = {1, 2, 2, 2, 3, 4, 5};
int target = 2;
```

First aur last occurrence find karo.

**Question 2:**

```cpp
int arr[] = {5, 5, 5, 5, 10, 20};
int target = 5;
```

Total occurrences find karo.

**Question 3:**

```cpp
int arr[] = {10, 20, 30, 40, 50};
int target = 25;
```

Element absent hone par `-1` return karo.

## 10. Quick Revision

- First Occurrence = Element ka pehla index.
- Last Occurrence = Element ka aakhri index.
- First occurrence mein match milne par `high = mid - 1`.
- Last occurrence mein match milne par `low = mid + 1`.
- Total Frequency = `last - first + 1`.
- Element absent ho toh first aur last dono `-1`.
- Time Complexity = O(log n).
- Auxiliary Space = O(1).
- Array sorted hona compulsory hai.

## 11. Topic Status

- [x] First Occurrence
- [x] Last Occurrence
- [x] Binary Search Logic
- [x] C++ Implementation
- [x] Total Frequency
- [x] Complexity Analysis
- [x] Practice Questions

**Next Topic 13:** Count Occurrences of an Element in a Sorted Array
