# ALGORITHMS AND COMPLEXITY

## Complete CS Fundamentals & Interview Preparation Notes

**Folder:** `CS Fundamentals/Algorithms and Complexity/`  
**File Name:** `Algorithms_and_Complexity_Complete_Notes.md`

---

# 1. Introduction to Algorithms

### Algorithm kya hota hai?

Algorithm kisi problem ko solve karne ke liye step-by-step instructions ka finite sequence hota hai.

**Example: Two numbers ka sum**

1. Start
2. Do numbers input lo.
3. Dono numbers add karo.
4. Result display karo.
5. Stop.

```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 20;
    int sum = a + b;

    cout << sum;
    return 0;
}
```

**Output:**

```text
30
```

### Real-life examples

- Google Maps: Shortest route find karna.
- Google Search: Relevant results find karna.
- YouTube: Video recommendations.
- Banking: Transaction processing.
- Instagram: Feed ranking.

### Algorithm vs Program

| Algorithm                               | Program                                 |
| --------------------------------------- | --------------------------------------- |
| Step-by-step solution                   | Code implementation                     |
| Language independent                    | Programming language dependent          |
| Logic represent karta hai               | Logic execute karta hai                 |
| Pseudocode/flowchart se likh sakte hain | C++, Java, Python etc. mein likhte hain |

---

# 2. Characteristics of an Algorithm

Ek good algorithm mein generally ye properties honi chahiye:

1. **Input:** Zero ya more inputs ho sakte hain.
2. **Output:** At least one result produce kare.
3. **Definiteness:** Har step clear aur unambiguous ho.
4. **Finiteness:** Limited steps ke baad terminate ho.
5. **Effectiveness:** Har step practically perform kiya ja sake.
6. **Correctness:** Given problem ke liye correct result de.
7. **Efficiency:** Time aur memory ka reasonable use kare.

**Interview Question:** Algorithm ki five main characteristics kya hain?

Answer: Input, Output, Definiteness, Finiteness aur Effectiveness.

---

# 3. Algorithm Representation

Algorithm ko different ways mein represent kar sakte hain.

### 1. Natural Language

Simple English/Hinglish mein steps likhna.

### 2. Pseudocode

Programming language jaisi simple language mein logic likhna, bina strict syntax ke.

Example:

```text
START
INPUT a, b
sum = a + b
PRINT sum
STOP
```

### 3. Flowchart

Algorithm ko symbols aur arrows ke through represent karna.

Common symbols:

| Symbol        | Meaning        |
| ------------- | -------------- |
| Oval          | Start / End    |
| Rectangle     | Process        |
| Parallelogram | Input / Output |
| Diamond       | Decision       |
| Arrow         | Flow direction |

### 4. Programming Language

Algorithm ko C++, Java, Python etc. mein implement karna.

---

# 4. What is Algorithm Analysis?

Algorithm Analysis ka matlab hai kisi algorithm ki performance evaluate karna.

Hum mainly do things analyze karte hain:

1. **Time Complexity:** Algorithm ko execute hone mein kitna time lagega, input size ke comparison mein.
2. **Space Complexity:** Algorithm ko kitni memory chahiye, input size ke comparison mein.

Example:

```cpp
for (int i = 0; i < n; i++) {
    cout << i << " ";
}
```

Agar `n = 5`, loop 5 times chalega.

Agar `n = 100`, loop 100 times chalega.

Isliye Time Complexity = **O(n)**.

Important: Big O actual seconds nahi batata. Ye input size badhne par growth rate describe karta hai.

---

# 5. Time Complexity

### Definition

Time Complexity batati hai ki input size `n` badhne par algorithm ke operations kis rate se increase hote hain.

### Common Time Complexities

| Complexity | Name         | Example                  |
| ---------- | ------------ | ------------------------ |
| O(1)       | Constant     | Array index access       |
| O(log n)   | Logarithmic  | Binary Search            |
| O(n)       | Linear       | Single loop              |
| O(n log n) | Linearithmic | Merge Sort               |
| O(n²)      | Quadratic    | Nested loops             |
| O(n³)      | Cubic        | Three nested loops       |
| O(2ⁿ)      | Exponential  | Some recursive solutions |
| O(n!)      | Factorial    | Brute-force permutations |

### Growth order

Generally, input size increase hone par:

`O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!)`

### Example 1: O(1)

```cpp
int arr[] = {10, 20, 30, 40};

cout << arr[2];
```

Array ka size kuch bhi ho, ek index access karne mein constant time lagta hai.

### Example 2: O(n)

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}
```

Loop `n` times chalega.

### Example 3: O(n²)

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << i << " " << j;
    }
}
```

Total operations approximately `n × n = n²`.

### Example 4: O(log n)

```cpp
while (n > 1) {
    n = n / 2;
}
```

Har iteration mein input half ho raha hai.

