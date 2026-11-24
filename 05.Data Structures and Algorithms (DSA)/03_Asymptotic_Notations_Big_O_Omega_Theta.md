# Topic 03 – Asymptotic Notations (Big O, Omega and Theta)

## 1. Asymptotic Notations kya hoti hain?

Asymptotic Notations ka use algorithm ki performance ko analyze karne ke liye hota hai.

Ye batati hain ki input size (n) bahut bada hone par algorithm ki Time Complexity kaise grow karti hai.

Mainly 3 types hoti hain:

1. Big O Notation – O(n)
2. Omega Notation – Ω(n)
3. Theta Notation – Θ(n)

## 2. Big O Notation – O()

Big O Notation algorithm ki growth ka Upper Bound batati hai.

Simple words mein: Algorithm maximum kis growth rate se operations badha sakta hai, uska upper bound represent karti hai.

Example:

```cpp
for (int i = 0; i < n; i++) {
    cout << i << endl;
}
```

Agar n = 5 hai, toh loop 5 baar chalega.

Time Complexity = O(n)

**Important:** Big O ko commonly Worst Case Analysis ke liye use kiya jata hai, lekin mathematically Big O sirf upper bound batata hai.

## 3. Omega Notation – Ω()

Omega Notation algorithm ki growth ka Lower Bound batati hai.

Simple words mein: Algorithm ko kam se kam kitne operations karne padenge, uski lower growth boundary batati hai.

Example:

```cpp
int arr[] = {10, 20, 30, 40, 50};

for (int i = 0; i < 5; i++) {
    cout << arr[i] << endl;
}
```

Is loop mein 5 elements hain aur har baar loop execute hoga.

Time Complexity = Ω(n)

**Important:** Omega ko commonly Best Case Analysis se relate kiya jata hai, lekin Omega mathematically lower bound represent karta hai.

## 4. Theta Notation – Θ()

Theta Notation algorithm ki growth ka Tight Bound batati hai.

Simple words mein: Jab algorithm ki upper aur lower growth same order ki ho, tab Theta use hota hai.

Example:

```cpp
for (int i = 0; i < n; i++) {
    cout << i << endl;
}
```

Loop exactly n baar execute hota hai.

Time Complexity = Θ(n)

## 5. Big O, Omega aur Theta mein Difference

| Notation  | Meaning     | Bound                 |
| --------- | ----------- | --------------------- |
| Big O     | Upper Bound | Maximum growth limit  |
| Omega (Ω) | Lower Bound | Minimum growth limit  |
| Theta (Θ) | Tight Bound | Exact order of growth |

## 6. Ek Example se Samjho

Maan lo:

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}
```

Is loop mein n operations honge.

- Big O = O(n)
- Omega = Ω(n)
- Theta = Θ(n)

Kyunki iska growth order upper aur lower dono taraf n hai.

## 7. Searching Example

Array mein kisi element ko Linear Search se find karna:

```cpp
int arr[] = {10, 20, 30, 40, 50};
int target = 10;

for (int i = 0; i < 5; i++) {
    if (arr[i] == target) {
        cout << "Found";
        break;
    }
}
```

Ismein:

- Best Case = Ω(1)
- Worst Case = O(n)
- Average Case = Θ(n)

Note: Yahan best, worst aur average case input ke arrangement aur target ki position par depend karte hain.

## 8. Growth Comparison

| Complexity | Growth       |
| ---------- | ------------ |
| O(1)       | Constant     |
| O(log n)   | Logarithmic  |
| O(n)       | Linear       |
| O(n log n) | Linearithmic |
| O(n²)      | Quadratic    |
| O(2ⁿ)      | Exponential  |

Generally, same input size par lower growth rate wala algorithm zyada scalable hota hai.

## 9. Important Points

1. Big O = Upper Bound.
2. Omega = Lower Bound.
3. Theta = Tight Bound.
4. Big O, Omega aur Theta mathematically different concepts hain.
5. Best Case, Worst Case aur Average Case input ke according decide hote hain.
6. Asymptotic analysis large input size ke liye useful hai.

## 10. Common Mistakes

- Big O ko hamesha exact running time samajhna.
- Omega ko directly Best Case ka synonym samajhna.
- Theta ko sirf average case samajhna.
- Upper Bound aur Worst Case ko mathematically same samajhna.

## 11. Practice Questions

1. Big O Notation kya batati hai?
2. Omega Notation ka kya meaning hai?
3. Theta Notation kya represent karti hai?
4. Upper Bound kis notation se show hota hai?
5. Tight Bound kis notation se show hota hai?
6. Linear Search ka Worst Case kya hota hai?
7. O(n), Ω(n) aur Θ(n) mein difference batao.

## Quick Revision

- Big O = Upper Bound.
- Omega = Lower Bound.
- Theta = Tight Bound.
- O(n) = Maximum growth boundary.
- Ω(n) = Minimum growth boundary.
- Θ(n) = Tight growth boundary.

## Topic Status

**Topic 03 – Completed**

**Next Topic 04:** How to Calculate Time Complexity (Loops, Nested Loops and Conditions).
