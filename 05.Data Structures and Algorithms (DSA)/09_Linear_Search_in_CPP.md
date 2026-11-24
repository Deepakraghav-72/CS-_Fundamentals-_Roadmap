# Topic 09 – Linear Search in C++

## 1. Searching kya hoti hai?

Searching ek process hai jisme hum kisi data structure ke andar kisi particular element ko find karte hain.

Example:

```cpp
int arr[5] = {10, 20, 30, 40, 50};
int target = 30;
```

Humein array mein 30 ko find karna hai.

Searching ke main types:

1. Linear Search
2. Binary Search

## 2. Linear Search kya hoti hai?

Linear Search ek simple searching algorithm hai jo array ke elements ko starting se one by one check karta hai.

Jab target element mil jata hai, toh search stop ho sakti hai.

Agar element nahi milta, toh poora array check karna padta hai.

## 3. Linear Search ka Working Process

Example:

```cpp
int arr[5] = {10, 20, 30, 40, 50};
int target = 30;
```

Searching process:

| Step | Element | Comparison |
| ---- | ------- | ---------- |
| 1    | 10      | Not Found  |
| 2    | 20      | Not Found  |
| 3    | 30      | Found      |

Element 30 index 2 par present hai.

## 4. Linear Search ka Algorithm

1. Array aur target element lo.
2. First element se searching start karo.
3. Current element ko target se compare karo.
4. Agar match milta hai, toh index return karo.
5. Agar match nahi milta, toh next element par jao.
6. Agar poora array check ho jaye aur element na mile, toh -1 return karo.

## 5. Linear Search ka C++ Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int target = 30;

    for (int i = 0; i < 5; i++) {
        if (arr[i] == target) {
            cout << "Element Found at Index: " << i;
            return 0;
        }
    }

    cout << "Element Not Found";

    return 0;
}
```

Output:

```text
Element Found at Index: 2
```

## 6. Linear Search using Function

Function ki help se Linear Search implement kar sakte hain.

```cpp
#include <iostream>
using namespace std;

int linearSearch(int arr[], int n, int target) {

    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            return i;
        }
    }

    return -1;
}

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = 5;
    int target = 40;

    int result = linearSearch(arr, n, target);

    if (result != -1) {
        cout << "Element Found at Index: " << result;
    }
    else {
        cout << "Element Not Found";
    }

    return 0;
}
```

Output:

```text
Element Found at Index: 3
```

## 7. Linear Search ke Cases

### A. Best Case

Jab target first position par mil jata hai.

Example:

```cpp
int arr[] = {10, 20, 30, 40};
int target = 10;
```

Sirf 1 comparison hoga.

Time Complexity = O(1)

### B. Average Case

Jab target generally beech ki position par milta hai.

Time Complexity = O(n)

### C. Worst Case

Jab target last position par ho ya array mein present na ho.

Time Complexity = O(n)

## 8. Linear Search ki Space Complexity

Iterative Linear Search mein fixed extra variables use hote hain.

**Auxiliary Space = O(1)**

## 9. Linear Search ke Advantages

1. Simple aur easy algorithm.
2. Sorted array ki requirement nahi hoti.
3. Small datasets ke liye useful.
4. Extra memory ki zaroorat nahi hoti.
5. Arrays aur linked lists jaise structures mein use ho sakta hai.

## 10. Linear Search ke Disadvantages

1. Large datasets par slow ho sakta hai.
2. Worst Case mein poora array check karna padta hai.
3. Binary Search ke comparison mein sorted arrays par generally less efficient hai.

## 11. Linear Search vs Binary Search

| Feature     | Linear Search    | Binary Search           |
| ----------- | ---------------- | ----------------------- |
| Working     | One by one check | Half mein divide        |
| Sorted Data | Not required     | Required                |
| Best Case   | O(1)             | O(1)                    |
| Worst Case  | O(n)             | O(log n)                |
| Difficulty  | Easy             | Comparatively difficult |

## 12. Common Mistakes

1. Loop ki condition galat likhna.
2. Index aur element value confuse karna.
3. Element nahi milne par -1 return na karna.
4. Array size galat pass karna.
5. Duplicate elements hone par first occurrence aur last occurrence ka difference ignore karna.

## 13. Practice Questions

1. Linear Search kya hoti hai?
2. Kya Linear Search ke liye sorted array zaroori hai?
3. Linear Search ka Best Case kya hai?
4. Linear Search ka Worst Case kya hai?
5. Linear Search ki Auxiliary Space Complexity kya hai?
6. Linear Search ka function banao jo element ka index return kare.
7. Array mein kisi element ki occurrence count karo.
8. Array mein kisi element ka last occurrence find karo.

## Quick Revision

- Linear Search = One by one searching.
- Sorted Array = Not Required.
- Best Case = O(1).
- Average Case = O(n).
- Worst Case = O(n).
- Auxiliary Space = O(1).
- Element Found = Index return.
- Element Not Found = -1 return.

## Topic Status

**Topic 09 – Completed**

**Next Topic 10:** Binary Search in C++.
