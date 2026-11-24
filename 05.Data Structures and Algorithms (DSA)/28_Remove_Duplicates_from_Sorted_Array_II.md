# Topic 28: Remove Duplicates from a Sorted Array II (At Most Twice)

## 1. Problem Kya Hai?

Is problem mein humein ek sorted array diya hota hai.

Humein duplicates remove karne hain, lekin har unique element ko maximum **2 times** rakh sakte hain.

**Example:**

```cpp
arr[] = {1, 1, 1, 2, 2, 3};
```

Output:

```text
1 1 2 2 3
```

Yahan `1` teen baar tha, lekin humne sirf 2 baar rakha.

## 2. Important Conditions

1. Array sorted hona chahiye.
2. Har element maximum 2 times aa sakta hai.
3. Original order maintain rehna chahiye.
4. Optimized solution mein extra array use nahi karna hai.

## 3. Approach 1: Extra Array

### Algorithm

1. Ek temporary vector banao.
2. Array ke elements ko traverse karo.
3. Agar temporary vector mein 2 se kam elements hain, toh current element add karo.
4. Otherwise, last two elements se compare karo.
5. Agar current element last two elements se different hai, toh add karo.
6. Temporary vector ko original array mein copy karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int removeDuplicates(vector<int>& arr) {

    vector<int> temp;

    for (int x : arr) {

        int n = temp.size();

        if (n < 2 || x != temp[n - 2]) {
            temp.push_back(x);
        }
    }

    arr = temp;

    return arr.size();
}

int main() {

    vector<int> arr = {1, 1, 1, 2, 2, 3};

    int k = removeDuplicates(arr);

    for (int i = 0; i < k; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

**Output:**

```text
1 1 2 2 3
```

### Complexity

- Time Complexity: O(n)
- Auxiliary Space: O(n)

## 4. Approach 2: Two Pointer (Optimized)

Is approach mein extra array use nahi hota.

Hum ek pointer `k` maintain karenge jo next valid element ki position batayega.

### Main Logic

- Agar array mein 2 ya usse kam elements hain, toh array already valid hai.
- `k = 2` se start karenge.
- Har element ko `arr[k - 2]` se compare karenge.
- Agar current element different hai, toh usse `arr[k]` par place karenge.
- `k++` karenge.

### C++ Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

int removeDuplicates(vector<int>& arr) {

    if (arr.size() <= 2) {
        return arr.size();
    }

    int k = 2;

    for (int i = 2; i < arr.size(); i++) {

        if (arr[i] != arr[k - 2]) {

            arr[k] = arr[i];

            k++;
        }
    }

    return k;
}

int main() {

    vector<int> arr = {1, 1, 1, 2, 2, 3};

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
Unique elements: 1 1 2 2 3
Count: 5
```

## 5. Dry Run

Initial Array:

```text
{1, 1, 1, 2, 2, 3}
```

Initially:

```cpp
k = 2;
```

| i   | arr[i] | arr[k-2] | Action       |
| --- | -----: | -------: | ------------ |
| 2   |      1 |        1 | Skip         |
| 3   |      2 |        1 | Store 2, k++ |
| 4   |      2 |        1 | Store 2, k++ |
| 5   |      3 |        2 | Store 3, k++ |

Final valid portion:

```text
1 1 2 2 3
```

Final count:

```text
k = 5
```

**Important:** Original vector ka size same reh sakta hai. Sirf first `k` elements valid result hote hain.

## 6. More Examples

**Example 1:**

```cpp
arr[] = {1, 1, 1, 1};
```

Output:

```text
1 1
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
arr[] = {0, 0, 0, 1, 1, 1, 2, 2};
```

Output:

```text
0 0 1 1 2 2
```

## 7. Time and Space Complexity

| Approach    | Time Complexity | Auxiliary Space |
| ----------- | --------------- | --------------- |
| Extra Array | O(n)            | O(n)            |
| Two Pointer | O(n)            | O(1)            |

**Best Approach:** Two Pointer.

## 8. General Concept: At Most K Times

Agar question mein har element ko maximum `K` times allow karna ho, toh sorted array ke liye same logic use kar sakte hain.

Condition:

```cpp
if (k < limit || arr[i] != arr[k - limit]) {
    arr[k] = arr[i];
    k++;
}
```

Yahan `limit` maximum allowed occurrences hain.

Note: Is general code mein `k` output length pointer hai, aur `limit` maximum allowed frequency.

## 9. Common Mistakes

1. `arr[k - 2]` ki jagah `arr[k - 1]` compare karna.
2. Array sorted hone ki condition bhool jana.
3. `k = 2` initialize na karna.
4. First two elements ko handle na karna.
5. Return value ko final array size samajh lena.

## 10. Practice Questions

1. `{1, 1, 1, 2, 2, 3}` solve karo.
2. `{1, 1, 1, 1, 2, 2, 2}` solve karo.
3. `{0, 0, 0, 1, 1, 2, 2, 2}` solve karo.
4. At most 3 occurrences ke liye code modify karo.
5. Two Pointer approach ka dry run khud karo.

## 11. Quick Revision

- Problem: Har element maximum 2 times rakhna.
- Input: Sorted array.
- Technique: Two Pointers.
- Starting pointer: `k = 2`.
- Comparison: `arr[i] != arr[k - 2]`.
- Time Complexity: O(n).
- Auxiliary Space: O(1).

## 12. Topic Completion Checklist

- [ ] Problem samajh li.
- [ ] Extra Array approach samajh li.
- [ ] Two Pointer approach samajh li.
- [ ] Dry Run kar liya.
- [ ] C++ code run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 29: Rotate Array by K Positions**
