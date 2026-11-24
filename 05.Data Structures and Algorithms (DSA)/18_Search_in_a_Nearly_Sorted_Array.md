# Topic 18: Search in a Nearly Sorted Array

## 1. Nearly Sorted Array Kya Hota Hai?

Nearly Sorted Array wo array hota hai jisme elements almost sorted order mein hote hain, lekin kuch elements apni correct position se ek index left ya right shift ho sakte hain.

**Example:**

```cpp
arr[] = {10, 20, 30, 50, 40, 60, 70};
```

Yahan `40` aur `50` ki positions interchange hain.

Normal sorted array:

```cpp
{10, 20, 30, 40, 50, 60, 70}
```

Nearly sorted array:

```cpp
{10, 20, 30, 50, 40, 60, 70}
```

## 2. Normal Binary Search Se Difference

Normal Binary Search mein hum sirf `mid` element check karte hain.

Lekin Nearly Sorted Array mein kisi element ki correct position se ek index left ya right shift hone ki possibility hoti hai.

Isliye humein 3 positions check karni hoti hain:

- `mid`
- `mid - 1`
- `mid + 1`

## 3. Algorithm

1. `low = 0` aur `high = n - 1` initialize karo.
2. Middle index calculate karo.
3. Check karo ki `arr[mid] == target` hai ya nahi.
4. Check karo ki `arr[mid - 1] == target` hai ya nahi.
5. Check karo ki `arr[mid + 1] == target` hai ya nahi.
6. Agar target nahi mila:
   - Agar `target < arr[mid]`, toh `high = mid - 2`.
   - Agar `target > arr[mid]`, toh `low = mid + 2`.
7. Jab tak `low <= high`, process repeat karo.
8. Target na mile toh `-1` return karo.

## 4. C++ Code (Iterative Approach)

```cpp
#include <iostream>
using namespace std;

int searchNearlySorted(int arr[], int n, int target) {
    int low = 0;
    int high = n - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        // Check middle element
        if (arr[mid] == target) {
            return mid;
        }

        // Check left element
        if (mid - 1 >= low && arr[mid - 1] == target) {
            return mid - 1;
        }

        // Check right element
        if (mid + 1 <= high && arr[mid + 1] == target) {
            return mid + 1;
        }

        // Search in left half
        if (target < arr[mid]) {
            high = mid - 2;
        }
        // Search in right half
        else {
            low = mid + 2;
        }
    }

    return -1;
}

int main() {
    int arr[] = {10, 20, 30, 50, 40, 60, 70};
    int n = 7;
    int target = 40;

    int result = searchNearlySorted(arr, n, target);

    if (result != -1) {
        cout << "Element found at index: " << result;
    } else {
        cout << "Element not found";
    }

    return 0;
}
```

**Output:**

```text
Element found at index: 4
```

## 5. Dry Run

Array:

```cpp
{10, 20, 30, 50, 40, 60, 70}
```

Target:

```cpp
40
```

| Step | low | high | mid | arr[mid] | Action                   |
| ---- | --: | ---: | --: | -------: | ------------------------ |
| 1    |   0 |    6 |   3 |       50 | Left and right check     |
| 2    |   0 |    6 |   3 |       50 | `arr[mid+1] = 40`, found |

Target index = `4`.

## 6. Time and Space Complexity

| Case            | Complexity |
| --------------- | ---------- |
| Best Case       | O(1)       |
| Average Case    | O(log n)   |
| Worst Case      | O(log n)   |
| Auxiliary Space | O(1)       |

**Reason:** Har iteration mein hum 3 nearby positions check karte hain aur search space approximately half ho jata hai.

## 7. Important Conditions

- Array nearly sorted hona chahiye.
- Har element maximum ek position left ya right shifted ho sakta hai.
- Array ka order ascending hona chahiye, except these small shifts.
- Code mein `mid - 1` aur `mid + 1` check karne se pehle boundaries verify karni zaroori hain.

## 8. Common Mistakes

1. Sirf `arr[mid]` check karna.
2. `mid - 1` ya `mid + 1` ki boundary check nahi karna.
3. `high = mid - 1` aur `low = mid + 1` use karna; yahan `mid - 2` aur `mid + 2` use hoga.
4. Normal unsorted array par Binary Search apply karna.
5. Nearly sorted array ki condition samjhe bina algorithm use karna.

## 9. Practice Questions

1. Nearly Sorted Array mein target `30` search karo.
2. Target `70` search karke index find karo.
3. Aisa target search karo jo array mein present nahi hai.
4. Function ko user input ke saath implement karo.
5. Nearly Sorted Array aur Normal Sorted Array mein difference likho.

## 10. Quick Revision

- Nearly Sorted Array mein elements maximum one position left ya right shifted ho sakte hain.
- Binary Search ka modified version use hota hai.
- Har iteration mein `mid`, `mid-1`, `mid+1` check karte hain.
- Left search: `high = mid - 2`.
- Right search: `low = mid + 2`.
- Time Complexity: O(log n).
- Auxiliary Space: O(1).

## 11. Topic Completion Checklist

- [ ] Nearly Sorted Array ka meaning samajh liya.
- [ ] Normal Binary Search se difference samajh liya.
- [ ] Algorithm samajh liya.
- [ ] C++ code practice kar liya.
- [ ] Dry Run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 19: Search in a 2D Matrix**
