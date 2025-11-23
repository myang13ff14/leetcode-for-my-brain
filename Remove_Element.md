# 27. Remove Element

## Problem Summary

Given an array `nums` and a value `val`, remove every occurrence of `val` **in-place** and return the new length.

That’s it.  
This entire question is basically:  
**“Manually implement filtering because interview traditions say so.”**

---

## My Solution

```python
class Solution:
    def removeElement(self, nums, val):
        pos = 0
        for x in nums:
            if x != val:
                nums[pos] = x
                pos += 1
        return pos
```

## How This Actually Works

pos points to where the next kept value should go and this is where the trick is.

Loop through the array:

If x == val: ignore it.

If x != val: copy it to the front.

Return how many values survived → that’s the new length.

## Comments
In reality, we probably just gonna write 
```python
nums = [x for x in nums if x != val]
```

This problem is pure pattern memorization. If you know it, it’s trivial; if you don’t, you’ll look slow and a clueless interviewer might take that as a sign you’re “not good enough,” which says more about them than about you.