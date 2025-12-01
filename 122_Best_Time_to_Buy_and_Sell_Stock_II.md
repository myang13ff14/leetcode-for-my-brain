# 122. Best Time to Buy and Sell Stock II

## Problem Summary

You're given an array `prices` where `prices[i]` is the price of a stock on day `i`.  
You can complete **as many transactions as you want** — but you must sell before buying again.

Return the maximum profit you can achieve.

This version basically says:  
**"Whenever the price goes up from one day to the next, take that profit."**

No tricks, no DP tables, no fancy math. Just stack the gains.

---

## My Solution

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        for i in range(1, len(prices)):
            profit += max(prices[i] - prices[i - 1], 0)
        return profit

```

## How This Actually Works

In this version of the problem, because unlimited transactions are allowed:

Every time the price goes up,

you could have bought the previous day and sold today.

So the total max profit is simply:

sum of all positive (prices[i] - prices[i-1])


This works because making many small “buy low → sell high” transactions
is mathematically equivalent to finding all upward slopes.

Example:

prices = [1, 5, 3, 6]
profits = (5-1) + (6-3) = 4 + 3 = 7


No need for tracking buy/sell points individually — the greedy approach captures all gains.

## Comments

This problem looks like it wants some DP or complicated interval manipulation,
but the optimal solution is literally:

“If price today > price yesterday, take the difference.”

That’s it.