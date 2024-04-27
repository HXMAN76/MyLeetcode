# Problem Explanation:

The problem involves finding the minimum number of steps required to spell out a given "key" string using a "ring" of characters. The ring can be rotated clockwise or anticlockwise to align characters with the key. Each rotation counts as one step.

# Solution Explanation:

The solution utilizes dynamic programming with memoization to efficiently solve the problem. It involves a recursive function `dfs` to explore all possible combinations of rotations and characters to find the minimum steps.

# Code Explanation:

1. `clock = [ring[i] for i in range(len(ring))]`, Creates a list clock containing the characters of the ring for clockwise rotation.
2. `cache = {}`, Initializes an empty dictionary for memoization.
3. Defines a recursive function `dfs` to calculate the minimum steps.
    1. Checks if the current state `(i, j)` has been computed before and returns the result from the `cache` if available.
    2. Simulate clockwise rotation to find the character `key[i]` on the ring.
    3. Simulate anticlockwise rotation to find the character `key[i]` on the ring.
    4. Calculates the minimum steps required for both clockwise and anticlockwise rotations and stores the result in the `cache`.
    5. Returns the minimum steps required for the current state `(i, j)`.
    
4. Initiates the DFS traversal from the starting state `(0, 0)`.

# My Submission
<a href = https://leetcode.com/problems/freedom-trail/submissions/1242944942/>![Screenshot 2024-04-27 094300.png](https://assets.leetcode.com/users/images/3da1a7ef-9ab1-4ea5-86c3-992d123ab7b5_1714191962.7669165.png)</a>


# Complexity
- Time complexity: $$O(\ n^2\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n^2\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution:
    def findRotateSteps(self, ring: str, key: str) -> int:
        clock = [ring[i] for i in range(len(ring))]
        cache = {}
        def dfs(i, j):
            if i >= len(key):
                return 0
            # clockwise
            if (i,j) in cache:
                return cache[(i,j)]
            c1 = 1
            s = j
            while ring[s] != key[i]:
                s = (s+1)%len(ring)
                c1 += 1
            c2 = 1
            p = j
            while ring[p] != key[i]:
                p = (len(ring)+p-1)%len(ring)
                c2 += 1
            cache[(i,j)] = min(c1+dfs(i+1,s), c2+dfs(i+1,p))
            return cache[(i,j)]
        return dfs(0,0)
            
```
