# 26. Remove Duplicates from Sorted Array

## Problem Summary

You’re given a **sorted** array `nums`.  
Remove the duplicates **in-place**, making sure the first part of the array contains only the unique values, in order.  
Return how many unique values exist.

Anything after that returned length is irrelevant.  
This is basically:  
**"Manually dedupe a sorted list because we can’t use `set()` in interview land."**

---

## My Solution

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        j = 0
        for i in range(1, len(nums)):
            if nums[j] != nums[i]:
                j += 1
                nums[j] = nums[i]
        return j + 1
```

## How This Actually Works

Since the array is sorted, duplicates are automatically grouped together.
That’s the key.

We maintain two pointers:

j → the position of the last unique value

i → scans the array

Whenever we see a truly new number (nums[i] != nums[j]):

move j forward

overwrite nums[j] with this new value

When the scan ends, j + 1 is the count of unique values.
Everything after j is garbage that LeetCode ignores.

That’s literally the whole trick.

## Comments

If we were writing real Python code, we’d probably just do:

nums = sorted(set(nums))


But LeetCode needs you to do this manually because… tradition.

This problem is another pattern-recognition exercise.
If you know the “sorted array + two pointers” trick, this feels trivial.
If you don’t, you’ll be slower and again, a not-so-bright interviewer may think this somehow reflects your real engineering ability.
(It doesn’t.)