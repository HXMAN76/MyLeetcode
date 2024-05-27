## Algorithm:

### Problem Statement:
Given an array `nums` of non-negative integers, return `x` if there exists a number `x` such that exactly `x` numbers in `nums` are greater than or equal to `x`. If no such `x` exists, return `-1`.

### Approach:
1. **Sort the Array:**
   - Sort the array `nums` in ascending order.

2. **Iterate Over Possible Values of `x`:**
   - Iterate over possible values of `x` from `1` to `n` (where `n` is the length of `nums`).
   - For each `x`, count how many numbers in `nums` are greater than or equal to `x`.

3. **Check Condition:**
   - If the count of numbers greater than or equal to `x` equals `x`, return `x`.

4. **Return -1:**
   - If no such `x` is found after iterating through all possible values, return `-1`.
## My Submission
<a href = https://leetcode.com/problems/special-array-with-x-elements-greater-than-or-equal-x/submissions/1269174789/>![image.png](https://assets.leetcode.com/users/images/8a546b3d-6bc9-40a9-b64d-cb345b28b092_1716795037.979317.png)</a>
### Code:
```python
class Solution:
    def specialArray(self, nums: List[int]) -> int:
        nums.sort()
        n = len(nums)
    
        for x in range(1, n + 1):
            count = 0
            for num in nums:
                if num >= x:
                    count += 1
            if count == x:
                return x
        return -1
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
