# 📈 Buy and Sell Stock II - Leetcode

## 🔗 Problem Link
[Best Time to Buy and Sell Stock II](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/564/)

---

## 🧠 Problem Summary

- You are given an array `prices[]` where `prices[i]` is the price of a given stock on day `i`.
- You may complete as many transactions as you like **(i.e., buy one and sell one share of the stock multiple times)**.
- You may not engage in multiple transactions at the same time (**must sell before you buy again**).

---

## ✅ Goal

**Maximize total profit** by choosing the best days to buy and sell stock.

---

## 🏔️ Key Concept: Buy at Valley, Sell at Peak

- Imagine the price graph as a mountain range:
  - **Valley**: Local minimum — buy here.
  - **Peak**: Local maximum — sell here.
- To maximize profit:
  - Scan left to right.
  - **Buy when price starts going up**.
  - **Sell when price is about to drop**.

> This models the real-life strategy of repeatedly buying low and selling high.

---

## ✅ Step-by-Step Plan Based on Your Explanation:
- Track whether you're holding a stock
  - Use a boolean flag like holdingStock or a variable like buyPrice (null or -1 if not holding).
- Iterate through prices one by one
  - Loop from index 0 to n - 1 (or n - 2 if you’re comparing with i + 1).
- Buy condition:
  - If you are not holding stock, and prices[i] < prices[i + 1] → that’s a valley → buy at prices[i].
- Sell condition:
  - If you are holding stock, and prices[i] > prices[i + 1] → that’s a peak → sell at prices[i].
- Edge case at the end:
  - If you're still holding stock at the end of the loop (because the last price is rising), sell on the last day.

---
## ✋ Key Ideas to Remember:
- Only buy when the next day is more expensive.
- Only sell when the next day is cheaper.
- Track whether you're currently holding stock to avoid double buys.
- Accumulate the total profit each time you sell.

---

## 🛠️ Track Buy/Sell State (Explicit)

Useful when constraints like cooldowns, fees, or limited transactions are added.

```java
public int maxProfit(int[] prices) {
    boolean holdingStock = false;
    int buy = 0, maxProfit = 0;

    for (int i = 0; i < prices.length - 1; i++) {
        if (!holdingStock && prices[i] < prices[i + 1]) {
            buy = prices[i];
            holdingStock = true;
        } else if (holdingStock && prices[i] > prices[i + 1]) {
            maxProfit += prices[i] - buy;
            holdingStock = false;
        }
    }

    // Edge case: sell on last day if still holding
    if (holdingStock) {
        maxProfit += prices[prices.length - 1] - buy;
    }

    return maxProfit;
}
```

### Complexity
- **Time:** O(n)
- **Space:** O(1)

---

## ✅ Summary

- Accumulate **all positive gains** between consecutive days.
- **Buy at every valley**, **sell at every peak**.
- Greedy works well because **no limit on number of transactions**.
