# Topic 02 – Introduction to Time and Space Complexity

## 1. Algorithm Complexity kya hoti hai?

Algorithm Complexity ka matlab hai kisi algorithm ko execute karne mein kitna time aur memory lagti hai.

DSA mein hum mainly do cheezein study karte hain:

1. Time Complexity – Code execute hone mein operations kitne lagte hain.
2. Space Complexity – Code execute hone mein kitni memory use hoti hai.

## 2. Time Complexity kya hoti hai?

Time Complexity batati hai ki input size (n) badhne par algorithm ke operations kitne badhte hain.

Example:

```cpp
int arr[5] = {10, 20, 30, 40, 50};

cout << arr[0];
```

Yahan sirf ek operation ho raha hai.

**Time Complexity: O(1)**

## 3. Space Complexity kya hoti hai?

Space Complexity batati hai ki algorithm execute hone ke dauran kitni memory use karta hai.

Example:

```cpp
int a = 10;
int b = 20;
int sum = a + b;
```

Yahan 3 integer variables memory use kar rahe hain.

**Auxiliary Space: O(1)**

## 4. Best Case, Average Case aur Worst Case

| Case         | Meaning                |
| ------------ | ---------------------- |
| Best Case    | Sabse kam operations   |
| Average Case | Average operations     |
| Worst Case   | Sabse zyada operations |

Example: Array mein 10 search karna.

```cpp
int arr[5] = {10, 20, 30, 40, 50};
```

- Best Case: Element first position par mile.
- Average Case: Element beech mein mile.
- Worst Case: Element last position par mile ya present na ho.

## 5. Big O Notation kya hai?

Big O Notation algorithm ki growth rate ko represent karta hai.

Isse pata chalta hai ki input size badhne par algorithm ke operations kis speed se badhenge.

### Important Big O Notations

| Notation   | Name         |
| ---------- | ------------ |
| O(1)       | Constant     |
| O(log n)   | Logarithmic  |
| O(n)       | Linear       |
| O(n log n) | Linearithmic |
| O(n²)      | Quadratic    |
| O(2ⁿ)      | Exponential  |
| O(n!)      | Factorial    |

## 6. O(1) – Constant Time

Jab input size badhne par bhi operations ki sankhya constant rahe.

```cpp
int arr[5] = {10, 20, 30, 40, 50};

cout << arr[2];
```

Output:

```text
30
```

**Time Complexity: O(1)**

## 7. O(n) – Linear Time

Jab operations input size ke according badhte hain.

```cpp
int n = 5;

for (int i = 0; i < n; i++) {
    cout << i << " ";
}
```

Output:

```text
0 1 2 3 4
```

**Time Complexity: O(n)**

## 8. O(n²) – Quadratic Time

Jab ek loop ke andar doosra loop execute hota hai.

```cpp
int n = 3;

for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << i << " " << j << endl;
    }
}
```

Total operations = 3 × 3 = 9

**Time Complexity: O(n²)**

## 9. O(log n) – Logarithmic Time

Jab har step mein input approximately half ho jata hai.

Example: Binary Search.

```cpp
while (low <= high) {
    int mid = low + (high - low) / 2;

    if (arr[mid] == target) {
        break;
    }
    else if (arr[mid] < target) {
        low = mid + 1;
    }
    else {
        high = mid - 1;
    }
}
```

**Time Complexity: O(log n)**

Note: Binary Search ke liye sorted array hona zaroori hai.

## 10. Complexity Comparison

| Complexity | Performance    |
| ---------- | -------------- |
| O(1)       | Excellent      |
| O(log n)   | Very Good      |
| O(n)       | Good           |
| O(n log n) | Good           |
| O(n²)      | Slow           |
| O(2ⁿ)      | Very Slow      |
| O(n!)      | Extremely Slow |

## 11. Important Rules of Time Complexity

1. Constant values ignore karte hain.
2. Lower-order terms ignore karte hain.
3. Nested loops mein generally multiplication hoti hai.
4. Consecutive loops mein complexities add hoti hain.
5. Big O growth ka upper bound represent karta hai.

Example:

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}

for (int j = 0; j < n; j++) {
    cout << j;
}
```

Complexity:

O(n) + O(n) = O(2n) = O(n)

## 12. Common Mistakes

- Time Complexity ko actual seconds samajhna.
- Har loop ko O(n) samajhna.
- Nested loops ki complexity ko add karna.
- Auxiliary Space aur Total Space ko same samajhna.
- Binary Search ko unsorted array par apply karna.

## 13. Practice Questions

1. Single loop ki Time Complexity kya hoti hai?
2. Nested loops ki complexity kya hogi?
3. Binary Search ki complexity kya hai?
4. O(1) aur O(n) mein kya difference hai?
5. Agar loop n baar chale, toh complexity kya hogi?

## Quick Revision

- Time Complexity = Operations ki growth.
- Space Complexity = Memory usage.
- Big O = Growth ka upper bound.
- O(1) = Constant.
- O(n) = Linear.
- O(n²) = Quadratic.
- O(log n) = Logarithmic.

## Topic Status

**Topic 02 – Completed**

**Next Topic 03:** Asymptotic Notations – Big O, Omega (Ω) and Theta (Θ).
