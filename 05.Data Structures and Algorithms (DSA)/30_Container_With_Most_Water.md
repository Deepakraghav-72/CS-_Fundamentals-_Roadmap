# Topic 30: Container With Most Water

## 1. Problem Kya Hai?

Humein ek integer array diya hota hai. Har element ek vertical line ki height represent karta hai.

Humein aisi 2 lines select karni hain jo milkar maximum water store kar sakein.

**Example:**

```cpp
height[] = {1, 8, 6, 2, 5, 4, 8, 3, 7};
```

Output:

```text
Maximum Water = 49
```

## 2. Water Calculate Kaise Hoga?

Container ka area calculate karne ka formula:

```text
Area = Width × Height
```

Where:

- Width = Dono lines ke indices ka difference.
- Height = Dono lines mein se minimum height.

Formula:

```text
Area = (j - i) × min(height[i], height[j])
```

**Example:**

```text
height[i] = 8
height[j] = 7

Width = 7 - 1 = 6
Height = min(8, 7) = 7

Area = 6 × 7 = 42
```

## 3. Approach 1: Brute Force

Is approach mein hum har possible pair of lines check karenge.

### Algorithm

1. Ek variable `maxArea = 0` initialize karo.
2. First loop se first line select karo.
3. Second loop se second line select karo.
4. Width aur minimum height calculate karo.
5. Area calculate karo.
6. Maximum area update karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int maxArea(vector<int>& height) {

    int n = height.size();

    int maxArea = 0;

    for (int i = 0; i < n; i++) {

        for (int j = i + 1; j < n; j++) {

            int width = j - i;

            int h = min(height[i], height[j]);

            int area = width * h;

            maxArea = max(maxArea, area);
        }
    }

    return maxArea;
}

int main() {

    vector<int> height = {1, 8, 6, 2, 5, 4, 8, 3, 7};

    cout << "Maximum Water = " << maxArea(height);

    return 0;
}
```

**Output:**

```text
Maximum Water = 49
```

### Complexity

- Time Complexity: O(n²)
- Auxiliary Space: O(1)

## 4. Approach 2: Two Pointer (Optimized)

Ye problem Two Pointer technique se efficiently solve hoti hai.

Hum 2 pointers use karenge:

- `left`: Array ke starting index par.
- `right`: Array ke ending index par.

### Algorithm

1. `left = 0` initialize karo.
2. `right = n - 1` initialize karo.
3. Dono pointers ke beech width calculate karo.
4. Minimum height calculate karo.
5. Area calculate karke maximum update karo.
6. Jis pointer ki height chhoti hai, usko move karo.
7. Jab tak `left < right`, process repeat karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int maxArea(vector<int>& height) {

    int left = 0;

    int right = height.size() - 1;

    int maxArea = 0;

    while (left < right) {

        int width = right - left;

        int h = min(height[left], height[right]);

        int area = width * h;

        maxArea = max(maxArea, area);

        if (height[left] < height[right]) {
            left++;
        }
        else {
            right--;
        }
    }

    return maxArea;
}

int main() {

    vector<int> height = {1, 8, 6, 2, 5, 4, 8, 3, 7};

    cout << "Maximum Water = " << maxArea(height);

    return 0;
}
```

**Output:**

```text
Maximum Water = 49
```

## 5. Dry Run

Initial Array:

```text
{1, 8, 6, 2, 5, 4, 8, 3, 7}
```

Initially:

```cpp
left = 0;
right = 8;
maxArea = 0;
```

| Left | Right | Width | Height | Area | Max Area |
| ---: | ----: | ----: | -----: | ---: | -------: |
|    0 |     8 |     8 |      1 |    8 |        8 |
|    1 |     8 |     7 |      7 |   49 |       49 |
|    1 |     7 |     6 |      3 |   18 |       49 |
|    1 |     6 |     5 |      8 |   40 |       49 |
|    1 |     5 |     4 |      4 |   16 |       49 |
|    1 |     4 |     3 |      5 |   15 |       49 |
|    1 |     3 |     2 |      2 |    4 |       49 |
|    1 |     2 |     1 |      6 |    6 |       49 |

Final Answer:

```text
Maximum Water = 49
```

## 6. Two Pointer Logic Samjho

Important question: Hum smaller height wale pointer ko hi move kyun karte hain?

**Reason:**

Area ka formula hai:

```text
Area = Width × Minimum Height
```

Agar hum larger height wale pointer ko move karte hain:

- Width kam ho jayegi.
- Minimum height improve hone ki guarantee nahi hai.
- Isliye better area milne ka chance nahi badhta.

Smaller height wale pointer ko move karne par humein larger height milne ka chance milta hai.

Isi wajah se Two Pointer approach efficient hai.

## 7. Time and Space Complexity

| Approach    | Time Complexity | Auxiliary Space |
| ----------- | --------------- | --------------- |
| Brute Force | O(n²)           | O(1)            |
| Two Pointer | O(n)            | O(1)            |

**Best Approach:** Two Pointer.

## 8. Common Mistakes

1. Height calculate karte waqt `max()` use karna.
2. Width calculate karte waqt `right - left` ki jagah galat formula use karna.
3. Smaller height wale pointer ko move na karna.
4. `left < right` condition bhool jana.
5. Area ko update karna bhool jana.

## 9. Practice Questions

1. `{1, 1}` ka maximum area calculate karo.
2. `{4, 3, 2, 1, 4}` solve karo.
3. `{1, 2, 1}` solve karo.
4. Brute Force approach implement karo.
5. Two Pointer approach ka dry run khud karo.

## 10. Quick Revision

- Problem: Maximum water store karne wala container find karna.
- Formula: `(right - left) * min(height[left], height[right])`.
- Technique: Two Pointers.
- Smaller height wala pointer move hota hai.
- Brute Force Time: O(n²).
- Optimized Time: O(n).
- Auxiliary Space: O(1).

## 11. Topic Completion Checklist

- [ ] Problem samajh li.
- [ ] Area formula samajh li.
- [ ] Brute Force approach samajh li.
- [ ] Two Pointer approach samajh li.
- [ ] Dry Run kar liya.
- [ ] C++ code run kar liya.
- [ ] Practice questions solve kar liye.

---

**Topic 30 Complete — Is agreed 30-topic sequence ka final topic.**