Time Complexity = O(log n).

---

# 6. Rules to Calculate Time Complexity

### Rule 1: Ignore constants

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}

for (int j = 0; j < n; j++) {
    cout << j;
}
```

Total operations: `n + n = 2n`

Complexity = **O(n)**

Constant 2 ignore karte hain.

### Rule 2: Ignore lower-order terms

Agar complexity hai:

`O(n² + n + 5)`

To dominant term `n²` hai.

Final Complexity = **O(n²)**

### Rule 3: Consecutive loops add hote hain

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}

for (int j = 0; j < n * n; j++) {
    cout << j;
}
```

Complexity:

`O(n + n²) = O(n²)`

### Rule 4: Nested loops multiply hote hain

```cpp
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        cout << i;
    }
}
```

Complexity = **O(n²)**

### Rule 5: Different variables

```cpp
for (int i = 0; i < n; i++) {
    cout << i;
}

for (int j = 0; j < m; j++) {
    cout << j;
}
```

Complexity = **O(n + m)**

Nested version mein complexity = **O(n × m)**.

---

# 7. Best, Average and Worst Case

Algorithm ki performance input ke according change ho sakti hai.

### 1. Best Case

Jab algorithm minimum operations perform kare.

### 2. Average Case

Typical inputs par expected performance.

### 3. Worst Case

Jab algorithm maximum operations perform kare.

**Example: Linear Search**

Array: `[10, 20, 30, 40, 50]`

| Case    | Search element | Complexity |
| ------- | -------------- | ---------- |
| Best    | 10             | O(1)       |
| Average | 30             | O(n)       |
| Worst   | 50 / Not found | O(n)       |

**Interview Question:** Worst-case analysis important kyu hai?

Answer: Ye algorithm ki maximum required work ka estimate deta hai aur performance guarantee samajhne mein help karta hai.

---

# 8. Asymptotic Notations

Asymptotic Notations large input size ke liye algorithm ki growth rate describe karti hain.

### 1. Big O — O()

Upper bound represent karta hai. Commonly worst-case growth describe karne ke liye use hota hai.

Example: Linear Search worst case = O(n).

### 2. Big Omega — Ω()

Lower bound represent karta hai.

Example: Linear Search best case = Ω(1).

### 3. Big Theta — Θ()

Tight bound represent karta hai, jab upper aur lower bounds same growth order ke hon.

Example: `3n + 5` = Θ(n).

| Notation | Meaning     |
| -------- | ----------- |
| O        | Upper Bound |
| Ω        | Lower Bound |
| Θ        | Tight Bound |

**Important:** Big O ko sirf worst case ka naam samajhna technically incomplete hai. Ye upper-bound notation hai; worst-case analysis mein commonly use hoti hai.

---

# 9. Space Complexity

### Definition

Space Complexity batati hai ki algorithm ko input size ke according kitni memory chahiye.

Ismein auxiliary space aur problem-specific memory usage important hote hain.

### 1. O(1) Space

```cpp
int sum = 0;

for (int i = 0; i < n; i++) {
    sum += i;
}
```

Fixed number of variables use ho rahe hain.

Auxiliary Space = O(1).

### 2. O(n) Space

```cpp
int* arr = new int[n];
```

`n` size ka additional array allocate ho raha hai.

Auxiliary Space = O(n).

### 3. Recursive Space

```cpp
void fun(int n) {
    if (n == 0) return;

    fun(n - 1);
}
```

Recursive call stack mein `n` calls tak ja sakti hain.

Space Complexity = O(n).

### Time vs Space Complexity

| Time Complexity                     | Space Complexity                      |
| ----------------------------------- | ------------------------------------- |
| Execution work measure karti hai    | Memory usage measure karti hai        |
| Operations/growth analyze karti hai | Extra storage/stack analyze karti hai |
| Example O(n)                        | Example O(1)                          |

**Space-Time Tradeoff:** Kabhi-kabhi extra memory use karke algorithm ka time reduce kar sakte hain. Example: Hashing.

---

# 10. Recursion and Recurrence Relation

### Recursion

Jab function apne aap ko call karta hai, use recursion kehte hain.

Example: Factorial

```cpp
int factorial(int n) {
    if (n == 0 || n == 1)
        return 1;

    return n * factorial(n - 1);
}
```

**Output:**

`factorial(5) = 120`

### Important Terms

- Base Case: Recursion stop karne ki condition.
- Recursive Case: Function ka khud ko call karna.
- Call Stack: Function calls ko manage karne wali memory structure.

### Recurrence Relation

Recursive algorithm ki time complexity ko mathematical equation ke through represent karna recurrence relation kehlata hai.

Example: Factorial recursion

`T(n) = T(n-1) + O(1)`

Solution: O(n).

Binary Search:

`T(n) = T(n/2) + O(1)`

Solution: O(log n).

Merge Sort:

