# Topic 26: Move All Zeroes to the End of an Array

## 1. Problem Kya Hai?

Is problem mein humein ek integer array diya hota hai.

Humein array ke saare zeroes ko end mein move karna hota hai, bina non-zero elements ka order change kiye.

**Example:**

```cpp
arr[] = {0, 1, 0, 3, 12};
```

Expected Output:

```text
{1, 3, 12, 0, 0}
```

## 2. Important Conditions

1. Saare zeroes array ke end mein hone chahiye.
2. Non-zero elements ka original order same rehna chahiye.
3. Array ka size change nahi hona chahiye.
4. In-place approach mein extra array use nahi karna chahiye.

## 3. Approach 1: Extra Array

Is approach mein hum ek temporary array banayenge.

### Algorithm

1. Ek empty temporary vector banao.
2. Saare non-zero elements usmein insert karo.
3. Remaining positions par zero insert karo.
4. Temporary array ko original array mein copy karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void moveZeroes(vector<int>& arr) {

    vector<int> temp;

    // Store non-zero elements
    for (int x : arr) {
        if (x != 0) {
            temp.push_back(x);
        }
    }

    // Add zeroes at the end
    while (temp.size() < arr.size()) {
        temp.push_back(0);
    }

    arr = temp;
}

int main() {

    vector<int> arr = {0, 1, 0, 3, 12};

    moveZeroes(arr);

    for (int x : arr) {
        cout << x << " ";
    }

    return 0;
}
```

**Output:**

```text
1 3 12 0 0
```

### Complexity

- Time Complexity: O(n)
- Auxiliary Space: O(n)

## 4. Approach 2: Two Pointer (Optimized)

Is approach mein hum extra array use nahi karenge.

Hum ek pointer `j` maintain karenge jo next non-zero element ki correct position batayega.

### Main Logic

1. `j = 0` initialize karo.
2. Array ko left se right traverse karo.
3. Jab bhi non-zero element mile:
   - `arr[i]` aur `arr[j]` swap karo.
   - `j++` karo.
4. Traversal complete hone par saare zeroes end mein aa jayenge.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void moveZeroes(vector<int>& arr) {

    int j = 0;

    for (int i = 0; i < arr.size(); i++) {

        if (arr[i] != 0) {

            swap(arr[i], arr[j]);

            j++;
        }
    }
}

int main() {

    vector<int> arr = {0, 1, 0, 3, 12};

    moveZeroes(arr);

    for (int x : arr) {
        cout << x << " ";
    }

    return 0;
}
```

**Output:**

```text
1 3 12 0 0
```

## 5. Dry Run

Initial Array:

```text
{0, 1, 0, 3, 12}
```

Initial:

```cpp
j = 0;
```

| Step |   i | arr[i] | Action             | Array          |
| ---- | --: | -----: | ------------------ | -------------- |
| 1    |   0 |      0 | Skip               | 0, 1, 0, 3, 12 |
| 2    |   1 |      1 | Swap index 1 and 0 | 1, 0, 0, 3, 12 |
| 3    |   2 |      0 | Skip               | 1, 0, 0, 3, 12 |
| 4    |   3 |      3 | Swap index 3 and 1 | 1, 3, 0, 0, 12 |
| 5    |   4 |     12 | Swap index 4 and 2 | 1, 3, 12, 0, 0 |

Final Array:

```text
{1, 3, 12, 0, 0}
```

## 6. More Examples

**Example 1:**

```cpp
arr[] = {0, 0, 1, 2, 3};
```

Output:

```text
{1, 2, 3, 0, 0}
```

**Example 2:**

```cpp
arr[] = {1, 2, 3, 4};
```

Output:

```text
{1, 2, 3, 4}
```

**Example 3:**

```cpp
arr[] = {0, 0, 0, 0};
```

Output:

```text
{0, 0, 0, 0}
```

## 7. Time and Space Complexity

| Approach    | Time Complexity | Auxiliary Space |
| ----------- | --------------- | --------------- |
| Extra Array | O(n)            | O(n)            |
| Two Pointer | O(n)            | O(1)            |

Two Pointer approach optimized hai kyunki ye in-place operation perform karti hai.

## 8. Common Mistakes

1. Non-zero elements ka original order change kar dena.
2. Extra array use karke bhi unnecessary nested loops lagana.
3. `j` ko increment karna bhool jana.
4. Zero elements ko bhi swap karna.
5. Array ke size ko unnecessarily change karna.

## 9. Practice Questions

1. `{0, 1, 0, 3, 12}` solve karo.
2. `{0, 0, 1, 0, 2, 3}` solve karo.
3. `{1, 2, 3, 4}` solve karo.
4. `{0, 0, 0}` solve karo.
5. Two Pointer approach bina `swap()` function ke implement karo.

## 10. Quick Revision

- Goal = Saare zeroes ko end mein move karna.
- Non-zero elements ka order same rehna chahiye.
- Extra Array approach: O(n) time, O(n) space.
- Two Pointer approach: O(n) time, O(1) auxiliary space.
- `j` next non-zero element ki position maintain karta hai.
- Optimized approach in-place operation perform karti hai.

## 11. Topic Completion Checklist

- [ ] Problem samajh li.
- [ ] Extra Array approach samajh li.
- [ ] Two Pointer approach samajh li.
- [ ] Dry Run kar liya.
- [ ] C++ code run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 27: Remove Duplicates from a Sorted Array**
