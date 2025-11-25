# 169. Majority Element

## Problem Summary

Given an array `nums`, find the element that appears more than `n/2` times.  
A majority element is guaranteed to exist.

This is one of those “there is only one possible answer so just find it” problems.

---

## My Solution (Counter Version)

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        counts = collections.Counter(nums)
        n = len(nums)
        for k, v in counts.items():
            if v > n // 2:
                return k
```

Simple: count everything, return the element whose count exceeds half the array.

In real Python code, this is 100% acceptable.