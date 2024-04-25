# Complexity
- Time complexity: $$O( \ n ^2 \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O( \ 1 \ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission 
<a href=https://leetcode.com/problems/longest-ideal-subsequence/submissions/1241415449/?source=submission-noac>
![image.png](https://assets.leetcode.com/users/images/921d2331-c5ed-40c1-88f3-849dc1885c75_1714025466.7919538.png)
</a>


# Code
```
class Solution:
    def longestIdealString(self, s: str, k: int) -> int:
        dp = [0] * 27
        n = len(s)

        for i in range(n - 1, -1, -1):
            cc = s[i]
            idx = ord(cc) - ord('a')
            maxi = float('-inf')

            left = max((idx - k), 0)
            right = min((idx + k), 26)

            for j in range(left, right + 1):
                maxi = max(maxi, dp[j])

            dp[idx] = maxi + 1

        return max(dp)
```
