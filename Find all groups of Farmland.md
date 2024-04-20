
# Complexity
> - Time complexity: $$O( \ n ^2 \ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

> - Space complexity: $$O( \ n \ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My Submission
<a href=https://leetcode.com/problems/find-all-groups-of-farmland/submissions/1237037027/>![Screenshot 2024-04-20 094433.png](https://assets.leetcode.com/users/images/97ce7e84-1b0b-4caa-b5f2-3f72166e5805_1713586627.5038702.png)</a>

---


# Code
```
class Solution:
    def findFarmland(self, land: List[List[int]]) -> List[List[int]]:
        m, n, res = len(land), len(land[0]), []
        for i in range(m):
            j = 0
            while j < n:
                if land[i][j]:
                    if land[i][j] == 1:
                        k, l = j+1, i+1
                        while k < n and land[i][k]==1: k += 1
                        k += 1
                        while l < m and land[l][j]==1:
                            land[l][j] = -k
                            l += 1
                        if l < m:
                            land[l][j] = 1-k
                        res.append([i,j,l-1,k-2])
                        j = k
                    else:
                        j = -land[i][j]
                else:
                    j += 1
        return res

        
```
> ***Have a nice day...***
