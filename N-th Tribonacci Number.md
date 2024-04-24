# Complexity
- Time complexity: $$O( \ n \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O( \ n \ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission
<a href = https://leetcode.com/problems/n-th-tribonacci-number/submissions/1240473089/>![image.png](https://assets.leetcode.com/users/images/50cc22a7-8b56-49de-8289-933eb9aa481c_1713934844.8672998.png)</a>

# Let's Code it down
**This is the submitted one.**
```
class Solution:
    def tribonacci(self, n: int) -> int:
        if n == 0:
            return 0
        elif n == 1 or n == 2:
            return 1
        
        dp = [0] * (n + 1)
        dp[1] = 1
        dp[2] = 1
        
        for i in range(3, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2] + dp[i - 3]
        
        return dp[n]
```
# Method 2
```
class Solution:
    def tribonacci(self, n: int) -> int:
        if n == 0:
            return 0
        if n == 1 or n == 2:
            return 1
        num0 = 0 
        num1 = 1
        num2 = 1
        c = 2
        while c < n:
            num3 = num1+ num2 + num0
            num0 = num1
            num1 = num2
            num2 = num3
            c += 1
        return num3
```
# Method 3
```
class Solution:
    def tribonacci(self, n: int) -> int:
        trib = [0, 1, 1]

        if n < 3:
            return trib[n]
        for i in range(3, n+1):
            trib[0], trib[1], trib[2] = trib[1], trib[2], sum(trib)
        return trib[2]
```
