# Topic 22: Two Sum Problem

## 1. Two Sum Problem Kya Hai?

Two Sum ek popular Array problem hai.

Is problem mein humein:

- Ek integer array diya hota hai.
- Ek target value di hoti hai.
- Humein array ke do aise elements find karne hote hain jinka sum target ke equal ho.

**Example:**

```cpp
arr[] = {2, 7, 11, 15};
target = 9;
```

Yahan:

```text
2 + 7 = 9
```

Answer:

```text
Index = 0, 1
```

## 2. Important Conditions

- Dono elements different indices par hone chahiye.
- Ek hi element ko do baar use nahi kar sakte.
- Array sorted ya unsorted dono ho sakta hai.
- Problem ke according indices ya values return karni hoti hain.

## 3. Approach 1: Brute Force

Is approach mein hum har element ko baaki elements ke saath check karenge.

### Algorithm

1. Outer loop se first element select karo.
2. Inner loop se uske baad ke elements select karo.
3. Dono elements ka sum calculate karo.
4. Agar sum target ke equal hai toh answer return karo.
5. Agar koi pair nahi milta toh `{-1, -1}` return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<int> twoSum(vector<int>& arr, int target) {

    int n = arr.size();

    for (int i = 0; i < n; i++) {

        for (int j = i + 1; j < n; j++) {

            if (arr[i] + arr[j] == target) {
                return {i, j};
            }
        }
    }

    return {-1, -1};
}

int main() {

    vector<int> arr = {2, 7, 11, 15};

    int target = 9;

    vector<int> ans = twoSum(arr, target);

    cout << "Indices: "
         << ans[0] << ", " << ans[1];

    return 0;
}
```

**Output:**

```text
Indices: 0, 1
```

### Complexity

- Time Complexity: O(n²)
- Auxiliary Space: O(1) (answer storage ko exclude karke).

## 4. Approach 2: Hashing (Optimized)

Hashing approach mein hum `unordered_map` ka use karte hain.

### Main Logic

Humein target ke equal sum banane ke liye har element ka required partner find karna hai.

**Formula:**

```cpp
required = target - arr[i];
```

Example:

```text
arr = {2, 7, 11, 15}
target = 9
```

First element = 2

```text
required = 9 - 2
required = 7
```

Agar 7 pehle se map mein present hai, toh pair mil gaya.

### Algorithm

1. Ek empty `unordered_map` banao.
2. Array ko left se right traverse karo.
3. Current element ke liye `required = target - arr[i]` calculate karo.
4. Check karo required element map mein present hai ya nahi.
5. Present hai toh dono indices return karo.
6. Nahi hai toh current element aur uska index map mein insert karo.
7. Pair nahi milta toh `{-1, -1}` return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

vector<int> twoSum(vector<int>& arr, int target) {

    unordered_map<int, int> mp;

    for (int i = 0; i < arr.size(); i++) {

        int required = target - arr[i];

        if (mp.find(required) != mp.end()) {
            return {mp[required], i};
        }

        mp[arr[i]] = i;
    }

    return {-1, -1};
}

int main() {

    vector<int> arr = {2, 7, 11, 15};

    int target = 9;

    vector<int> ans = twoSum(arr, target);

    cout << "Indices: "
         << ans[0] << ", " << ans[1];

    return 0;
}
```

**Output:**

```text
Indices: 0, 1
```

### Complexity

- Average Time Complexity: O(n)
- Auxiliary Space: O(n)
- Worst-case Time Complexity of unordered_map operations can be O(n²) overall due to collisions.

## 5. Approach 3: Two Pointer (Sorted Array)

Agar array sorted hai, toh Two Pointer approach use kar sakte hain.

### Logic

Do pointers maintain karenge:

- `left = 0`
- `right = n - 1`

Dono elements ka sum check karenge.

| Condition     | Action     |
| ------------- | ---------- |
| Sum == Target | Pair found |
| Sum < Target  | `left++`   |
| Sum > Target  | `right--`  |

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

vector<int> twoSum(vector<int>& arr, int target) {

    int left = 0;
    int right = arr.size() - 1;

    while (left < right) {

        int sum = arr[left] + arr[right];

        if (sum == target) {
            return {left, right};
        }
        else if (sum < target) {
            left++;
        }
        else {
            right--;
        }
    }

    return {-1, -1};
}

int main() {

    vector<int> arr = {2, 7, 11, 15};

    int target = 9;

    vector<int> ans = twoSum(arr, target);

    cout << "Indices: "
         << ans[0] << ", " << ans[1];

    return 0;
}
```

**Output:**

```text
Indices: 0, 1
```

### Complexity

- Time Complexity: O(n)
- Auxiliary Space: O(1)

**Important:** Two Pointer approach tabhi directly valid hai jab array sorted ho. Agar original unsorted array ke indices chahiye, toh sorting se pehle original indices preserve karne honge.

## 6. Dry Run (Hashing Approach)

Array:

```cpp
arr = {2, 7, 11, 15};
target = 9;
```

Initially:

```text
Map = {}
```

| i   | arr[i] | Required | Map mein present? | Action       |
| --- | -----: | -------: | ----------------- | ------------ |
| 0   |      2 |        7 | No                | 2 → 0 insert |
| 1   |      7 |        2 | Yes               | Pair found   |

Final Answer:

```text
Indices = {0, 1}
Values = {2, 7}
```

## 7. All Approaches Comparison

| Approach             | Time Complexity | Auxiliary Space |
| -------------------- | --------------- | --------------- |
| Brute Force          | O(n²)           | O(1)            |
| Hashing              | O(n) Average    | O(n)            |
| Two Pointer (Sorted) | O(n)            | O(1)            |

## 8. Common Mistakes

1. Same element ko do baar use karna.
2. `j = i` se inner loop start karna.
3. Hash Map mein current element insert karne se pehle required element check na karna.
4. Unsorted array par directly Two Pointer use karna.
5. Index aur value mein confusion karna.
6. Pair na milne par return condition handle na karna.

## 9. Practice Questions

1. Array `{3, 2, 4}` aur target `6` ka answer find karo.
2. Array `{3, 3}` aur target `6` solve karo.
3. Array `{1, 5, 8, 10}` aur target `13` solve karo.
4. Brute Force approach implement karo.
5. Hashing approach implement karo.
6. Sorted array par Two Pointer approach implement karo.

## 10. Quick Revision

- Two Sum mein do elements ka sum target ke equal hota hai.
- Brute Force: O(n²).
- Hashing: O(n) average time, O(n) space.
- Two Pointer: O(n) time, O(1) auxiliary space for sorted array.
- Required element = `target - arr[i]`.
- Same index ko do baar use nahi karna.

## 11. Topic Completion Checklist

- [ ] Two Sum problem samajh liya.
- [ ] Brute Force approach samajh li.
- [ ] Hashing approach samajh li.
- [ ] Two Pointer approach samajh li.
- [ ] C++ code run kar liya.
- [ ] Dry Run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 23: Best Time to Buy and Sell Stock**