`T(n) = 2T(n/2) + O(n)`

Solution: O(n log n).

---

# 11. Master Theorem

Master Theorem divide-and-conquer recurrence relations solve karne ka shortcut hai.

General form:

`T(n) = aT(n/b) + f(n)`

Where:

- `a` = Subproblems ki number.
- `b` = Har subproblem ka size reduction factor.
- `f(n)` = Divide aur combine karne ka extra work.

Let:

`d = log_b(a)`

### Three Main Cases

**Case 1:**

Agar `f(n) = O(n^(d-ε))` for some ε > 0,

Then:

`T(n) = Θ(n^d)`

**Case 2:**

Agar `f(n) = Θ(n^d log^k n)`,

Then:

`T(n) = Θ(n^d log^(k+1) n)`

**Case 3:**

Agar `f(n) = Ω(n^(d+ε))` and regularity condition satisfy hoti hai,

Then:

`T(n) = Θ(f(n))`

### Examples

| Algorithm                      | Recurrence      | Complexity |
| ------------------------------ | --------------- | ---------- |
| Binary Search                  | T(n/2) + O(1)   | O(log n)   |
| Merge Sort                     | 2T(n/2) + O(n)  | O(n log n) |
| Standard Matrix Multiplication | 8T(n/2) + O(n²) | O(n³)      |

**Note:** Master Theorem har recurrence par apply nahi hota. Unequal subproblem sizes ya non-standard recurrences ke liye other methods use karne pad sakte hain.

---

# 12. Algorithm Design Techniques

Algorithm Design Techniques ka matlab hai problems solve karne ke different approaches.

Main techniques:

1. Brute Force
2. Divide and Conquer
3. Greedy
4. Dynamic Programming
5. Backtracking
6. Branch and Bound
7. Randomized Algorithms

---

# 13. Brute Force Algorithm

### Definition

Brute Force mein problem ke possible solutions ko directly check karte hain, jab tak correct solution na mil jaye.

Example: Array mein element find karna using Linear Search.

```cpp
int linearSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == key)
            return i;
    }

    return -1;
}
```

Time Complexity = O(n).

### Advantages

- Easy to understand.
- Easy to implement.
- Small inputs ke liye useful.

### Disadvantages

- Large inputs par slow ho sakta hai.
- Efficient approach available ho to unnecessary operations karta hai.

**Examples:** Linear Search, basic password-combination checking, brute-force substring matching.

---

# 14. Divide and Conquer

### Definition

Divide and Conquer mein problem ko smaller subproblems mein divide karte hain, unhe solve karte hain aur results combine karte hain.

### Three Steps

1. Divide: Problem ko smaller parts mein divide karo.
2. Conquer: Subproblems solve karo.
3. Combine: Results combine karo.

### Examples

- Merge Sort
- Quick Sort
- Binary Search
- Strassen's Matrix Multiplication

### Merge Sort Example

Array: `[5, 2, 8, 1]`

1. Divide: `[5,2]` and `[8,1]`
2. Further divide: `[5] [2] [8] [1]`
3. Sort and merge: `[2,5]` and `[1,8]`
4. Final: `[1,2,5,8]`

Time Complexity = O(n log n).

### Advantages

- Large problems ko manageable banata hai.
- Efficient algorithms design karne mein useful.
- Parallel processing ke liye useful ho sakta hai.

### Disadvantages

- Extra memory lag sakti hai.
- Recursive calls ka overhead hota hai.

---

# 15. Greedy Algorithm

### Definition

Greedy Algorithm har step par locally best choice select karta hai, with the aim of reaching a globally optimal solution.

**Important:** Har problem mein greedy approach optimal answer nahi deti.

### Examples

- Activity Selection
- Fractional Knapsack
- Huffman Coding
- Dijkstra's Algorithm (non-negative edge weights)
- Kruskal's Algorithm
- Prim's Algorithm

### Fractional Knapsack

Items ka weight aur value diya hota hai. Bag ki capacity limited hoti hai. Item ka fraction bhi le sakte hain.

Greedy approach:

1. Har item ka value/weight ratio calculate karo.
2. Highest ratio wala item pehle lo.
3. Capacity bachne par next item lo.
4. Zaroorat pade to item ka fraction lo.

### Greedy vs Dynamic Programming

| Greedy                                 | Dynamic Programming                                |
| -------------------------------------- | -------------------------------------------------- |
| Local best choice leta hai             | Subproblems solve karta hai                        |
| Choice generally reconsider nahi karta | Stored results reuse karta hai                     |
| Often simpler                          | Often more memory use karta hai                    |
| Har problem mein optimal nahi          | Suitable conditions mein optimal solution deta hai |

---

# 16. Dynamic Programming (DP)

### Definition

Dynamic Programming ek technique hai jisme overlapping subproblems ke results store kiye jaate hain, taaki repeated calculations avoid ho sakein.

