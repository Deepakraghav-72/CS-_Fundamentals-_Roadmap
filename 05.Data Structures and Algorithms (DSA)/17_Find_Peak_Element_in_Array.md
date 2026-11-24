# 17. Find Peak Element in an Array

## 1. Peak Element Kya Hai?

Peak Element woh element hota hai jo apne neighbouring elements se bada hota hai.

Example:

```cpp
int arr[] = {1, 3, 5, 4, 2};
```

Yahan `5` peak element hai, kyunki:

- 5 > 3
- 5 > 4

**Output:**

```text
Peak Element: 5
Peak Index: 2
```

## 2. Important Conditions

Peak element ke liye:

- `arr[i] > arr[i-1]`
- `arr[i] > arr[i+1]`

First aur last element ke liye missing neighbour ko negative infinity ki tarah consider karte hain.

Example:

```cpp
{10, 5, 3, 2}
```

Yahan first element `10` peak hai.

**Note:** Is topic mein adjacent elements equal nahi hain. Multiple peaks ho sakte hain; humein koi ek peak find karna hai.

## 3. Linear Search Method

Sabse simple method Linear Search hai.

Har element ko uske neighbours se compare karenge.

```cpp
#include <iostream>
using namespace std;

int findPeak(int arr[], int n) {

    for (int i = 0; i < n; i++) {

        bool left = (i == 0 || arr[i] > arr[i - 1]);
        bool right = (i == n - 1 || arr[i] > arr[i + 1]);

        if (left && right) {
            return i;
        }
    }

    return -1;
}

int main() {

    int arr[] = {1, 3, 5, 4, 2};
    int n = 5;

    int index = findPeak(arr, n);

    if (index != -1) {
        cout << "Peak Element: " << arr[index] << endl;
        cout << "Peak Index: " << index;
    }

    return 0;
}
```

**Output:**

```text
Peak Element: 5
Peak Index: 2
```

**Time Complexity:** O(n)

**Auxiliary Space:** O(1)

## 4. Binary Search Method

Peak Element ko Binary Search se bhi find kar sakte hain.

Is method mein array ka sorted hona zaroori nahi hai.

### Logic

Initially:

```cpp
low = 0;
high = n - 1;
```

Middle index:

```cpp
mid = low + (high - low) / 2;
```

Ab `arr[mid]` aur `arr[mid + 1]` compare karenge.

### Case 1: Right Neighbour Bada Hai

```cpp
if (arr[mid] < arr[mid + 1])
```

Matlab right side mein upward slope hai.

Isliye peak right side mein zaroor milega.

```cpp
low = mid + 1;
```

### Case 2: Middle Element Right Neighbour Se Bada Hai

```cpp
else
```

Matlab peak middle position ya left side mein milega.

```cpp
high = mid;
```

Jab `low == high` ho jayega, wahi peak element ka index hoga.

## 5. Binary Search C++ Implementation

```cpp
#include <iostream>
using namespace std;

int findPeak(int arr[], int n) {

    int low = 0;
    int high = n - 1;

    while (low < high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] < arr[mid + 1]) {
            low = mid + 1;
        }
        else {
            high = mid;
        }
    }

    return low;
}

int main() {

    int arr[] = {1, 3, 5, 4, 2};
    int n = 5;

    int index = findPeak(arr, n);

    cout << "Peak Element: " << arr[index] << endl;
    cout << "Peak Index: " << index;

    return 0;
}
```

**Output:**

```text
Peak Element: 5
Peak Index: 2
```

## 6. Dry Run

Array:

```cpp
arr = {1, 3, 5, 4, 2};
```

| Step | Low | High | Mid | arr[mid] | arr[mid+1] |
| ---- | --: | ---: | --: | -------: | ---------: |
| 1    |   0 |    4 |   2 |        5 |          4 |
| 2    |   0 |    2 |   1 |        3 |          5 |
| 3    |   2 |    2 |   - |        - |          - |

Step 1:

- `5 > 4`
- Peak middle ya left side mein hai.
- `high = 2`

Step 2:

- `3 < 5`
- Peak right side mein hai.
- `low = 2`

Now:

```cpp
low = 2;
high = 2;
```

Peak element:

```cpp
arr[2] = 5;
```

**Answer: 5**

## 7. Linear Search vs Binary Search

| Feature         | Linear Search      | Binary Search     |
| --------------- | ------------------ | ----------------- |
| Method          | One by one check   | Search range half |
| Time Complexity | O(n)               | O(log n)          |
| Auxiliary Space | O(1)               | O(1)              |
| Sorted Array    | Required nahi      | Required nahi     |
| Efficiency      | Comparatively slow | Faster            |

## 8. Time and Space Complexity

| Method        | Best Case | Worst Case |
| ------------- | --------- | ---------- |
| Linear Search | O(1)      | O(n)       |
| Binary Search | O(1)      | O(log n)   |

Binary Search method ki Auxiliary Space Complexity O(1) hai.

## 9. Common Mistakes

1. Peak element ko sirf maximum element samajhna. Peak local maximum hota hai.
2. `arr[mid + 1]` access karne se pehle loop condition `low < high` use karna.
3. `low = mid` karne se infinite loop ho sakta hai. Yahan `mid + 1` use karo.
4. `high = mid - 1` karna. Is algorithm mein `mid` khud peak ho sakta hai.
5. Ye assume karna ki array sorted hona chahiye. Peak Element ke liye sorted array required nahi hai.
6. Multiple peaks hone par sirf ek hi answer possible hai, aisa samajhna.

## 10. Practice Questions

1. Peak Element kya hota hai?
2. Peak aur global maximum mein kya difference hai?
3. Kya Peak Element find karne ke liye sorted array required hai?
4. Binary Search mein `arr[mid] < arr[mid + 1]` hone par kya karenge?
5. Binary Search ki worst-case time complexity kya hai?

### Coding Practice

**Question 1:**

```cpp
int arr[] = {1, 2, 3, 1};
```

Peak element aur uska index find karo.

**Question 2:**

```cpp
int arr[] = {5, 4, 3, 2, 1};
```

Peak element find karo.

**Question 3:**

```cpp
int arr[] = {1, 2, 1, 3, 5, 6, 4};
```

Koi ek peak element find karo.

## 11. Quick Revision

- Peak Element apne adjacent elements se bada hota hai.
- Array ka sorted hona compulsory nahi hai.
- Linear Search se O(n) time lagta hai.
- Binary Search se O(log n) time lagta hai.
- `arr[mid] < arr[mid + 1]` ho toh right side jao.
- Otherwise left side ya middle mein search karo.
- Loop condition = `low < high`.
- Final peak index = `low`.
- Auxiliary Space = O(1).

## 12. Topic Status

- [x] Peak Element Introduction
- [x] Peak Conditions
- [x] Linear Search Method
- [x] Binary Search Method
- [x] C++ Implementation
- [x] Dry Run
- [x] Complexity Analysis
- [x] Practice Questions

**Next Topic 18:** Search in a Nearly Sorted Array
