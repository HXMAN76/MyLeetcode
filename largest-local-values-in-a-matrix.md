# Complexity
- Time complexity: $$O(n^2)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n ^2)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My submission
<a href = https://leetcode.com/problems/largest-local-values-in-a-matrix/submissions/1256039742/>![image.png](https://assets.leetcode.com/users/images/785a7634-97d5-4b6e-bdd3-7ef124b64269_1715511283.03899.png)</a>
# Let's Code it down
```
class Solution:
    def largestLocal(self, grid: List[List[int]]) -> List[List[int]]:
        n, res = len(grid), []

        for i in range(1, n - 1):
            temp_row = []
            for j in range(1, n - 1):
                temp = 0

                for k in range(i - 1, i + 2):
                    for l in range(j - 1, j + 2):
                        temp = max(temp, grid[k][l])

                temp_row.append(temp)
            res.append(temp_row)

        return res
```
# Complexity
- Time complexity: $$O(n^2)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
```
class Solution:
    def largestLocal(self, grid):
        n = len(grid)

        for i in range(1, n - 1):
            for j in range(1, n - 1):
                temp = 0

                for k in range(i - 1, i + 2):
                    for l in range(j - 1, j + 2):
                        temp = max(temp, grid[k][l])

                grid[i - 1][j - 1] = temp

        n = len(grid)
        grid = [row[:n-2] for row in grid[:n-2]]

        return grid
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
