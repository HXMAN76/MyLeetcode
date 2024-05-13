# Algorithm
**Maximize MSBs Across All Rows:**

- **Initial Check:** For each row, check if the first bit (MSB) is 0.
Flip Rows: If the MSB of any row is 0, flip the entire row. This ensures that the highest value bit in every row contributes the maximum possible value.
Optimize Columns for Maximum 1s:

- **Column Iteration:** After ensuring all rows start with a 1, examine the remaining columns from the second to the last.
Majority Check: For each column, check if the number of 0s exceeds the number of 1s.

- **Flip Columns:** If flipping a column results in more 1s than 0s, proceed to flip it. This strategy increases the binary value of more rows since each column beyond the first still contributes significantly to the total score.

- **Calculate the Final Score:**

    1. *Binary to Decimal:* Convert each row to its decimal equivalent by interpreting it as a binary number.

    2. *Summation:* Sum these decimal values to get the total score of the matrix after all optimizations.

---


# Complexity
- Time complexity: $$O(n ^2)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My Submission
> ***Click the image to see my submission***
<a href = https://leetcode.com/problems/score-after-flipping-matrix/submissions/1256548491/>![image.png](https://assets.leetcode.com/users/images/7591ce89-04b2-4626-b6b6-fcfb5e457bac_1715567512.2182808.png)</a>
# Let's Code it Down
```
class Solution:
    def matrixScore(self, grid: List[List[int]]) -> int:
        nRows, nCols = len(grid), len(grid[0])

        def flipRow(row):
            for col in range(nCols):
                grid[row][col] = 1 - grid[row][col] 

        def flipCol(col):
            for row in range(nRows):
                grid[row][col] = 1 - grid[row][col]

        def checkRow(nums):
            return int(''.join([str(num) for num in nums]), 2)
        for row in range(nRows):
            if grid[row][0] == 0:
                flipRow(row)
        for col in range(1, nCols):
            if sum(grid[r][col] for r in range(nRows)) * 2 < nRows:
                flipCol(col)
        return sum(checkRow(row) for row in grid)
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
