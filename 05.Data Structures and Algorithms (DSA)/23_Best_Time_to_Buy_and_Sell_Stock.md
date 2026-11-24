# Topic 23: Best Time to Buy and Sell Stock

## 1. Problem Kya Hai?

Is problem mein humein stock ki prices ka array diya hota hai.

Har index ek din ko represent karta hai aur us din stock ki price batata hai.

Humein ek din stock buy karna hai aur uske baad kisi future day par sell karna hai.

Goal: Maximum profit find karna.

**Example:**

```cpp
prices[] = {7, 1, 5, 3, 6, 4};
```

Best choice:

- Buy price = 1
- Sell price = 6
- Profit = 6 - 1 = 5

**Output:**

```text
Maximum Profit = 5
```

## 2. Important Rules

1. Buy pehle karna hai.
2. Sell buy ke baad wale din hi karna hai.
3. Maximum profit find karna hai.
4. Agar profit possible nahi hai, toh answer `0` hoga.
5. Ek hi transaction karni hai (one buy and one sell).

## 3. Approach 1: Brute Force

Har possible buying day aur uske baad ke selling days check karenge.

### Algorithm

1. Ek outer loop buy day ke liye chalao.
2. Inner loop uske next day se start karo.
3. Profit calculate karo.
4. Maximum profit update karo.
5. Finally maximum profit return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int maxProfit(vector<int>& prices) {

    int n = prices.size();
    int maxProfit = 0;

    for (int i = 0; i < n; i++) {

        for (int j = i + 1; j < n; j++) {

            int profit = prices[j] - prices[i];

            maxProfit = max(maxProfit, profit);
        }
    }

    return maxProfit;
}

int main() {

    vector<int> prices = {7, 1, 5, 3, 6, 4};

    cout << "Maximum Profit: "
         << maxProfit(prices);

    return 0;
}
```

**Output:**

```text
Maximum Profit: 5
```

### Complexity

- Time Complexity: O(n²)
- Auxiliary Space: O(1)

## 4. Approach 2: One Pass (Optimized)

Ye optimal approach hai.

Hum array ko sirf ek baar traverse karenge.

### Main Logic

Humein do variables maintain karne hain:

1. `minPrice`: Ab tak ki minimum stock price.
2. `maxProfit`: Ab tak ka maximum profit.

Har day:

- Current price ko minimum price se compare karo.
- Profit calculate karo.
- Maximum profit update karo.
- Agar current price minimum hai toh `minPrice` update karo.

### Formula

```cpp
profit = currentPrice - minPrice;
```

### Algorithm

1. `minPrice = INT_MAX` initialize karo.
2. `maxProfit = 0` initialize karo.
3. Array ko traverse karo.
4. Current price agar minimum hai toh `minPrice` update karo.
5. Otherwise current profit calculate karo.
6. `maxProfit` update karo.
7. Finally maximum profit return karo.

### C++ Code

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits>
using namespace std;

int maxProfit(vector<int>& prices) {

    int minPrice = INT_MAX;
    int maxProfit = 0;

    for (int i = 0; i < prices.size(); i++) {

        if (prices[i] < minPrice) {
            minPrice = prices[i];
        }

        else {
            int profit = prices[i] - minPrice;

            maxProfit = max(maxProfit, profit);
        }
    }

    return maxProfit;
}

int main() {

    vector<int> prices = {7, 1, 5, 3, 6, 4};

    cout << "Maximum Profit: "
         << maxProfit(prices);

    return 0;
}
```

**Output:**

```text
Maximum Profit: 5
```

## 5. Dry Run

Array:

```cpp
prices[] = {7, 1, 5, 3, 6, 4};
```

Initial values:

```cpp
minPrice = INT_MAX;
maxProfit = 0;
```

| Day | Price | Minimum Price | Current Profit | Maximum Profit |
| --- | ----: | ------------: | -------------: | -------------: |
| 1   |     7 |             7 |              0 |              0 |
| 2   |     1 |             1 |              0 |              0 |
| 3   |     5 |             1 |              4 |              4 |
| 4   |     3 |             1 |              2 |              4 |
| 5   |     6 |             1 |              5 |              5 |
| 6   |     4 |             1 |              3 |              5 |

Final Answer:

```text
Maximum Profit = 5
```

Buy on Day 2 and Sell on Day 5.

## 6. Example: No Profit Possible

```cpp
prices[] = {7, 6, 4, 3, 1};
```

Yahan har next day price decrease ho rahi hai.

Isliye profit possible nahi hai.

**Output:**

```text
Maximum Profit = 0
```

## 7. Time and Space Complexity

| Approach    | Time Complexity | Auxiliary Space |
| ----------- | --------------- | --------------- |
| Brute Force | O(n²)           | O(1)            |
| One Pass    | O(n)            | O(1)            |

**Optimized Approach:** O(n) time aur O(1) auxiliary space.

## 8. Common Mistakes

1. Buy aur sell day ka order galat rakhna.
2. Current day par buy aur sell dono karne ki koshish karna.
3. `maxProfit = 0` initialize na karna.
4. Har iteration mein minimum price update karne ka logic galat likhna.
5. Negative profit ko answer mein include karna.
6. Multiple transactions wale stock problem ke saath confuse karna.

## 9. Practice Questions

1. `{7, 1, 5, 3, 6, 4}` ka maximum profit find karo.
2. `{7, 6, 4, 3, 1}` solve karo.
3. `{2, 4, 1}` ka maximum profit find karo.
4. `{3, 8, 2, 10, 1, 12}` solve karo.
5. Maximum profit ke saath buying aur selling day bhi print karo.

## 10. Quick Revision

- Stock ko pehle buy aur baad mein sell karna hai.
- Goal maximum profit find karna hai.
- Profit = Selling Price - Buying Price.
- `minPrice` minimum buying price track karta hai.
- `maxProfit` maximum profit track karta hai.
- Brute Force: O(n²).
- Optimized One Pass: O(n).
- Auxiliary Space: O(1).
- Profit possible nahi ho toh answer 0.

## 11. Topic Completion Checklist

- [ ] Stock problem samajh liya.
- [ ] Brute Force approach samajh li.
- [ ] One Pass approach samajh li.
- [ ] Dry Run kar liya.
- [ ] C++ code run kar liya.
- [ ] Practice questions solve kar liye.

---

**Next Topic 24: Maximum Subarray Sum (Kadane's Algorithm)**
