# Algorithm
1. Initialize a hash set named `negative` to store negative numbers.
2. Iterate over nums and add negative numbers to `negative`.
3. Initialize `res` to -1.
4. Iterate over nums:
    - For each `i`, check if `i` is greater than ans and if -num exists in the neg set.
    - If the condition is true, update `res` to `i`.
    - Return `res`.
# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission
<a href= https://leetcode.com/problems/largest-positive-integer-that-exists-with-its-negative/submissions/1247062516/>![Screenshot 2024-05-02 093313.png](https://assets.leetcode.com/users/images/b6fdd762-62f2-412d-a572-e228f01728f8_1714622670.6453655.png)
</a>

# Let's Code it down
```
class Solution:
    def findMaxK(self, nums: List[int]) -> int:
        negative = set() #to have only negative numbers.
        for i in nums: 
            if i < 0:
                negative.add(i) #add all the negative values.
        res = -1 #variable to hold the result
        for i in nums:
            if i > res and -i in negative:
                ans = i #if i is positive and negative pair exist then res = ans
        return res        
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