### DP ki Main Properties

1. **Overlapping Subproblems:** Same subproblems repeatedly appear hote hain.
2. **Optimal Substructure:** Problem ka optimal solution smaller subproblems ke optimal solutions se build ho sakta hai.

### Fibonacci Example

Basic Recursion:

```cpp
int fib(int n) {
    if (n <= 1)
        return n;

    return fib(n - 1) + fib(n - 2);
}
```

Time Complexity approximately O(2ⁿ).

DP using Memoization:

```cpp
int fib(int n, vector<int>& dp) {
    if (n <= 1)
        return n;

    if (dp[n] != -1)
        return dp[n];

    return dp[n] =
        fib(n - 1, dp) + fib(n - 2, dp);
}
```

Call:

```cpp
vector<int> dp(n + 1, -1);
cout << fib(n, dp);
```

Time Complexity = O(n).

Space Complexity = O(n), including DP storage and recursion stack.

### Two Approaches

**1. Memoization (Top-Down)**

- Recursion use hoti hai.
- Results store kiye jaate hain.
- Required subproblems solve hote hain.

**2. Tabulation (Bottom-Up)**

- Iteration use hoti hai.
- Small problems se start karte hain.
- Table fill karke final answer find karte hain.

Tabulation Example:

```cpp
int fib(int n) {
    if (n <= 1) return n;

    vector<int> dp(n + 1);

    dp[0] = 0;
    dp[1] = 1;

    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }

    return dp[n];
}
```

Time Complexity = O(n).

Space Complexity = O(n).

### Common DP Problems

- Fibonacci
- 0/1 Knapsack
- Coin Change
- Longest Common Subsequence (LCS)
- Longest Increasing Subsequence (LIS)
- Matrix Chain Multiplication
- Edit Distance
- Grid/Path Problems

---

# 17. Backtracking

### Definition

Backtracking mein possible solutions explore karte hain. Agar koi choice solution tak nahi pahunch sakti, to us choice ko undo karke another choice try karte hain.

Simple concept:

**Choose → Explore → Unchoose**

### Examples

- N-Queens
- Sudoku Solver
- Rat in a Maze
- Permutations
- Subsets
- Word Search

### N-Queens Problem

N × N chessboard par N queens place karni hoti hain.

Condition:

- Same row mein nahi.
- Same column mein nahi.
- Same diagonal mein nahi.

Backtracking approach:

1. Ek row select karo.
2. Safe column find karo.
3. Queen place karo.
4. Next row solve karo.
5. Agar solution possible nahi, queen remove karo.
6. Next position try karo.

Worst-case search bahut expensive ho sakti hai; basic N-Queens search ko commonly exponential/factorial-scale problem maana jata hai.

### Backtracking vs Brute Force

| Backtracking                      | Brute Force                                 |
| --------------------------------- | ------------------------------------------- |
| Invalid paths ko prune karta hai  | Possible choices ko broadly check karta hai |
| Search space reduce kar sakta hai | More unnecessary work ho sakta hai          |
| Constraint problems mein useful   | Simple exhaustive checking mein useful      |

---

# 18. Branch and Bound

### Definition

Branch and Bound optimization problems solve karne ki technique hai. Ismein problem ko branches mein divide karte hain aur bounds use karke un branches ko eliminate karte hain jo optimal answer nahi de sakti.

### Main Concepts

- Branch: Problem ko smaller subproblems mein divide karna.
- Bound: Possible best/worst result ka estimate.
- Pruning: Unpromising branches remove karna.

### Examples

- Travelling Salesman Problem
- 0/1 Knapsack
- Assignment Problem

### Backtracking vs Branch and Bound

| Backtracking                       | Branch and Bound                                 |
| ---------------------------------- | ------------------------------------------------ |
| Feasible solution find karna       | Optimal solution find karna                      |
| Constraints violate hone par prune | Bound ke basis par prune                         |
| DFS commonly used                  | BFS, priority queue or other strategies possible |

---

# 19. Searching Algorithms

Searching ka matlab data collection mein required element find karna.

### 1. Linear Search

Elements ko one-by-one check karte hain.

Time Complexity:

- Best: O(1)
- Average: O(n)
- Worst: O(n)

Works on sorted and unsorted data.

### 2. Binary Search

Sorted data ko repeatedly half divide karke search karte hain.

```cpp
int binarySearch(int arr[], int n, int key) {
    int low = 0;
    int high = n - 1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] == key)
            return mid;

        if (arr[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }

    return -1;
}
```

Time Complexity = O(log n).

**Important:** Standard binary search ke liye sorted data aur efficient random access chahiye.

### Linear vs Binary Search

| Linear Search             | Binary Search        |
| ------------------------- | -------------------- |
| O(n)                      | O(log n)             |
| Sorted data required nahi | Sorted data required |
| Sequential checking       | Half-half division   |
| Simple implementation     | Slightly more logic  |

