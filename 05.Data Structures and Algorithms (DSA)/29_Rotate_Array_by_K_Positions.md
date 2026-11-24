# Topic 29: Rotate Array by K Positions

## 1. Problem Kya Hai?

Is problem mein humein ek array aur integer `k` diya hota hai.

Humein array ko `k` positions rotate karna hota hai.

Array rotation ke 2 types hote hain:

1. Left Rotation
2. Right Rotation

## 2. Left Rotation

Left rotation mein elements left side move hote hain aur starting elements end mein chale jaate hain.

**Example:**

```cpp
arr[] = {1, 2, 3, 4, 5};
k = 2;
```

Output:

```text
3 4 5 1 2
```

### Approach 1: Extra Array

**Algorithm:**

1. `k = k % n` calculate karo.
2. Starting ke `k` elements ko temporary array mein store karo.
3. Remaining elements ko left shift karo.
4. Temporary elements ko end mein place karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void leftRotate(vector<int>& arr, int k) {

    int n = arr.size();

    if (n == 0) return;

    k = k % n;

    vector<int> temp;

    for (int i = 0; i < k; i++) {
        temp.push_back(arr[i]);
    }

    for (int i = k; i < n; i++) {
        arr[i - k] = arr[i];
    }

    for (int i = 0; i < k; i++) {
        arr[n - k + i] = temp[i];
    }
}

int main() {

    vector<int> arr = {1, 2, 3, 4, 5};

    leftRotate(arr, 2);

    for (int x : arr) {
        cout << x << " ";
    }

    return 0;
}
```

**Output:**

```text
3 4 5 1 2
```

## 3. Right Rotation

Right rotation mein elements right side move hote hain aur last ke elements starting mein aa jaate hain.

**Example:**

```cpp
arr[] = {1, 2, 3, 4, 5};
k = 2;
```

Output:

```text
4 5 1 2 3
```

### Approach 1: Extra Array

**Algorithm:**

1. `k = k % n` calculate karo.
2. Last ke `k` elements temporary array mein store karo.
3. Remaining elements ko right shift karo.
4. Temporary elements ko starting mein place karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

void rightRotate(vector<int>& arr, int k) {

    int n = arr.size();

    if (n == 0) return;

    k = k % n;

    vector<int> temp;

    for (int i = n - k; i < n; i++) {
        temp.push_back(arr[i]);
    }

    for (int i = n - k - 1; i >= 0; i--) {
        arr[i + k] = arr[i];
    }

    for (int i = 0; i < k; i++) {
        arr[i] = temp[i];
    }
}

int main() {

    vector<int> arr = {1, 2, 3, 4, 5};

    rightRotate(arr, 2);

    for (int x : arr) {
        cout << x << " ";
    }

    return 0;
}
```

**Output:**

```text
4 5 1 2 3
```

## 4. Approach 2: Reversal Algorithm (Optimized)

Reversal Algorithm se hum array ko bina extra array ke rotate kar sakte hain.

Ismein `reverse()` function use hota hai.

### A. Left Rotation Logic

For left rotation by `k`:

1. First `k` elements reverse karo.
2. Remaining `n-k` elements reverse karo.
3. Complete array reverse karo.

**Example:**

```text
Original:  1 2 3 4 5

Step 1:    2 1 3 4 5
Step 2:    2 1 5 4 3
Step 3:    3 4 5 1 2
```

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void leftRotate(vector<int>& arr, int k) {

    int n = arr.size();

    if (n == 0) return;

    k = k % n;

    reverse(arr.begin(), arr.begin() + k);

    reverse(arr.begin() + k, arr.end());

    reverse(arr.begin(), arr.end());
}

int main() {

    vector<int> arr = {1, 2, 3, 4, 5};

    leftRotate(arr, 2);

    for (int x : arr) {
        cout << x << " ";
    }

    return 0;
}
```

**Output:**

```text
3 4 5 1 2
```

### B. Right Rotation Logic

For right rotation by `k`:

1. Complete array reverse karo.
2. First `k` elements reverse karo.
3. Remaining elements reverse karo.

**Example:**

```text
Original:  1 2 3 4 5

Step 1:    5 4 3 2 1
Step 2:    4 5 3 2 1
Step 3:    4 5 1 2 3
```

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void rightRotate(vector<int>& arr, int k) {

    int n = arr.size();

    if (n == 0) return;

    k = k % n;

    reverse(arr.begin(), arr.end());

    reverse(arr.begin(), arr.begin() + k);

    reverse(arr.begin() + k, arr.end());
}

int main() {

    vector<int> arr = {1, 2, 3, 4, 5};

    rightRotate(arr, 2);

    for (int x : arr) {
        cout << x << " ";
    }

    return 0;
}
```

**Output:**

```text
4 5 1 2 3
```

## 5. Dry Run: Right Rotation by 2

Initial Array:

```text
1 2 3 4 5
```

**Step 1: Complete Array Reverse**

```text
5 4 3 2 1
```

**Step 2: First 2 Elements Reverse**

```text
4 5 3 2 1
```

**Step 3: Remaining Elements Reverse**

```text
4 5 1 2 3
```

Final Answer:

```text
4 5 1 2 3
```

## 6. Important Concept: K % N

Agar `k` array ke size se bada ho, toh `k % n` use karte hain.

Example:

```cpp
n = 5;
k = 7;

k = k % n;  // 2
```

7 rotations aur 2 rotations ka result same hoga.

**Special Cases:**

- `k = 0`: Array same rahega.
- `k = n`: Array same rahega.
- `k > n`: `k % n` use karenge.
- Empty array: Rotation perform nahi karenge.

## 7. Time and Space Complexity

| Approach           | Time Complexity | Auxiliary Space |
| ------------------ | --------------- | --------------- |
| Extra Array        | O(n)            | O(k)            |
| Reversal Algorithm | O(n)            | O(1)            |

**Best Approach:** Reversal Algorithm.

## 8. Common Mistakes

1. `k % n` calculate nahi karna.
2. Left aur Right rotation ka difference bhoolna.
3. Reversal ka order galat rakhna.
4. Empty array handle nahi karna.
5. `reverse()` ke iterator boundaries galat dena.

## 9. Practice Questions

1. `{1, 2, 3, 4, 5}` ko left rotate by 2 karo.
2. `{1, 2, 3, 4, 5}` ko right rotate by 3 karo.
3. `{10, 20, 30, 40}` ko left rotate by 1 karo.
4. `{1, 2, 3}` ko right rotate by 5 karo.
5. Reversal Algorithm ko bina `reverse()` function ke implement karo.

## 10. Quick Revision

- Array rotation ke 2 types: Left aur Right.
- Left Rotation: Starting elements end mein jaate hain.
- Right Rotation: Last elements starting mein aate hain.
- Large `k` ke liye `k % n` use hota hai.
- Optimized technique: Reversal Algorithm.
- Time Complexity: O(n).
- Auxiliary Space: O(1).

## 11. Topic Completion Checklist

- [ ] Left Rotation samajh li.
- [ ] Right Rotation samajh li.
- [ ] Extra Array approach samajh li.
- [ ] Reversal Algorithm samajh li.
- [ ] Dry Run kar liya.
- [ ] C++ code run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 30: Container With Most Water**
