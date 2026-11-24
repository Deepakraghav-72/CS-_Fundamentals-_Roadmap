# 10. Binary Search in C++

## 1. Binary Search Kya Hai?

Binary Search ek searching algorithm hai jo **sorted array** mein kisi element ko efficiently search karta hai.

Isme hum array ke middle element ko check karte hain:

- Agar middle element target ke equal hai, element mil gaya.
- Agar target middle element se chhota hai, left half mein search karte hain.
- Agar target middle element se bada hai, right half mein search karte hain.

Har step mein search area aadha ho jata hai.

**Important:** Binary Search lagane ke liye array ka sorted hona zaroori hai.

## 2. Binary Search Ka Example

Sorted Array:

```cpp
arr = {10, 20, 30, 40, 50, 60, 70};
```

Target:

```cpp
target = 50;
```

Initially:

```cpp
low = 0;
high = 6;
```

### Step 1

Middle index:

```cpp
mid = (0 + 6) / 2 = 3;
```

`arr[3] = 40`

Target 50, middle element 40 se bada hai.

Isliye right half mein search karenge:

```cpp
low = mid + 1;
low = 4;
```

### Step 2

Ab:

```cpp
low = 4;
high = 6;
mid = (4 + 6) / 2 = 5;
```

`arr[5] = 60`

Target 50, middle element 60 se chhota hai.

Isliye left half mein search karenge:

```cpp
high = mid - 1;
high = 4;
```

### Step 3

Ab:

```cpp
low = 4;
high = 4;
mid = (4 + 4) / 2 = 4;
```

`arr[4] = 50`

Target mil gaya!

**Answer: Index 4**

## 3. Binary Search Ka Algorithm

1. `low = 0` set karo.
2. `high = n - 1` set karo.
3. Jab tak `low <= high` ho:
   - Middle index calculate karo.
   - Agar `arr[mid] == target`, index return karo.
   - Agar `target < arr[mid]`, `high = mid - 1` karo.
   - Agar `target > arr[mid]`, `low = mid + 1` karo.
4. Agar element nahi milta, `-1` return karo.

## 4. Binary Search in C++ (Iterative Method)

```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int n, int target) {
    int low = 0;
    int high = n - 1;

    while (low <= high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] == target) {
            return mid;
        }
        else if (target < arr[mid]) {
            high = mid - 1;
        }
        else {
            low = mid + 1;
        }
    }

    return -1;
}

int main() {
    int arr[] = {10, 20, 30, 40, 50, 60, 70};
    int n = 7;

    int target = 50;

    int result = binarySearch(arr, n, target);

    if (result != -1) {
        cout << "Element found at index: " << result;
    }
    else {
        cout << "Element not found";
    }

    return 0;
}
```

**Output:**

```text
Element found at index: 4
```

## 5. Important Variables

| Variable | Meaning                         |
| -------- | ------------------------------- |
| `low`    | Search range ka starting index  |
| `high`   | Search range ka ending index    |
| `mid`    | Middle index                    |
| `target` | Jis element ko search karna hai |
| `n`      | Array ke total elements         |

## 6. Mid Calculate Karne Ka Formula

Common formula:

```cpp
mid = (low + high) / 2;
```

Better formula:

```cpp
mid = low + (high - low) / 2;
```

Second formula integer overflow ke risk ko reduce karta hai jab indexes bahut bade hon.

## 7. Binary Search Ki Time Complexity

| Case         | Time Complexity | Meaning                                               |
| ------------ | --------------- | ----------------------------------------------------- |
| Best Case    | O(1)            | Target first middle position par mil jaye             |
| Average Case | O(log n)        | Search area baar-baar half hota hai                   |
| Worst Case   | O(log n)        | Maximum halving steps ke baad element mile ya na mile |

**Space Complexity (Iterative):** O(1)

Iterative Binary Search mein extra memory constant rehti hai.

## 8. Binary Search vs Linear Search

| Feature          | Linear Search                     | Binary Search              |
| ---------------- | --------------------------------- | -------------------------- |
| Searching method | One by one                        | Middle element check       |
| Sorted array     | Required nahi                     | Required                   |
| Best Case        | O(1)                              | O(1)                       |
| Average Case     | O(n)                              | O(log n)                   |
| Worst Case       | O(n)                              | O(log n)                   |
| Efficiency       | Large data par comparatively slow | Large sorted data par fast |

## 9. Binary Search Ke Common Mistakes

1. **Unsorted array par Binary Search lagana:** Result incorrect ho sakta hai.
2. **Wrong condition:** Loop mein `low <= high` use karna hai.
3. **Wrong update:** Left search ke liye `high = mid - 1`.
4. **Wrong update:** Right search ke liye `low = mid + 1`.
5. **Mid formula:** Safe formula use karo:
   ```cpp
   mid = low + (high - low) / 2;
   ```
6. **Element not found:** Search complete hone par `-1` return karo.

## 10. Duplicate Elements

Agar array mein duplicate elements hain:

```cpp
int arr[] = {10, 20, 20, 20, 30};
```

Normal Binary Search matching element ka **koi bhi valid index** return kar sakta hai. Zaroori nahi ki first occurrence hi return kare.

First ya last occurrence find karne ke liye modified Binary Search use hoti hai. Ye aage alag topic mein padhenge.

## 11. Practice Questions

1. Binary Search kya hai?
2. Binary Search ke liye array sorted hona kyun zaroori hai?
3. `low`, `high` aur `mid` ka kya kaam hai?
4. Binary Search ki worst-case time complexity kya hai?
5. Agar target `mid` se chhota ho, toh kya update karenge?
6. Agar target array mein nahi hai, toh function kya return karega?
7. Linear Search aur Binary Search mein kya difference hai?

### Coding Practice

**Question 1:** Sorted array mein 30 search karo.

```cpp
int arr[] = {10, 20, 30, 40, 50};
```

**Question 2:** Array mein 100 search karo. Agar nahi mile toh `Element not found` print karo.

**Question 3:** User se target input lekar Binary Search perform karo.

## 12. Quick Revision

- Binary Search ek efficient searching algorithm hai.
- Ye sirf sorted data par correctly work karta hai.
- Search range ko har step mein half karta hai.
- `low` starting index hota hai.
- `high` ending index hota hai.
- `mid` middle index hota hai.
- Best Time Complexity = O(1).
- Average/Worst Time Complexity = O(log n).
- Iterative Space Complexity = O(1).
- Element na milne par `-1` return karte hain.

## 13. Topic Status

- [x] Binary Search Introduction
- [x] Binary Search Algorithm
- [x] Iterative C++ Implementation
- [x] Time and Space Complexity
- [x] Linear vs Binary Search
- [x] Common Mistakes
- [x] Practice Questions

**Next Topic 11:** Recursive Binary Search in C++