---

# 20. Sorting Algorithms

Sorting ka matlab data ko ascending ya descending order mein arrange karna.

### 1. Bubble Sort

Adjacent elements compare aur swap karta hai.

Time Complexity:

- Best: O(n) with optimized early-stop implementation.
- Average: O(n²).
- Worst: O(n²).

Space: O(1).

### 2. Selection Sort

Har pass mein minimum element find karke correct position par place karta hai.

Time: O(n²) in all common cases.

Space: O(1).

### 3. Insertion Sort

Elements ko sorted portion mein correct position par insert karta hai.

Time:

- Best: O(n).
- Average: O(n²).
- Worst: O(n²).

Space: O(1).

### 4. Merge Sort

Divide and Conquer technique use karta hai.

Time: O(n log n).

Space: O(n) for typical array implementation.

### 5. Quick Sort

Pivot select karke array partition karta hai.

Time:

- Best/Average: O(n log n).
- Worst: O(n²).

Auxiliary Space: Recursion stack; average O(log n), worst O(n) in common implementations.

### 6. Heap Sort

Heap data structure use karke sorting karta hai.

Time: O(n log n).

Space: O(1) auxiliary space for in-place implementation.

### Sorting Comparison Table

| Algorithm      | Best       | Average    | Worst      |
| -------------- | ---------- | ---------- | ---------- |
| Bubble Sort*   | O(n)       | O(n²)      | O(n²)      |
| Selection Sort | O(n²)      | O(n²)      | O(n²)      |
| Insertion Sort | O(n)       | O(n²)      | O(n²)      |
| Merge Sort     | O(n log n) | O(n log n) | O(n log n) |
| Quick Sort     | O(n log n) | O(n log n) | O(n²)      |
| Heap Sort      | O(n log n) | O(n log n) | O(n log n) |

*Bubble Sort best case O(n) tab hai jab early-stop optimization implemented ho.

### Stable vs Unstable Sorting

**Stable Sorting:** Equal-key elements ka original relative order preserve rehta hai.

Common stable algorithms:

- Bubble Sort
- Insertion Sort
- Merge Sort (standard stable merge implementation)

Common unstable algorithms:

- Selection Sort
- Quick Sort
- Heap Sort

### In-place Sorting

Jo algorithm very little extra auxiliary memory use karke sorting kare.

Examples: Selection Sort, Insertion Sort, Heap Sort.

**Note:** In-place ka exact meaning implementation par depend kar sakta hai.

---

# 21. Graph Algorithms

Graph algorithms nodes (vertices) aur connections (edges) par operations perform karte hain.

### 1. BFS — Breadth First Search

Graph ko level-by-level traverse karta hai.

- Queue use karta hai.
- Unweighted graph mein shortest path (minimum number of edges) find kar sakta hai.

Time Complexity with adjacency list = O(V + E).

### 2. DFS — Depth First Search

Ek path par deep jaata hai, phir backtrack karta hai.

- Recursion ya Stack use karta hai.
- Connected components aur cycle detection mein useful.

Time Complexity with adjacency list = O(V + E).

### 3. Dijkstra's Algorithm

Non-negative edge weights wale graph mein single-source shortest paths find karta hai.

Priority queue aur adjacency list ke saath common implementation:

O((V + E) log V)

### 4. Bellman-Ford Algorithm

Single-source shortest paths find karta hai aur reachable negative-weight cycles detect kar sakta hai.

Time Complexity = O(V × E).

### 5. Floyd-Warshall Algorithm

All-pairs shortest paths find karta hai.

Time Complexity = O(V³).

Space Complexity = O(V²).

### 6. Minimum Spanning Tree (MST)

Connected, weighted, undirected graph ke sabhi vertices connect karne ke liye minimum total edge weight ka spanning tree.

**Kruskal's Algorithm**

- Edges ko weight ke according sort karta hai.
- DSU use karke cycle avoid karta hai.
- Common complexity: O(E log E).

**Prim's Algorithm**

- Ek starting vertex se MST grow karta hai.
- Priority queue use kar sakta hai.
- Adjacency list + binary heap: O((V + E) log V).

### 7. Topological Sorting

Directed Acyclic Graph (DAG) ka linear ordering find karta hai, jahan har directed edge `u → v` mein `u`, `v` se pehle aaye.

Methods:

- DFS-based.
- Kahn's Algorithm (BFS + indegree).

Time Complexity = O(V + E).

---

# 22. String Matching Algorithms

String Matching ka matlab ek text ke andar particular pattern find karna.

### 1. Naive String Matching

Har possible position par pattern compare karte hain.

Worst-case Time = O(n × m).

Where:

- n = Text length.
- m = Pattern length.

### 2. KMP Algorithm

