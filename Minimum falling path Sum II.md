# My Submission
<a href = https://leetcode.com/problems/minimum-falling-path-sum-ii/submissions/1242152205/>![Screenshot 2024-04-26 085512.png](https://assets.leetcode.com/users/images/a31c87ad-05c2-4f82-80c2-5b1d334bdd9d_1714101946.7419748.png)</a>

# Complexity
- Time complexity: $$O( \ n ^2 \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ 1\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution(object):
    def minFallingPathSum(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        N = len(grid)
        DP = grid[0]

        for i in range(1, N):
            indx1 = DP.index(min(DP))
            indx2 = DP.index(min(DP[:indx1] + DP[indx1+1:]))
            for j in range(N):
                if j != indx1:
                    grid[i][j] += DP[indx1]
                else:
                    grid[i][j] += DP[indx2]
            DP = grid[i]

        return min(DP)
```
