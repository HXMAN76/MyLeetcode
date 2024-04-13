> # Complexity
- Time complexity: $$O(m \ (n \ * \ n))$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(m \ * \ n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->


---

# Code
```
class Solution(object):
    def maximalRectangle(self, matrix):
        """
        :type matrix: List[List[str]]
        :rtype: int
        """
        if not matrix or len(matrix) == 0 or len(matrix[0]) == 0:
            return 0
        m = len(matrix)
        n = len(matrix[0])
        maxRectangle = 0
        dp = {}
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == '0':
                    dp[(i,j)] = (0,0)
                else:
                    x = dp[(i,j-1)][0]+1 if j > 0 else 1
                    y = dp[(i-1,j)][1]+1 if i > 0 else 1
                    dp[(i, j)] = (x,y)
                    maxRectangle = max(x,y,maxRectangle)
                    minWidth = x
                    for r in range(i-1,i-y,-1):
                        minWidth = min(minWidth, dp[(r,j)][0])
                        maxRectangle = max(maxRectangle,minWidth*(i-r+1))
        
        return maxRectangle
```