Knuth-Morris-Pratt algorithm LPS (Longest Proper Prefix which is also Suffix) array use karta hai.

Time Complexity = O(n + m).

### 3. Rabin-Karp Algorithm

Hashing use karke pattern search karta hai.

Expected/average performance often O(n + m), but collisions ki wajah se worst case O(n × m) ho sakta hai.

### 4. Z Algorithm

Z-array use karke string matching aur prefix-related problems solve karta hai.

Time Complexity = O(n + m) for common pattern-search construction.

---

# 23. Randomized Algorithms

### Definition

Randomized Algorithms apne execution mein random choices use karte hain.

### Types

**1. Las Vegas Algorithm**

- Answer always correct.
- Running time random ho sakta hai.

Example: Randomized Quick Sort.

**2. Monte Carlo Algorithm**

- Running time bounded/fixed ho sakta hai.
- Small probability of incorrect answer ho sakti hai.

### Example

Randomized Quick Sort mein pivot randomly select kiya jata hai.

Expected Time Complexity = O(n log n).

Worst Case = O(n²).

---

# 24. Algorithm Correctness

Algorithm Correctness ka matlab algorithm har valid input ke liye expected result produce kare.

### Correctness Prove Karne ke Methods

1. Mathematical Induction.
2. Loop Invariant.
3. Proof by Contradiction.
4. Direct Proof.

### Loop Invariant

Loop ke har iteration se pehle ya baad ek property true rehti hai, jise loop invariant kehte hain.

Three steps:

- Initialization: Starting mein property true hai.
- Maintenance: Har iteration ke baad property true rehti hai.
- Termination: Loop end hone par property se final result prove hota hai.

**Interview Point:** Testing bugs find karne mein help karti hai, lekin mathematical correctness proof har valid input ke liye guarantee establish kar sakta hai.

---

# 25. Amortized Analysis

### Definition

Amortized Analysis multiple operations ki sequence ka average cost analyze karta hai, even if some individual operations expensive hon.

Ye probability-based average nahi hai.

### Example: Dynamic Array

Dynamic array mein capacity full hone par larger array allocate karke elements copy karne pad sakte hain.

- Most insertions: O(1) amortized-style append.
- Resizing insertion: O(n).
- n append operations: O(n) total under geometric growth.
- Per append amortized cost: O(1).

### Three Methods

1. Aggregate Method.
2. Accounting Method.
3. Potential Method.

**Interview Question:** Amortized O(1) ka matlab har operation O(1) hai?

Answer: Nahi. Kuch individual operations O(n) ho sakte hain, lekin long sequence ka average cost per operation O(1) hota hai.

---

# 26. P vs NP — Basic Introduction

Ye theoretical Computer Science ka important topic hai.

### P Class

Problems jo deterministic algorithm se polynomial time mein solve ho sakti hain.

Examples:

- Sorting.
- Shortest path.
- Minimum spanning tree.

### NP Class

Problems jinke proposed solutions ko polynomial time mein verify kiya ja sakta hai.

### NP-Hard

Aise problems jinki difficulty at least NP ke hardest problems jitni hoti hai. NP-Hard problem ka NP mein hona necessary nahi.

### NP-Complete

Problems jo:

1. NP mein hoti hain.
2. NP-Hard bhi hoti hain.

Examples:

- SAT.
- 3-SAT.
- Hamiltonian Cycle (decision version).
- Travelling Salesman Problem (decision version).

### P vs NP Question

Kya har problem jiska solution quickly verify ho sakta hai, uska solution bhi quickly find kiya ja sakta hai?

Abhi tak iska answer unknown hai.

**Important:** P vs NP ek unsolved major theoretical problem hai.

---

# 27. Algorithm Efficiency and Optimization

Algorithm optimization ka goal performance improve karna hai.

### Common Techniques

1. Better algorithm select karna.
2. Unnecessary loops remove karna.
3. Repeated calculations avoid karna.
4. Hashing use karna.
5. Memoization use karna.
6. Suitable data structure choose karna.
7. Space-time tradeoff samajhna.
8. Efficient input/output use karna.

### Example: Repeated Search

Agar array mein repeatedly search karna hai:

- Har baar Linear Search: O(n) per search.
- Hash Set: Average O(1) lookup, with O(n) expected preprocessing.

Multiple queries ke liye hashing useful ho sakti hai.

---

# 28. Important Algorithm Complexity Cheat Sheet

| Algorithm             | Time Complexity                                |
| --------------------- | ---------------------------------------------- |
| Linear Search         | O(n) worst                                     |
| Binary Search         | O(log n)                                       |
| Bubble Sort           | O(n²) worst                                    |
| Selection Sort        | O(n²)                                          |
| Insertion Sort        | O(n²) worst                                    |
| Merge Sort            | O(n log n)                                     |
| Quick Sort            | O(n log n) average                             |
| Heap Sort             | O(n log n)                                     |
| BFS                   | O(V + E)                                       |
| DFS                   | O(V + E)                                       |
| Dijkstra              | O((V+E) log V) with common heap implementation |
| Bellman-Ford          | O(VE)                                          |
| Floyd-Warshall        | O(V³)                                          |
| Kruskal               | O(E log E)                                     |
| KMP                   | O(n + m)                                       |
| Naive String Matching | O(nm) worst                                    |

