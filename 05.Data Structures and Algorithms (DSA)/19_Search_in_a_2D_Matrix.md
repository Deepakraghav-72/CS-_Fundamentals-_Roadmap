# Topic 19: Search in a 2D Matrix

## 1. 2D Matrix Kya Hota Hai?

2D Matrix ek aisa data structure hai jisme data rows aur columns mein store hota hai.

**Example:**

```cpp
int arr[3][4] = {
    {1,  3,  5,  7},
    {10, 11, 16, 20},
    {23, 30, 34, 60}
};
```

Is matrix mein:

- Rows = 3
- Columns = 4
- Total Elements = 3 × 4 = 12

## 2. Problem Statement

Humein ek sorted 2D Matrix diya hota hai aur ek target element diya hota hai.

Humein check karna hai ki target matrix mein present hai ya nahi.

Example:

```cpp
Matrix:
1   3   5   7
10  11  16  20
23  30  34  60

Target = 16
```

Output:

```text
Element found at Row: 1, Column: 2
```

## 3. Matrix Ki Important Conditions

Is topic mein hum aisi matrix consider kar rahe hain jisme:

1. Har row ascending order mein sorted hai.
2. Har next row ka first element previous row ke last element se bada hai.

Example:

```text
1   3   5   7
10  11  16  20
23  30  34  60
```

Is condition ki wajah se poori matrix ko ek sorted 1D array ki tarah treat kar sakte hain.

## 4. Approach 1: Linear Search

Har element ko one by one check karenge.

### C++ Code

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[3][4] = {
        {1, 3, 5, 7},
        {10, 11, 16, 20},
        {23, 30, 34, 60}
    };

    int target = 16;

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {

            if (arr[i][j] == target) {
                cout << "Element found at Row: "
                     << i << ", Column: " << j;
                return 0;
            }
        }
    }

    cout << "Element not found";

    return 0;
}
```

**Output:**

```text
Element found at Row: 1, Column: 2
```

### Complexity

- Time Complexity: O(rows × columns)
- Space Complexity: O(1)

## 5. Approach 2: Binary Search (Optimized)

Kyuki matrix completely sorted hai, hum Binary Search apply kar sakte hain.

Hum poori 2D matrix ko logically ek 1D sorted array maanenge.

### Important Formula

Agar matrix mein `rows` aur `cols` hain, toh:

**Middle index se row aur column:**

```cpp
row = mid / cols;
col = mid % cols;
```

Ye formula 1D index ko 2D matrix ke row aur column mein convert karta hai.

### Algorithm

1. `low = 0` initialize karo.
2. `high = rows * cols - 1` initialize karo.
3. Middle index calculate karo.
4. Middle index ko row aur column mein convert karo.
5. `arr[row][col]` ko target se compare karo.
6. Agar equal hai toh element mil gaya.
7. Agar target chhota hai toh `high = mid - 1`.
8. Agar target bada hai toh `low = mid + 1`.
9. Element nahi milta toh `false` return karo.

### C++ Code

```cpp
#include <iostream>
using namespace std;

bool searchMatrix(int arr[][4], int rows, int target) {
    int cols = 4;

    int low = 0;
    int high = rows * cols - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        int row = mid / cols;
        int col = mid % cols;

        if (arr[row][col] == target) {
            cout << "Element found at Row: "
                 << row << ", Column: " << col;
            return true;
        }
        else if (target < arr[row][col]) {
            high = mid - 1;
        }
        else {
            low = mid + 1;
        }
    }

    return false;
}

int main() {
    int arr[3][4] = {
        {1, 3, 5, 7},
        {10, 11, 16, 20},
        {23, 30, 34, 60}
    };

    int target = 16;

    if (!searchMatrix(arr, 3, target)) {
        cout << "Element not found";
    }

    return 0;
}
```

**Output:**

```text
Element found at Row: 1, Column: 2
```

## 6. Dry Run

Matrix:

```text
1   3   5   7
10  11  16  20
23  30  34  60
```

Target = `16`

Total elements = 12

Initial values:

```cpp
low = 0;
high = 11;
```

| Step | low | high | mid | Row | Column | Value |
| ---- | --: | ---: | --: | --: | -----: | ----: |
| 1    |   0 |   11 |   5 |   1 |      1 |    11 |
| 2    |   6 |   11 |   8 |   2 |      0 |    23 |
| 3    |   6 |    7 |   6 |   1 |      2 |    16 |

Target found at Row 1, Column 2.

## 7. Time and Space Complexity

| Approach      | Time Complexity     | Space Complexity |
| ------------- | ------------------- | ---------------- |
| Linear Search | O(rows × cols)      | O(1)             |
| Binary Search | O(log(rows × cols)) | O(1)             |

Binary Search optimized approach hai.

## 8. Important Difference

**Type 1: Completely Sorted Matrix**

- Har row sorted hoti hai.
- Har next row ka first element previous row ke last element se bada hota hai.
- Is matrix ko 1D sorted array ki tarah treat kar sakte hain.
- Binary Search directly apply hoti hai.

**Type 2: Row and Column Wise Sorted Matrix**

- Har row ascending order mein sorted hoti hai.
- Har column bhi ascending order mein sorted hota hai.
- Lekin next row ka first element previous row ke last element se bada hona zaroori nahi hai.
- Iske liye alag searching approach use hoti hai.

## 9. Common Mistakes

1. `row = mid / cols` ki jagah `mid / rows` likhna.
2. `col = mid % cols` ki jagah `mid % rows` likhna.
3. `high = rows * cols` set karna; correct value `rows * cols - 1` hai.
4. Matrix sorted hone ki condition check kiye bina Binary Search lagana.
5. Row aur column indexing mein confusion karna.

## 10. Practice Questions

1. Given matrix mein target `30` search karo.
2. Target `60` ka row aur column find karo.
3. Matrix mein target `15` search karo.
4. Linear Search aur Binary Search ka comparison likho.
5. 4 × 4 sorted matrix mein Binary Search implement karo.

## 11. Quick Revision

- 2D Matrix mein rows aur columns hote hain.
- Completely sorted matrix ko logically 1D array maan sakte hain.
- Total elements = `rows × cols`.
- `row = mid / cols`.
- `col = mid % cols`.
- Binary Search Time Complexity = O(log(rows × cols)).
- Auxiliary Space = O(1).

## 12. Topic Completion Checklist

- [ ] 2D Matrix samajh li.
- [ ] Matrix sorting conditions samajh li.
- [ ] Linear Search implement kar li.
- [ ] Binary Search implement kar li.
- [ ] Row-column conversion formula samajh li.
- [ ] Dry Run kar li.
- [ ] Practice questions solve kar li.

---

**Next Topic 20: Search in a Row-wise and Column-wise Sorted Matrix**
