# Topic 08 – Array Traversal and Array Operations in C++

## 1. Array Traversal kya hota hai?

Array Traversal ka matlab hai array ke har element ko one by one access karna.

Traversal ke liye generally loops use kiye jaate hain.

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

Time Complexity = O(n)

## 2. Array Operations kya hote hain?

Array par perform kiye jaane wale common operations ko Array Operations kehte hain.

Important operations:

1. Traversal
2. Insertion
3. Deletion
4. Searching
5. Updating
6. Accessing

## 3. Accessing an Array Element

Array ke kisi particular element ko index ki help se access karna Accessing kehlata hai.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    cout << arr[2];

    return 0;
}
```

Output:

```text
30
```

Time Complexity = O(1)

## 4. Updating an Array Element

Array ke kisi existing element ki value change karna Updating kehlata hai.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    arr[2] = 100;

    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
10 20 100 40 50
```

Time Complexity = O(1)

## 5. Insertion in Array

Array mein kisi new element ko add karna Insertion kehlata hai.

Insertion generally 3 ways se ho sakta hai:

1. Beginning mein
2. End mein
3. Kisi particular position par

### A. Insertion at Beginning

Beginning mein element insert karne ke liye existing elements ko right shift karna padta hai.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[10] = {10, 20, 30, 40, 50};
    int n = 5;

    int value = 5;

    for (int i = n; i > 0; i--) {
        arr[i] = arr[i - 1];
    }

    arr[0] = value;
    n++;

    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
5 10 20 30 40 50
```

Time Complexity = O(n)

### B. Insertion at End

End mein element insert karne ke liye next available index par value store karte hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[10] = {10, 20, 30, 40, 50};
    int n = 5;

    arr[n] = 60;
    n++;

    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
10 20 30 40 50 60
```

Time Complexity = O(1)

Note: Yeh O(1) tab hai jab array mein extra capacity available ho aur shifting ki zaroorat na ho.

### C. Insertion at Specific Position

Kisi particular position par element insert karne ke liye elements ko right shift karte hain.

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[10] = {10, 20, 30, 40, 50};
    int n = 5;

    int position = 2;
    int value = 100;

    for (int i = n; i > position; i--) {
        arr[i] = arr[i - 1];
    }

    arr[position] = value;
    n++;

    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
10 20 100 30 40 50
```

Time Complexity = O(n)

Note: Yahan position zero-based index hai.

## 6. Deletion from Array

Array se kisi existing element ko remove karna Deletion kehlata hai.

Deletion ke baad elements ko generally left shift karna padta hai.

Example: Beginning se deletion.

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int n = 5;

    for (int i = 0; i < n - 1; i++) {
        arr[i] = arr[i + 1];
    }

    n--;

    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
20 30 40 50
```

Time Complexity = O(n)

## 7. Deletion at Specific Position

Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int n = 5;

    int position = 2;

    for (int i = position; i < n - 1; i++) {
        arr[i] = arr[i + 1];
    }

    n--;

    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

Output:

```text
10 20 40 50
```

Time Complexity = O(n)

## 8. Searching in Array

Array mein kisi particular element ko find karna Searching kehlata hai.

Example: Linear Search

```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int target = 30;

    for (int i = 0; i < 5; i++) {
        if (arr[i] == target) {
            cout << "Element Found at Index " << i;
            break;
        }
    }

    return 0;
}
```

Output:

```text
Element Found at Index 2
```

Time Complexity:

- Best Case = O(1)
- Worst Case = O(n)

## 9. Array Operations ki Time Complexity

| Operation              | Time Complexity |
| ---------------------- | --------------- |
| Accessing              | O(1)            |
| Updating               | O(1)            |
| Traversal              | O(n)            |
| Insertion at Beginning | O(n)            |
| Insertion at End       | O(1)            |
| Insertion at Position  | O(n)            |
| Deletion at Beginning  | O(n)            |
| Deletion at End        | O(1)            |
| Deletion at Position   | O(n)            |
| Linear Search          | O(n)            |

Note: Insertion at end O(1) tab hai jab capacity available ho. Dynamic arrays mein occasional resizing ke karan append ki amortized complexity O(1) hoti hai.

## 10. Common Mistakes

1. Insertion se pehle array capacity check na karna.
2. Right shifting galat direction mein karna.
3. Deletion ke baad n update na karna.
4. Position aur index confuse karna.
5. Array ke valid index se bahar access karna.
6. Array ki logical size aur actual capacity ko same samajhna.

## 11. Practice Questions

1. Array Traversal kya hota hai?
2. Array mein Accessing ki complexity kya hai?
3. Beginning mein insertion ke liye shifting kyu hoti hai?
4. End mein deletion ki complexity kya hoti hai?
5. Linear Search kya hota hai?
6. Array mein updating kaise karte hain?
7. Insertion aur Deletion mein kya difference hai?
8. Array ki size aur capacity mein kya difference hai?

## Quick Revision

- Traversal = Har element ko access karna.
- Accessing = O(1).
- Updating = O(1).
- Insertion at Beginning = O(n).
- Insertion at End = O(1), if capacity available.
- Deletion at Beginning = O(n).
- Deletion at End = O(1).
- Linear Search = O(n).
- Shifting = Elements ko left ya right move karna.

## Topic Status

**Topic 08 – Completed**

**Next Topic 09:** Linear Search in C++.