---

# 29. Frequently Asked Interview Questions

### Q1. Algorithm kya hota hai?

Problem solve karne ke liye finite step-by-step instructions.

### Q2. Algorithm aur program mein difference?

Algorithm solution ka logic hai; program us logic ka executable implementation hai.

### Q3. Time Complexity kya hai?

Input size ke according algorithm ke operations ki growth rate.

### Q4. Space Complexity kya hai?

Algorithm ki memory requirement ka growth rate.

### Q5. Big O kya represent karta hai?

Asymptotic upper bound.

### Q6. Big Omega kya represent karta hai?

Asymptotic lower bound.

### Q7. Big Theta kya represent karta hai?

Asymptotically tight bound.

### Q8. O(1) ka example?

Array index access.

### Q9. O(log n) ka example?

Binary Search.

### Q10. O(n²) ka example?

Two nested loops over n elements.

### Q11. Best, Average aur Worst Case kya hain?

Minimum, typical expected aur maximum work ke scenarios.

### Q12. Recursion kya hai?

Function ka khud ko call karna.

### Q13. Base Case kya hai?

Recursion terminate karne ki condition.

### Q14. Recurrence Relation kya hai?

Recursive algorithm ki complexity ko equation mein represent karna.

### Q15. Master Theorem kya hai?

Divide-and-conquer recurrence solve karne ki method.

### Q16. Divide and Conquer kya hai?

Problem ko divide, subproblems solve aur results combine karna.

### Q17. Greedy Algorithm kya hai?

Har step par locally best choice select karna.

### Q18. Dynamic Programming kya hai?

Repeated subproblems ke results store karke repeated calculations avoid karna.

### Q19. Memoization kya hai?

Top-down DP approach jisme recursive results cache hote hain.

### Q20. Tabulation kya hai?

Bottom-up DP approach jisme iterative table fill hoti hai.

### Q21. Backtracking kya hai?

Choice explore karna aur invalid path par choice undo karna.

### Q22. Branch and Bound kya hai?

Bounds use karke unpromising optimization branches prune karna.

### Q23. Stable Sorting kya hai?

Equal elements ka original relative order preserve karna.

### Q24. In-place Sorting kya hai?

Very little additional auxiliary memory use karke sorting karna.

### Q25. Merge Sort aur Quick Sort mein difference?

Merge Sort guaranteed O(n log n) time leta hai but array implementation mein extra memory use karta hai. Quick Sort average O(n log n) hai, in-place partitioning kar sakta hai, but worst case O(n²) ho sakta hai.

### Q26. BFS aur DFS mein difference?

BFS level-wise Queue use karta hai; DFS depth-wise Stack/Recursion use karta hai.

### Q27. Dijkstra negative edge weights handle kar sakta hai?

Standard Dijkstra algorithm negative edge weights ke liye reliable nahi hai.

### Q28. Bellman-Ford ka advantage?

Negative edge weights handle karta hai aur reachable negative-weight cycles detect kar sakta hai.

### Q29. Amortized Analysis kya hai?

Operations ki sequence ka average cost analyze karna.

### Q30. P vs NP kya hai?

P aur NP complexity classes ke beech relationship ka fundamental theoretical question.

---

# 30. Tricky Interview Questions

### Q1. Kya O(n) hamesha O(log n) se slow hota hai?

Nahi. Small input size ya constants ke karan actual running time different ho sakta hai. Asymptotic growth large input ke liye compare hoti hai.

### Q2. Kya nested loops hamesha O(n²) hote hain?

Nahi. Inner loop ki iterations depend karti hain. Example: Inner loop repeatedly half hota hai to O(n log n) possible hai.

### Q3. Kya recursion hamesha O(n) space leti hai?

Nahi. Recursion depth par depend karta hai. Binary Search recursion depth O(log n) hoti hai.

### Q4. Kya Binary Search linked list par efficient hai?

Generally nahi. Middle element access karne ke liye traversal chahiye, isliye standard O(log n) search-time benefit nahi milta.

### Q5. Kya Merge Sort stable hai?

Standard implementation mein haan, agar equal elements merge karte waqt original order preserve kiya jaye.

### Q6. Kya Quick Sort stable hai?

Standard in-place implementation usually stable nahi hoti.

### Q7. Kya Greedy aur DP same hain?

Nahi. Greedy local choice leta hai; DP multiple subproblems ke results compare/store karta hai.

