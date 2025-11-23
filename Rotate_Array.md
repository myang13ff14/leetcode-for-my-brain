# 189. Rotate Array

## Problem Summary

You’re given an array `nums` and a number `k`.  
Rotate the array to the right by `k` steps **in-place**.

Essentially:  
**“Take the last k elements and move them to the front. Don’t create a new array… except you basically will anyway.”**

Another LeetCode classic where they pretend Python slicing isn’t a thing.

---

## My Solution

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        n = len(nums)
        k = k % n
        temp = nums[:(n - k)]
        nums[:k] = nums[(n - k):]
        nums[k:] = temp
```

## How This Actually Works

First take k % n to avoid useless full rotations (I couldn't think of using k%n at first until I see other people's solution)

The last k elements are supposed to become the front

The first n - k elements get pushed to the back

So we:

Save the front part:
temp = nums[:n - k]

Move the tail to the front:
nums[:k] = nums[n - k:]

Put the saved part after it:
nums[k:] = temp

And just like that, the array is rotated.


## Comments

In real Python, this is the most natural implementation. Sure, it’s not “in-place,” but outside of algorithm-heavy SDE interviews, nobody is going to die because you used an extra list. Real-world Python engineers care about readability and correctness, not proving they can manually rotate arrays like it's C in 1995.
