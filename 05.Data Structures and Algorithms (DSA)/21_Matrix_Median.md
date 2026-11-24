# Topic 21: Matrix Median

## 1. Matrix Median Kya Hota Hai?

Median kisi sorted data ka middle value hota hai.

Agar total elements odd hain, toh beech wala element median hota hai.

Agar total elements even hain, toh beech ke dono elements ka average median hota hai.

**Example:**

```text
1  3  5
2  6  9
3  6  9
```

Sabhi elements ko sorted order mein likho:

```text
1, 2, 3, 3, 5, 6, 6, 9, 9
```

Total elements = 9

Median = `5`

## 2. Problem Statement

Humein ek 2D matrix di jaati hai jisme har row individually sorted hoti hai.

Humein matrix ka median find karna hai.

**Important Conditions:**

- Har row ascending order mein sorted honi chahiye.
- Total elements usually odd hote hain.
- Matrix ke different rows aapas mein sorted hona zaroori nahi hai.

## 3. Approach 1: Brute Force

Is approach mein:

1. Matrix ke saare elements ek 1D array mein store karo.
2. 1D array ko sort karo.
3. Middle index ka element return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int findMedian(vector<vector<int>>& matrix) {
    vector<int> temp;

    for (int i = 0; i < matrix.size(); i++) {
        for (int j = 0; j < matrix[i].size(); j++) {
            temp.push_back(matrix[i][j]);
        }
    }

    sort(temp.begin(), temp.end());

    int n = temp.size();

    return temp[n / 2];
}

int main() {
    vector<vector<int>> matrix = {
        {1, 3, 5},
        {2, 6, 9},
        {3, 6, 9}
    };

    cout << "Median: " << findMedian(matrix);

    return 0;
}
```

**Output:**

```text
Median: 5
```

## 4. Approach 2: Binary Search (Optimized)

Kyuki har row already sorted hai, hum Binary Search ka use karke median find kar sakte hain.

Is approach mein hum directly matrix ke elements par Binary Search nahi karte, balki possible median values par Binary Search karte hain.

### Important Concept

Maan lo matrix mein total 9 elements hain.

Median ki position:

```cpp
desired = (9 + 1) / 2;
desired = 5;
```

Humein aisi value find karni hai jiske equal ya usse chhote elements ki total count kam se kam 5 ho.

### Algorithm

1. Matrix ka minimum element find karo.
   - Har row ka first element check karo.
2. Matrix ka maximum element find karo.
   - Har row ka last element check karo.
3. `low = minimum` aur `high = maximum` set karo.
4. Binary Search se middle value calculate karo.
5. Har row mein `upper_bound()` use karke middle value se chhote ya equal elements count karo.
6. Agar count median position se chhota hai, toh `low = mid + 1`.
7. Otherwise `high = mid`.
8. Jab `low == high` ho jaye, wahi median hai.

## 5. C++ Code (Optimized Approach)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int findMedian(vector<vector<int>>& matrix) {

    int rows = matrix.size();
    int cols = matrix[0].size();

    int low = matrix[0][0];
    int high = matrix[0][cols - 1];

    // Find minimum and maximum
    for (int i = 1; i < rows; i++) {
        low = min(low, matrix[i][0]);
        high = max(high, matrix[i][cols - 1]);
    }

    int desired = (rows * cols + 1) / 2;

    while (low < high) {

        int mid = low + (high - low) / 2;

        int count = 0;

        // Count elements <= mid
        for (int i = 0; i < rows; i++) {
            count += upper_bound(
                matrix[i].begin(),
                matrix[i].end(),
                mid
            ) - matrix[i].begin();
        }

        if (count < desired) {
            low = mid + 1;
        }
        else {
            high = mid;
        }
    }

    return low;
}

int main() {

    vector<vector<int>> matrix = {
        {1, 3, 5},
        {2, 6, 9},
        {3, 6, 9}
    };

    cout << "Median: " << findMedian(matrix);

    return 0;
}
```

**Output:**

```text
Median: 5
```

## 6. upper_bound() Kya Hai?

C++ STL ka `upper_bound()` function sorted range mein kisi value se strictly greater pehle element ka iterator return karta hai.

**Syntax:**

```cpp
upper_bound(start, end, value);
```

Example:

```cpp
vector<int> arr = {1, 3, 5, 7, 9};

int count = upper_bound(
    arr.begin(),
    arr.end(),
    5
) - arr.begin();

cout << count;
```

**Output:**

```text
3
```

Reason: `5` se chhote ya equal elements hain `1, 3, 5`.

## 7. Dry Run

Matrix:

```text
1  3  5
2  6  9
3  6  9
```

Total elements = 9

Median position:

```text
desired = (9 + 1) / 2 = 5
```

Initial range:

```text
low = 1
high = 9
```

| Step | low | high | mid | Count (<= mid) | Action   |
| ---- | --: | ---: | --: | -------------: | -------- |
| 1    |   1 |    9 |   5 |              5 | high = 5 |
| 2    |   1 |    5 |   3 |              4 | low = 4  |
| 3    |   4 |    5 |   4 |              4 | low = 5  |

Now:

```text
low = 5
high = 5
```

Median = `5`

## 8. Time and Space Complexity

Let:

- R = Number of rows
- C = Number of columns
- V = Value range (maximum - minimum + 1)

| Approach      | Time Complexity       | Auxiliary Space |
| ------------- | --------------------- | --------------- |
| Brute Force   | O(R × C × log(R × C)) | O(R × C)        |
| Binary Search | O(log(V) × R × log C) | O(1)            |

**Note:** Optimized approach mein `upper_bound()` har row mein O(log C) time leta hai.

## 9. Common Mistakes

1. Har row sorted hone ki condition ignore karna.
2. Binary Search mein minimum aur maximum value galat find karna.
3. `upper_bound()` ki jagah `lower_bound()` use karke count galat nikalna.
4. Median position calculate karne mein mistake karna.
5. Matrix empty hone par `matrix[0]` access karna.

## 10. Practice Questions

1. Given matrix ka median find karo:

```text
1  4  7
2  5  8
3  6  9
```

2. Duplicate elements wali matrix ka median find karo.
3. Brute Force approach implement karo.
4. Binary Search approach implement karo.
5. `upper_bound()` aur `lower_bound()` ka difference samjho.

## 11. Quick Revision

- Median sorted data ka middle element hota hai.
- Matrix ki har row sorted honi chahiye.
- Brute Force mein elements collect karke sort karte hain.
- Optimized approach mein Binary Search on Answer use hoti hai.
- `upper_bound()` se elements <= mid count karte hain.
- Median position = `(rows × cols + 1) / 2`.
- Optimized Time Complexity = O(log(V) × R × log C).
- Auxiliary Space = O(1).

## 12. Topic Completion Checklist

- [ ] Median ka meaning samajh liya.
- [ ] Brute Force approach samajh li.
- [ ] Binary Search approach samajh li.
- [ ] upper_bound() samajh liya.
- [ ] C++ code run kar liya.
- [ ] Dry Run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 22: Two Sum Problem**
