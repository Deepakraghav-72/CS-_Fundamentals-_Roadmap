# Topic 07 – Types of Arrays (1D, 2D and Multidimensional Arrays)

## 1. Types of Arrays kya hote hain?

C++ mein arrays ko dimensions ke according different types mein divide kiya jata hai.

Main types:

1. One-Dimensional Array (1D)
2. Two-Dimensional Array (2D)
3. Multidimensional Array (3D and more)

## 2. One-Dimensional Array (1D)

1D Array ek simple array hota hai jisme elements ek single sequence mein store hote hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
10 20 30 40 50
```

### 1D Array Representation

| Index | Value |
| ----- | ----- |
| 0     | 10    |
| 1     | 20    |
| 2     | 30    |
| 3     | 40    |
| 4     | 50    |

Syntax:

```cpp
data_type array_name[size];
```

## 3. Two-Dimensional Array (2D)

2D Array ek array hota hai jisme data rows aur columns ke form mein store hota hai.

Isse Matrix bhi kaha jata hai.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[2][3] = {
        {10, 20, 30},
        {40, 50, 60}
    };

    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

Output:

```text
10 20 30
40 50 60
```

### 2D Array Representation

| Row / Column | 0   | 1   | 2   |
| ------------ | --- | --- | --- |
| Row 0        | 10  | 20  | 30  |
| Row 1        | 40  | 50  | 60  |

Syntax:

```cpp
data_type array_name[rows][columns];
```

Example:

```cpp
int arr[3][4];
```

Yahan:

- Rows = 3
- Columns = 4
- Total Elements = 3 × 4 = 12

## 4. 2D Array Elements Access karna

2D Array mein element access karne ke liye do indexes use hote hain.

Syntax:

```cpp
array_name[row][column];
```

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[2][2] = {
        {10, 20},
        {30, 40}
    };

    cout << arr[0][1] << endl;
    cout << arr[1][0] << endl;

    return 0;
}
```

Output:

```text
20
30
```

Explanation:

- `arr[0][1]` = First row, Second column.
- `arr[1][0]` = Second row, First column.

## 5. 2D Array mein Values Modify karna

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[2][2] = {
        {10, 20},
        {30, 40}
    };

    arr[0][1] = 100;

    cout << arr[0][1];

    return 0;
}
```

Output:

```text
100
```

## 6. Multidimensional Array

Jab array mein two se zyada dimensions hoti hain, toh use Multidimensional Array kehte hain.

Example: 3D Array

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[2][2][2] = {
        {
            {10, 20},
            {30, 40}
        },
        {
            {50, 60},
            {70, 80}
        }
    };

    cout << arr[0][1][1];

    return 0;
}
```

Output:

```text
40
```

Yahan:

- First Index = Block
- Second Index = Row
- Third Index = Column

Total Elements = 2 × 2 × 2 = 8

## 7. 1D, 2D aur 3D Array mein Difference

| Feature    | 1D Array | 2D Array       | 3D Array     |
| ---------- | -------- | -------------- | ------------ |
| Dimensions | 1        | 2              | 3            |
| Structure  | Linear   | Rows & Columns | Blocks       |
| Indexes    | 1        | 2              | 3            |
| Example    | arr[5]   | arr[2][3]      | arr[2][2][2] |

## 8. 2D Array Traversal

2D Array ke saare elements print karne ke liye nested loops use karte hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            cout << arr[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

Output:

```text
1 2 3
4 5 6
```

Time Complexity = O(rows × columns)

## 9. Array Memory Representation

C++ ke built-in arrays ke elements contiguous memory mein store hote hain.

2D arrays bhi memory mein contiguous locations par store hote hain.

C++ mein 2D built-in arrays Row-Major Order follow karte hain.

Example:

```cpp
int arr[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

Memory order:

```text
1 → 2 → 3 → 4 → 5 → 6
```

## 10. Arrays ke Real-Life Examples

| Array Type             | Example           |
| ---------------------- | ----------------- |
| 1D Array               | Students ke marks |
| 2D Array               | Matrix / Tables   |
| 3D Array               | Multiple matrices |
| Multidimensional Array | Scientific data   |

## 11. Common Mistakes

1. Array indexing ko 1 se start karna.
2. 2D Array mein row aur column confuse karna.
3. Array ke size se bahar access karna.
4. 2D Array mein sirf ek loop use karna jab sabhi elements traverse karne hon.
5. 3D Array ke indexes ka order bhoolna.

## 12. Practice Questions

1. 1D Array kya hota hai?
2. 2D Array ko Matrix kyu kehte hain?
3. 3 × 4 Array mein total elements kitne honge?
4. `arr[1][2]` ka kya meaning hai?
5. 3D Array kya hota hai?
6. 2D Array ko traverse karne ke liye kitne loops chahiye?
7. C++ 2D built-in arrays kaun sa memory order follow karte hain?

## Quick Revision

- 1D Array = Single Dimension.
- 2D Array = Rows and Columns.
- 3D Array = Multiple Blocks.
- 1D mein one index.
- 2D mein two indexes.
- 3D mein three indexes.
- 2D Traversal = O(rows × columns).
- C++ built-in arrays = Contiguous Memory.
- 2D Array = Row-Major Order.

## Topic Status

**Topic 07 – Completed**

**Next Topic 08:** Array Traversal and Array Operations in C++.