### Q8. Kya DP har recursive problem par apply hoti hai?

Nahi. Overlapping subproblems aur suitable optimal substructure hona important hai.

### Q9. Kya O(1) ka matlab exactly one operation hai?

Nahi. Constant number of operations ya constant growth represent karta hai.

### Q10. Kya amortized O(1) ka matlab worst case O(1) hai?

Nahi. Individual operation expensive ho sakta hai, lekin sequence ka amortized cost O(1) ho sakta hai.

---

# 31. Quick Revision

| Topic               | Remember                       |
| ------------------- | ------------------------------ |
| Algorithm           | Step-by-step solution          |
| Time Complexity     | Work growth                    |
| Space Complexity    | Memory growth                  |
| O(1)                | Constant                       |
| O(log n)            | Logarithmic                    |
| O(n)                | Linear                         |
| O(n log n)          | Linearithmic                   |
| O(n²)               | Quadratic                      |
| Big O               | Upper bound                    |
| Big Omega           | Lower bound                    |
| Big Theta           | Tight bound                    |
| Recursion           | Function calls itself          |
| Master Theorem      | Recurrence solving             |
| Brute Force         | Direct/exhaustive checking     |
| Divide and Conquer  | Divide, solve, combine         |
| Greedy              | Local best choice              |
| Dynamic Programming | Store/reuse subproblem results |
| Backtracking        | Choose, explore, undo          |
| Branch and Bound    | Bound-based pruning            |
| BFS                 | Queue                          |
| DFS                 | Stack/Recursion                |
| Dijkstra            | Non-negative shortest paths    |
| Bellman-Ford        | Negative edges supported       |
| Floyd-Warshall      | All-pairs shortest paths       |
| KMP                 | LPS-based string matching      |
| Amortized Analysis  | Sequence-based average cost    |
| P vs NP             | Complexity theory              |

---

# 32. Practice Questions

In questions ko khud solve karna. Sirf answer read mat karna.

### Basic Level

1. Algorithm aur program mein difference likho.
2. Time Complexity kya hoti hai?
3. Space Complexity kya hoti hai?
4. O(1), O(n), O(n²) ka example do.
5. Linear Search ki complexity calculate karo.
6. Binary Search ke liye kya condition hai?
7. Big O, Omega aur Theta explain karo.
8. Best, Average aur Worst Case explain karo.

### Intermediate Level

9. Nested loops ki complexity calculate karo.
10. Recurrence relation kya hoti hai?
11. Master Theorem explain karo.
12. Merge Sort ki complexity derive karo.
13. Greedy aur DP compare karo.
14. Memoization aur Tabulation compare karo.
15. Backtracking ka example explain karo.
16. Stable aur unstable sorting explain karo.

### Advanced / Interview Level

17. Dijkstra aur Bellman-Ford compare karo.
18. BFS aur DFS ki complexity explain karo.
19. KMP algorithm ka LPS array kya hai?
20. Amortized Analysis explain karo.
21. P, NP, NP-Hard aur NP-Complete compare karo.
22. Quick Sort worst case kab aata hai?
23. Recursive Binary Search ki space complexity kya hai?
24. 0/1 Knapsack mein Greedy approach generally optimal kyu nahi hoti?

---

# 33. Final Interview Preparation Checklist

- [ ] Algorithm definition and characteristics
- [ ] Algorithm representation and pseudocode
- [ ] Time and Space Complexity
- [ ] Big O, Omega, Theta
- [ ] Best, Average, Worst Case
- [ ] Complexity calculation rules
- [ ] Recursion and Recurrence Relations
- [ ] Master Theorem
- [ ] Brute Force
- [ ] Divide and Conquer
- [ ] Greedy Algorithms
- [ ] Dynamic Programming
- [ ] Backtracking
- [ ] Branch and Bound
- [ ] Searching and Sorting
- [ ] Graph Algorithms
- [ ] String Matching
- [ ] Randomized Algorithms
- [ ] Algorithm Correctness
- [ ] Amortized Analysis
- [ ] P vs NP

---

## Important: Is Subject ko Kaise Study Karna Hai?

1. Pehle concept samjho.
2. Har algorithm ka dry run notebook mein karo.
3. C++ mein implementation likho.
4. Time aur Space Complexity khud calculate karo.
5. Practice questions solve karo.
6. Interview questions ke answers bolkar practice karo.

**Subject distinction:**

- **Data Structures Fundamentals:** Data ko organize aur store karne ke concepts.
- **Algorithms and Complexity:** Problems solve karne ke methods aur unki efficiency.
- **DSA in C++:** In concepts ko C++ coding, implementation aur problem-solving mein apply karna.

**Note:** Ye CS Fundamentals ke theory aur interview preparation notes hain. DSA coding practice mein algorithms ki implementation aur problems separately karni hongi.

**End of Algorithms and Complexity Notes.**
