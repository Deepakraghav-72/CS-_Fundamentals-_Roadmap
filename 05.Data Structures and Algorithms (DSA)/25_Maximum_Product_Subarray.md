# Topic 25: Maximum Product Subarray

## 1. Maximum Product Subarray Kya Hai?

Is problem mein humein ek integer array diya hota hai.

Humein ek continuous subarray find karna hota hai jiska product maximum ho.

**Example:**

```cpp
arr[] = {2, 3, -2, 4};
```

Possible products:

```text
2 × 3 = 6
2 × 3 × -2 = -12
3 × -2 = -6
-2 × 4 = -8
```

Maximum product:

```text
2 × 3 = 6
```

**Output:**

```text
Maximum Product = 6
```

## 2. Important Concept

Maximum Product Subarray mein positive aur negative numbers dono important hote hain.

Example:

```cpp
arr[] = {-2, 3, -4};
```

Product:

```text
-2 × 3 × -4 = 24
```

Yahan do negative numbers multiply hokar positive result dete hain.

Isliye humein maximum ke saath minimum product bhi track karna hota hai.

## 3. Approach 1: Brute Force

Har possible subarray ka product calculate karenge.

### Algorithm

1. `maxProduct = INT_MIN` initialize karo.
2. Outer loop se starting index select karo.
3. Inner loop se ending index select karo.
4. Product calculate karte jao.
5. Maximum product update karo.
6. Final answer return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits>
using namespace std;

int maxProduct(vector<int>& arr) {

    int n = arr.size();
    int maxProduct = INT_MIN;

    for (int i = 0; i < n; i++) {

        int product = 1;

        for (int j = i; j < n; j++) {

            product *= arr[j];

            maxProduct = max(maxProduct, product);
        }
    }

    return maxProduct;
}

int main() {

    vector<int> arr = {2, 3, -2, 4};

    cout << "Maximum Product: "
         << maxProduct(arr);

    return 0;
}
```

**Output:**

```text
Maximum Product: 6
```

### Complexity

- Time Complexity: O(n²)
- Auxiliary Space: O(1)

## 4. Approach 2: Optimized Approach

Is approach mein hum maximum aur minimum product dono track karenge.

### Important Variables

- `maxEnding`: Current position par end hone wale subarrays ka maximum product.
- `minEnding`: Current position par end hone wale subarrays ka minimum product.
- `answer`: Overall maximum product.

### Logic

Har element ke liye 3 possibilities hoti hain:

1. Current element khud ek naya subarray start kare.
2. Current element ko previous maximum product se multiply kare.
3. Current element ko previous minimum product se multiply kare.

**Formulas:**

```cpp
newMax = max({arr[i], arr[i] * oldMax, arr[i] * oldMin});

newMin = min({arr[i], arr[i] * oldMax, arr[i] * oldMin});
```

Old values ko use karna important hai.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int maxProduct(vector<int>& arr) {

    int maxEnding = arr[0];
    int minEnding = arr[0];

    int answer = arr[0];

    for (int i = 1; i < arr.size(); i++) {

        int oldMax = maxEnding;
        int oldMin = minEnding;

        maxEnding = max({
            arr[i],
            arr[i] * oldMax,
            arr[i] * oldMin
        });

        minEnding = min({
            arr[i],
            arr[i] * oldMax,
            arr[i] * oldMin
        });

        answer = max(answer, maxEnding);
    }

    return answer;
}

int main() {

    vector<int> arr = {2, 3, -2, 4};

    cout << "Maximum Product: "
         << maxProduct(arr);

    return 0;
}
```

**Output:**

```text
Maximum Product: 6
```

## 5. Dry Run

Array:

```cpp
arr[] = {2, 3, -2, 4};
```

Initial values:

```text
maxEnding = 2
minEnding = 2
answer = 2
```

| Element | maxEnding | minEnding | answer |
| ------: | --------: | --------: | -----: |
|       2 |         2 |         2 |      2 |
|       3 |         6 |         3 |      6 |
|      -2 |        -2 |       -12 |      6 |
|       4 |         4 |       -48 |      6 |

Final Answer:

```text
Maximum Product = 6
```

## 6. Zero Ka Special Case

Example:

```cpp
arr[] = {-2, 0, -1};
```

Zero product ko reset karta hai.

Optimized approach mein current element ko khud se start karne ka option diya gaya hai, isliye zero ke baad naya subarray start ho sakta hai.

**Output:**

```text
Maximum Product = 0
```

## 7. All Negative Numbers

Example:

```cpp
arr[] = {-2, -3, -4};
```

Maximum product:

```text
(-2) × (-3) × (-4) = -24
```

Lekin maximum product `12` hai, jo subarray `{-3, -4}` se milta hai.

**Output:**

```text
Maximum Product = 12
```

## 8. Time and Space Complexity

| Approach    | Time Complexity | Auxiliary Space |
| ----------- | --------------- | --------------- |
| Brute Force | O(n²)           | O(1)            |
| Optimized   | O(n)            | O(1)            |

Optimized approach har element ko sirf ek baar process karti hai.

## 9. Common Mistakes

1. Sirf maximum product track karna.
2. Minimum product track na karna.
3. Negative number ke effect ko ignore karna.
4. Zero ke case ko samajh na paana.
5. `oldMax` aur `oldMin` save kiye bina values update karna.
6. `answer = 1` initialize karna; all-negative cases mein problem ho sakti hai.
7. Integer overflow ka dhyan na rakhna. Large values ke liye `long long` use karna better hai.

## 10. Practice Questions

1. `{2, 3, -2, 4}` ka maximum product find karo.
2. `{-2, 3, -4}` solve karo.
3. `{-2, 0, -1}` solve karo.
4. `{-3, -1, -2}` solve karo.
5. `{0, 2, 0, 3}` solve karo.
6. Brute Force aur Optimized approaches implement karo.

## 11. Quick Revision

- Goal = Maximum Product Subarray find karna.
- Subarray continuous elements ka group hota hai.
- Positive × Positive = Positive.
- Negative × Negative = Positive.
- Zero product ko reset kar sakta hai.
- Maximum aur Minimum dono products track karte hain.
- Brute Force: O(n²).
- Optimized: O(n).
- Auxiliary Space: O(1).

## 12. Topic Completion Checklist

- [ ] Maximum Product Subarray samajh liya.
- [ ] Negative numbers ka effect samajh liya.
- [ ] Brute Force approach samajh li.
- [ ] Optimized approach samajh li.
- [ ] Zero aur all-negative cases samajh liye.
- [ ] C++ code run kar liya.
- [ ] Dry Run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 26: Move All Zeroes to the End of an Array**
