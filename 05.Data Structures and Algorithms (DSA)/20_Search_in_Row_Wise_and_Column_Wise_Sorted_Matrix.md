# Topic 20: Search in a Row-wise and Column-wise Sorted Matrix

## 1. Introduction

Is problem mein humein ek 2D matrix di jaati hai jisme:

1. Har row ascending order mein sorted hoti hai.
2. Har column bhi ascending order mein sorted hota hai.

**Example:**

```text
1   4   7   11
2   5   8   12
3   6   9   16
10  13  14  17
```

Target = `9`

Humein matrix mein target element search karna hai.

## 2. Previous Topic Se Difference

**Topic 19: Completely Sorted Matrix**

- Har row sorted hoti hai.
- Har column sorted hota hai.
- Next row ka first element previous row ke last element se bada hota hai.
- Matrix ko logically 1D sorted array maan sakte hain.

**Topic 20: Row-wise and Column-wise Sorted Matrix**

- Har row sorted hoti hai.
- Har column sorted hota hai.
- Lekin next row ka first element previous row ke last element se bada hona zaroori nahi hai.

Example:

```text
1   4   7   11
2   5   8   12
3   6   9   16
10  13  14  17
```

Is matrix par Topic 19 wala Binary Search directly apply nahi kar sakte.

## 3. Staircase Search Approach

Is problem ko solve karne ke liye hum Staircase Search use karte hain.

Hum matrix ke **top-right corner** se searching start karenge.

### Logic

Suppose matrix:

```text
1   4   7   11
2   5   8   12
3   6   9   16
10  13  14  17
```

Target = `9`

Top-right element = `11`

- Agar current element target se bada hai, toh current column eliminate kar do.
- Agar current element target se chhota hai, toh current row eliminate kar do.
- Agar equal hai, toh target mil gaya.

### Important Rules

| Condition                 | Action        |
| ------------------------- | ------------- |
| `arr[row][col] == target` | Element found |
| `arr[row][col] > target`  | `col--`       |
| `arr[row][col] < target`  | `row++`       |

## 4. Algorithm

1. `row = 0` initialize karo.
2. `col = total columns - 1` initialize karo.
3. Jab tak row aur column valid hain:
   - Current element check karo.
   - Equal hai toh position return karo.
   - Current element bada hai toh left move karo.
   - Current element chhota hai toh down move karo.
4. Agar target nahi milta toh `{-1, -1}` return karo.

## 5. C++ Code (Staircase Search)

```cpp
#include <iostream>
#include <vector>
using namespace std;

pair<int, int> searchMatrix(
    vector<vector<int>>& arr, int target
) {
    int rows = arr.size();
    int cols = arr[0].size();

    int row = 0;
    int col = cols - 1;

    while (row < rows && col >= 0) {

        if (arr[row][col] == target) {
            return {row, col};
        }
        else if (arr[row][col] > target) {
            col--;
        }
        else {
            row++;
        }
    }

    return {-1, -1};
}

int main() {

    vector<vector<int>> arr = {
        {1, 4, 7, 11},
        {2, 5, 8, 12},
        {3, 6, 9, 16},
        {10, 13, 14, 17}
    };

    int target = 9;

    pair<int, int> result = searchMatrix(arr, target);

    if (result.first != -1) {
        cout << "Element found at Row: "
             << result.first
             << ", Column: "
             << result.second;
    }
    else {
        cout << "Element not found";
    }

    return 0;
}
```

**Output:**

```text
Element found at Row: 2, Column: 2
```

## 6. Dry Run

Matrix:

```text
1   4   7   11
2   5   8   12
3   6   9   16
10  13  14  17
```

Target = `9`

Starting position = Top-right corner (0, 3).

| Step | Row | Column | Current Value | Action            |
| ---- | --: | -----: | ------------: | ----------------- |
| 1    |   0 |      3 |            11 | 11 > 9, move left |
| 2    |   0 |      2 |             7 | 7 < 9, move down  |
| 3    |   1 |      2 |             8 | 8 < 9, move down  |
| 4    |   2 |      2 |             9 | Target found      |

Final position:

```text
Row = 2
Column = 2
```

## 7. Alternative: Bottom-Left Approach

Hum bottom-left corner se bhi searching start kar sakte hain.

Starting position:

```cpp
int row = rows - 1;
int col = 0;
```

Rules:

| Condition         | Action  |
| ----------------- | ------- |
| Current == Target | Found   |
| Current > Target  | `row--` |
| Current < Target  | `col++` |

Dono approaches ki Time Complexity same hoti hai.

## 8. Time and Space Complexity

Let:

- R = Number of rows
- C = Number of columns

| Complexity      | Value    |
| --------------- | -------- |
| Time Complexity | O(R + C) |
| Auxiliary Space | O(1)     |

**Reason:** Har step mein ek row ya ek column eliminate hota hai. Isliye maximum R + C steps lagte hain.

## 9. Important Conditions

- Matrix ki har row ascending sorted honi chahiye.
- Matrix ka har column ascending sorted hona chahiye.
- Matrix non-empty honi chahiye (code mein `arr[0]` access kiya gaya hai).
- Duplicate elements hone par algorithm kisi ek matching position ko return kar sakta hai.

## 10. Common Mistakes

1. Top-right se start karke wrong direction mein move karna.
2. `col >= 0` boundary condition bhool jana.
3. `row < rows` boundary condition bhool jana.
4. Matrix sorting conditions verify na karna.
5. Is problem ko completely sorted matrix wali problem samajhna.

## 11. Practice Questions

1. Target `14` search karo.
2. Target `1` search karo.
3. Target `15` search karke not-found condition check karo.
4. Bottom-left approach implement karo.
5. 5 × 5 sorted matrix par Staircase Search implement karo.

## 12. Quick Revision

- Har row aur column ascending order mein sorted hota hai.
- Is problem mein Staircase Search use hoti hai.
- Top-right se start karte hain.
- Current value bada ho toh left move: `col--`.
- Current value chhota ho toh down move: `row++`.
- Time Complexity: O(R + C).
- Auxiliary Space: O(1).

## 13. Topic Completion Checklist

- [ ] Row-wise sorting samajh li.
- [ ] Column-wise sorting samajh li.
- [ ] Topic 19 aur Topic 20 ka difference samajh liya.
- [ ] Staircase Search samajh li.
- [ ] C++ code run kar liya.
- [ ] Dry Run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 21: Matrix Median**
