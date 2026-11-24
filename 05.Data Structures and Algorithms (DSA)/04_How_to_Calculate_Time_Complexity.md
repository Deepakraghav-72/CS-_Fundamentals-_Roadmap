# Topic 04 – How to Calculate Time Complexity

## 1. Time Complexity Calculate kaise karte hain?

Time Complexity calculate karne ka matlab hai code mein hone wale operations ki growth ko identify karna.

Iske liye humein loops, nested loops, conditions aur function calls ko analyze karna hota hai.

## 2. Rule 1 – Simple Statement

Agar code mein simple statements hain, toh unki Time Complexity O(1) hoti hai.

Example:

```cpp
int a = 10;
int b = 20;
int sum = a + b;

cout << sum;
```

Total operations constant hain.

**Time Complexity: O(1)**

## 3. Rule 2 – Single Loop

Agar loop n times execute hota hai, toh complexity O(n) hoti hai.

Example:

```cpp
for (int i = 0; i < n; i++) {
    cout << i << endl;
}
```

Loop n times chalega.

**Time Complexity: O(n)**

## 4. Rule 3 – Nested Loops

Jab ek loop ke andar doosra loop hota hai, toh generally dono ki complexities multiply hoti hain.

Example:

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << i << " " << j << endl;
    }
}
```

Outer Loop = n

Inner Loop = n

Total Operations = n × n = n²

**Time Complexity: O(n²)**

## 5. Rule 4 – Consecutive Loops

Jab multiple loops ek ke baad ek execute hote hain, toh complexities add hoti hain.

Example:

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}

for (int j = 0; j < n; j++) {
    cout << j;
}
```

First Loop = O(n)

Second Loop = O(n)

Total = O(n) + O(n)

= O(2n)

Constant ignore karne par:

**Time Complexity: O(n)**

## 6. Rule 5 – Different Nested Loops

Agar nested loops ki limits different hain, toh unhe separately calculate karo.

Example:

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < 5; j++) {
        cout << i << " " << j << endl;
    }
}
```

Outer Loop = n

Inner Loop = 5

Total = n × 5

O(5n) = O(n)

**Time Complexity: O(n)**

## 7. Rule 6 – Loop Increment by 2

Agar loop variable har baar 2 se increase hota hai, toh bhi complexity O(n) hoti hai.

Example:

```cpp
for (int i = 0; i < n; i += 2) {
    cout << i << endl;
}
```

Loop approximately n/2 times chalega.

O(n/2) = O(n)

**Time Complexity: O(n)**

## 8. Rule 7 – Loop Multiplication by 2

Agar har iteration mein variable double hota hai, toh complexity O(log n) hoti hai.

Example:

```cpp
for (int i = 1; i < n; i *= 2) {
    cout << i << endl;
}
```

Values:

1, 2, 4, 8, 16, 32...

**Time Complexity: O(log n)**

## 9. Rule 8 – Conditions (if-else)

Conditions mein execution path ke according complexity calculate hoti hai.

Example:

```cpp
if (n > 0) {
    cout << "Positive";
}
else {
    cout << "Negative";
}
```

Dono branches mein constant operations hain.

**Time Complexity: O(1)**

Example 2:

```cpp
if (n > 0) {
    for (int i = 0; i < n; i++) {
        cout << i;
    }
}
else {
    cout << "Invalid";
}
```

Worst Case mein loop execute hoga.

**Time Complexity: O(n)**

## 10. Rule 9 – Loop Inside a Loop with Different Variables

Example:

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        cout << i << " " << j << endl;
    }
}
```

Outer Loop = n

Inner Loop = m

Total Operations = n × m

**Time Complexity: O(n × m)**

Important: Jab n aur m independent input sizes hon, tab dono ko alag rakhna zaroori hai.

## 11. Rule 10 – Loop Dividing by 2

Jab har iteration mein value half hoti hai, toh complexity O(log n) hoti hai.

Example:

```cpp
for (int i = n; i > 1; i /= 2) {
    cout << i << endl;
}
```

Values approximately:

n, n/2, n/4, n/8...

**Time Complexity: O(log n)**

## 12. Important Time Complexity Rules

| Code Pattern         | Complexity |
| -------------------- | ---------- |
| Simple Statement     | O(1)       |
| Single Loop          | O(n)       |
| Nested Loop          | O(n²)      |
| Three Nested Loops   | O(n³)      |
| Consecutive Loops    | O(n)       |
| Loop with i += 2     | O(n)       |
| Loop with i *= 2     | O(log n)   |
| Loop with i /= 2     | O(log n)   |
| Nested n and m loops | O(n × m)   |

## 13. Common Mistakes

1. Har loop ko O(n) samajhna.
2. Consecutive loops ko multiply karna.
3. Nested loops ko add karna.
4. Constants ko final complexity mein include karna.
5. i *= 2 aur i += 2 ko same samajhna.
6. Independent variables n aur m ko combine kar dena.

## 14. Practice Questions

In codes ki Time Complexity calculate karo:

### Question 1

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}
```

### Question 2

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << i;
    }
}
```

### Question 3

```cpp
for (int i = 1; i < n; i *= 2) {
    cout << i;
}
```

### Question 4

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}

for (int j = 0; j < n; j++) {
    cout << j;
}
```

### Question 5

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
        cout << i + j;
    }
}
```

## Quick Revision

- Simple Statement = O(1)
- Single Loop = O(n)
- Nested Loop = O(n²)
- Three Nested Loops = O(n³)
- Consecutive Loops = Addition
- Nested Loops = Multiplication
- i *= 2 = O(log n)
- i /= 2 = O(log n)
- i += 2 = O(n)

## Topic Status

**Topic 04 – Completed**

**Next Topic 05:** Space Complexity Analysis in C++.
