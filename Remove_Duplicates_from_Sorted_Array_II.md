# 80. Remove Duplicates from Sorted Array II

## Problem Summary

Given a **sorted** array `nums`, remove duplicates **in-place** so that each element appears **at most twice**.  
Return the new length.  
As always, anything beyond that length doesn’t matter.

This is basically Problem 26 but with one extra twist:  
**“You may keep each number twice, but not more.”**

Classic LeetCode problem where the logic isn’t hard, but if you don’t know the pattern, you’ll burn time and look slow.

---

## My Solution

```python
class Solution(object):
    def removeDuplicates(self, nums):  # this works cuz it's sorted
        n = len(nums)
        writing_pos = 2

        for i in range(2, n):
            if nums[writing_pos - 2] != nums[i]:
                nums[writing_pos] = nums[i]
                writing_pos += 1

        return writing_pos
```

## How This Actually Works

Because nums is sorted, duplicates appear in consecutive blocks.
That makes everything much easier.

We maintain a pointer writing_pos which marks where the next valid element should go.
We start it at 2, because the first two elements are always allowed.

Then for each element nums[i] starting from index 2:

Look back two positions: nums[writing_pos - 2]

If that value is different from nums[i], it means we haven't already placed two copies of this number

So it’s allowed → write it to nums[writing_pos]

Move writing_pos forward

If it's the same, skip it (it would make 3 duplicates)

At the end, writing_pos is the count of valid elements.

## Comments: 
Sorted array → duplicates are grouped.

To limit duplicates to 2, just compare against the element 2 positions back.

Real-world value: very low
