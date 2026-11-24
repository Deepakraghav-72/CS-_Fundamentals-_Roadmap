# Topic 27: Remove Duplicates from a Sorted Array

## 1. Problem Kya Hai?

Humein ek **sorted array** diya hota hai. Humein usmein se duplicate elements remove karne hain aur sirf unique elements rakhne hain.

**Example:**

```cpp
arr[] = {1, 1, 2, 2, 3, 4, 4};
```

Output:

```text
1 2 3 4
```

Sorted array hone ki wajah se duplicate elements ek saath hote hain.

## 2. Important Conditions

1. Array sorted hona chahiye.
2. Har unique element sirf ek baar aana chahiye.
3. Original order maintain rehna chahiye.
4. Optimized approach mein extra array use nahi karna hai.

## 3. Approach 1: Extra Array

### Algorithm

1. Ek temporary vector banao.
2. Array ka first element temporary vector mein add karo.
3. Baaki elements ko previous element se compare karo.
4. Agar element different hai, toh temporary vector mein add karo.
5. Temporary vector ko original array mein copy karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int removeDuplicates(vector<int>& arr) {

    if (arr.empty()) {
        return 0;
    }

    vector<int> temp;

    temp.push_back(arr[0]);

    for (int i = 1; i < arr.size(); i++) {

        if (arr[i] != arr[i - 1]) {
            temp.push_back(arr[i]);
        }
    }

    arr = temp;

    return arr.size();
}

int main() {

    vector<int> arr = {1, 1, 2, 2, 3, 4, 4};

    int k = removeDuplicates(arr);

    for (int i = 0; i < k; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

**Output:**

```text
1 2 3 4
```

### Complexity

- Time Complexity: O(n)
- Auxiliary Space: O(n)

## 4. Approach 2: Two Pointer (Optimized)

Is approach mein hum extra array use nahi karenge.

Hum do pointers use karenge:

- `i`: Unique elements ki last position maintain karega.
- `j`: Array ko traverse karega.

### Algorithm

1. Agar array empty hai toh 0 return karo.
2. `i = 0` initialize karo.
3. `j = 1` se array traverse karo.
4. Agar `arr[j] != arr[i]` hai:
   - `i++` karo.
   - `arr[i] = arr[j]` assign karo.
5. End mein `i + 1` return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int removeDuplicates(vector<int>& arr) {

    if (arr.empty()) {
        return 0;
    }

    int i = 0;

    for (int j = 1; j < arr.size(); j++) {

        if (arr[j] != arr[i]) {

            i++;

            arr[i] = arr[j];
        }
    }

    return i + 1;
}

int main() {

    vector<int> arr = {1, 1, 2, 2, 3, 4, 4};

    int k = removeDuplicates(arr);

    cout << "Unique elements: ";

    for (int i = 0; i < k; i++) {
        cout << arr[i] << " ";
    }

    cout << "\nCount: " << k;

    return 0;
}
```

**Output:**

```text
Unique elements: 1 2 3 4
Count: 4
```

## 5. Dry Run

Initial Array:

```text
{1, 1, 2, 2, 3, 4, 4}
```

Initially:

```cpp
i = 0;
```

| Step |   j | arr[j] | Comparison | Action          |
| ---- | --: | -----: | ---------- | --------------- |
| 1    |   1 |      1 | 1 == 1     | Skip            |
| 2    |   2 |      2 | 2 != 1     | i++, arr[1] = 2 |
| 3    |   3 |      2 | 2 == 2     | Skip            |
| 4    |   4 |      3 | 3 != 2     | i++, arr[2] = 3 |
| 5    |   5 |      4 | 4 != 3     | i++, arr[3] = 4 |
| 6    |   6 |      4 | 4 == 4     | Skip            |

Final Array:

```text
{1, 2, 3, 4, 3, 4, 4}
```

Unique elements sirf first `k` positions mein valid hain.

```cpp
k = i + 1; // 4
```

**Important:** Humein sirf first 4 elements consider karne hain. Remaining positions ko ignore karna hai. Vector ka size automatically reduce nahi hota.

## 6. More Examples

**Example 1:**

```cpp
arr[] = {1, 1, 1, 1};
```

Output:

```text
1
```

**Example 2:**

```cpp
arr[] = {1, 2, 3, 4};
```

Output:

```text
1 2 3 4
```

**Example 3:**

```cpp
arr[] = {};
```

Output:

```text
Empty array, count = 0
```

## 7. Time and Space Complexity

| Approach    | Time Complexity | Auxiliary Space |
| ----------- | --------------- | --------------- |
| Extra Array | O(n)            | O(n)            |
| Two Pointer | O(n)            | O(1)            |

**Best Approach:** Two Pointer technique.

## 8. Common Mistakes

1. Unsorted array par directly ye approach use karna.
2. `i = 0` ki jagah galat index se start karna.
3. `return i` karna, jabki `return i + 1` karna hai.
4. Empty array ka case handle nahi karna.
5. Ye samajhna ki duplicate removal ke baad vector ka size automatically kam ho jayega.

## 9. Practice Questions

1. `{1, 1, 2, 2, 3}` se duplicates remove karo.
2. `{2, 2, 2, 3, 3, 4, 5, 5}` solve karo.
3. Empty array ke liye function test karo.
4. Two Pointer approach ko bina extra array ke implement karo.
5. Function se unique elements ka count return karwao.

## 10. Quick Revision

- Problem: Sorted array se duplicates remove karna.
- Technique: Two Pointers.
- `i`: Unique elements ki position.
- `j`: Array traversal.
- Condition: `arr[j] != arr[i]`.
- Final unique count: `i + 1`.
- Time Complexity: O(n).
- Auxiliary Space: O(1).

## 11. Topic Completion Checklist

- [ ] Problem samajh li.
- [ ] Extra Array approach samajh li.
- [ ] Two Pointer approach samajh li.
- [ ] Dry Run kar liya.
- [ ] C++ code run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 28: Remove Duplicates from a Sorted Array II (At Most Twice)**
