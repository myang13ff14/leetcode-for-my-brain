# 121. Best Time to Buy and Sell Stock

## Problem Summary

You're given a list `prices`, where `prices[i]` is the price of a stock on day `i`.  
You can make **one** transaction: buy once and sell once.  
Return the maximum profit you can achieve. If no profit is possible, return 0.

This is one of LeetCode’s most famous warm-up questions — simple idea, very interview-friendly, and 100% pattern-based.

---

## My Solution

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_price = float('inf')
        max_profit = 0

        for price in prices:
            min_price = min(min_price, price)
            max_profit = max(max_profit, price - min_price)

        return max_profit
```

## How This Actually Works

To maximize profit, we want:

sell_price - buy_price


Where:

buy_price must come before sell_price

We want the smallest buy price before the current day

And the largest difference afterward

So we track:

min_price → the lowest price seen so far

max_profit → the best profit so far

For each price:

Update the lowest price we've ever seen

Compute what profit we'd get if we sold today

Update our best profit

That’s literally it.
