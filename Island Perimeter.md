# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
> *We could use a iterative call to check for the land or water and append the perimeter variable by 4 and reduce variable by 2 if nearby land is found.*

---


# Approach
<!-- Describe your approach to solving the problem. -->
1. Initalise a variable `perimeter` to store the result , `rows` and `cols` to store length of the rows and columns of the input. 
2. Iterate the 2D array using loop and if `grid[row][col] == 1` increment `perimeter` by 4 and if previous row-th element or col-th element is 1 then decrement by 2
3. return the `perimeter` after the iterations.  


---


# Complexity
- Time complexity: $$O( \ n ^2 \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O( \ 1 \ ) $$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My Submission
<a href = https://leetcode.com/problems/island-perimeter/submissions/1235483462/></a>
![Screenshot 2024-04-18 112721.png](https://assets.leetcode.com/users/images/fa4ed787-fe48-4f3d-9092-933743618c8b_1713420357.6290524.png)

---


# Let's Code it down 👨🏻‍💻
```
class Solution(object):
    def islandPerimeter(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        perimeter = 0 
        rows , cols = len(grid), len(grid[0])
        for row in range(rows):
            for col in range(cols):
                if grid[row][col] == 1:
                    perimeter += 4
                    if row > 0 and grid[row - 1][col] == 1:
                        perimeter -= 2
                    if col > 0 and grid[row][col - 1] == 1:
                        perimeter -= 2
        return perimeter
        
```
![Img](https://camo.githubusercontent.com/87ae3dcd6945f437a57dcfb3193e9fd58e1580b0292491fa649c9bf1b33eaede/68747470733a2f2f692e696d67666c69702e636f6d2f32387262746c2e6a7067)

> *Have a Nice Day...*
