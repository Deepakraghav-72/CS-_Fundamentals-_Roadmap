# Topic 24: Maximum Subarray Sum (Kadane's Algorithm)

## 1. Subarray Kya Hota Hai?

Subarray array ke continuous elements ka group hota hai.

**Example:**

```cpp
arr[] = {2, 4, 6, 8};
```

Valid subarrays:

```text
{2}
{2, 4}
{4, 6}
{6, 8}
{2, 4, 6}
{4, 6, 8}
```

Invalid subarray:

```text
{2, 6}
```

Reason: Subarray mein elements continuous hone chahiye.

## 2. Maximum Subarray Sum Kya Hai?

Is problem mein humein ek integer array diya hota hai.

Humein aisa continuous subarray find karna hai jiska sum maximum ho.

**Example:**

```cpp
arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
```

Maximum sum wala subarray:

```text
{4, -1, 2, 1}
```

Sum:

```text
4 + (-1) + 2 + 1 = 6
```

**Output:**

```text
Maximum Subarray Sum = 6
```

## 3. Approach 1: Brute Force

Is approach mein hum saare possible subarrays ka sum calculate karenge.

### Algorithm

1. Ek outer loop se subarray ka starting index select karo.
2. Inner loop se ending index select karo.
3. Subarray ke elements ka sum calculate karo.
4. Maximum sum update karo.
5. Final maximum sum return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits>
using namespace std;

int maxSubArray(vector<int>& arr) {

    int n = arr.size();
    int maxSum = INT_MIN;

    for (int i = 0; i < n; i++) {

        int sum = 0;

        for (int j = i; j < n; j++) {

            sum += arr[j];

            maxSum = max(maxSum, sum);
        }
    }

    return maxSum;
}

int main() {

    vector<int> arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};

    cout << "Maximum Subarray Sum: "
         << maxSubArray(arr);

    return 0;
}
```

**Output:**

```text
Maximum Subarray Sum: 6
```

### Complexity

- Time Complexity: O(n²)
- Auxiliary Space: O(1)

## 4. Approach 2: Kadane's Algorithm (Optimized)

Kadane's Algorithm maximum subarray sum find karne ka optimized algorithm hai.

Ismein hum array ko sirf ek baar traverse karte hain.

### Main Logic

Hum do variables maintain karte hain:

1. `currentSum`: Current subarray ka sum.
2. `maxSum`: Ab tak ka maximum subarray sum.

Har element par:

- Current element ko `currentSum` mein add karo.
- `maxSum` update karo.
- Agar `currentSum` negative ho jaye, toh use 0 kar do, taaki next subarray fresh start kar sake.

### Algorithm

1. `currentSum = 0` initialize karo.
2. `maxSum = INT_MIN` initialize karo.
3. Array traverse karo.
4. Current element ko `currentSum` mein add karo.
5. `maxSum = max(maxSum, currentSum)` update karo.
6. Agar `currentSum < 0` ho, toh `currentSum = 0` kar do.
7. Finally `maxSum` return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits>
using namespace std;

int maxSubArray(vector<int>& arr) {

    int currentSum = 0;
    int maxSum = INT_MIN;

    for (int i = 0; i < arr.size(); i++) {

        currentSum += arr[i];

        maxSum = max(maxSum, currentSum);

        if (currentSum < 0) {
            currentSum = 0;
        }
    }

    return maxSum;
}

int main() {

    vector<int> arr = {-2, 1, -3, 4, -1, 2, 1, -5, 4};

    cout << "Maximum Subarray Sum: "
         << maxSubArray(arr);

    return 0;
}
```

**Output:**

```text
Maximum Subarray Sum: 6
```

## 5. Dry Run

Array:

```cpp
arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
```

Initial values:

```cpp
currentSum = 0;
maxSum = INT_MIN;
```

| Element | currentSum | maxSum | Action                |
| ------: | ---------: | -----: | --------------------- |
|      -2 |         -2 |     -2 | Reset currentSum to 0 |
|       1 |          1 |      1 | Continue              |
|      -3 |         -2 |      1 | Reset currentSum to 0 |
|       4 |          4 |      4 | Continue              |
|      -1 |          3 |      4 | Continue              |
|       2 |          5 |      5 | Continue              |
|       1 |          6 |      6 | Continue              |
|      -5 |          1 |      6 | Continue              |
|       4 |          5 |      6 | Continue              |

Final Answer:

```text
Maximum Subarray Sum = 6
```

## 6. Important: All Negative Elements

Example:

```cpp
arr[] = {-5, -2, -8, -1};
```

Maximum subarray sum = `-1`.

**Important:** Agar hum `maxSum = 0` initialize karenge, toh all-negative array ke liye wrong answer milega.

Isliye:

```cpp
int maxSum = INT_MIN;
```

use karna important hai.

## 7. Time and Space Complexity

| Approach           | Time Complexity | Auxiliary Space |
| ------------------ | --------------- | --------------- |
| Brute Force        | O(n²)           | O(1)            |
| Kadane's Algorithm | O(n)            | O(1)            |

Kadane's Algorithm optimal approach hai.

## 8. Common Mistakes

1. `maxSum` ko 0 initialize karna.
2. All-negative array handle na karna.
3. Subarray aur subsequence mein confusion karna.
4. Maximum sum update karne se pehle `currentSum` reset karna.
5. Empty array handle na karna.
6. Continuous elements ki condition bhool jana.

## 9. Practice Questions

1. `{1, 2, 3, 4}` ka maximum subarray sum find karo.
2. `{-5, -2, -8, -1}` solve karo.
3. `{5, -2, 3, 4}` solve karo.
4. `{-2, 1, -3, 4, -1, 2, 1}` solve karo.
5. Maximum sum ke saath subarray ke starting aur ending indices bhi find karo.

## 10. Quick Revision

- Subarray = Continuous elements ka group.
- Goal = Maximum Subarray Sum find karna.
- Brute Force: O(n²).
- Kadane's Algorithm: O(n).
- `currentSum` current subarray ka sum maintain karta hai.
- `maxSum` maximum sum maintain karta hai.
- Negative `currentSum` ko reset karte hain.
- `maxSum = INT_MIN` all-negative arrays ke liye important hai.
- Auxiliary Space = O(1).

## 11. Topic Completion Checklist

- [ ] Subarray samajh liya.
- [ ] Maximum Subarray Sum problem samajh li.
- [ ] Brute Force approach samajh li.
- [ ] Kadane's Algorithm samajh li.
- [ ] All-negative array ka case samajh liya.
- [ ] C++ code run kar liya.
- [ ] Dry Run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 25: Maximum Product Subarray**
