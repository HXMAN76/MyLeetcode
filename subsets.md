## Algorithm:

1. **Initialize Result List:**
   - Start with `result` initialized to `[[]]`, which represents the empty subset.

2. **Iterate Over Each Number:**
   - For each number `num` in the input list `nums`:
     - Append new subsets to `result` by adding `num` to each existing subset in `result`.

3. **Return Result:**
   - Return the `result` list, which now contains all possible subsets of `nums`.

## Time Complexity:
- The algorithm iterates over each number in `nums`.
- For each number, it generates new subsets by iterating over the existing subsets in `result`.
- The number of subsets doubles with each new number added, leading to an overall time complexity of $$O(n * 2^n)$$, where n is the number of elements in `nums`.

## Space Complexity:
- The space complexity is $$O(2^n)$$ because the number of subsets generated is $$\ (2^n\  )$$, where n is the number of elements in `nums`.
- Each subset can be stored in O(n) space, but since we are considering the number of subsets, the dominant factor is$$ \ (2^n\ )$$.
# My Submission
<a href =https://leetcode.com/problems/subsets/submissions/1264510146>![image.png](https://assets.leetcode.com/users/images/bccb8934-8b7c-4463-8a9e-7bef3ce6b17a_1716348916.63176.png)</a>

# Let's Code it Down
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        result = [[]]
        for num in nums:
            result += [curr + [num] for curr in result]
        return result
```
---
# Another method
## Algorithm:

1. **Initialize Variables:**
   - `res` to store all subsets.
   - `subset` to store the current subset being constructed.

2. **Define DFS Function:**
   - Define a Depth-First Search (DFS) function `dfs(i)` that explores all possible subsets starting from index `i`.

3. **Base Case:**
   - If `i` is greater than or equal to the length of `nums`, append a copy of `subset` to `res` and return.

4. **Recursive Calls:**
   - Include `nums[i]` in the current subset:
     - Append `nums[i]` to `subset`.
     - Recursively call `dfs(i + 1)`.
   - Exclude `nums[i]` from the current subset:
     - Remove `nums[i]` from `subset`.
     - Recursively call `dfs(i + 1)`.

5. **Initial Call:**
   - Call `dfs(0)` to start the DFS from the first index.

6. **Return Result:**
   - Return the `res` list, which now contains all possible subsets of `nums`.

## Time Complexity:
- Each element in `nums` has two choices: to be included or not included in a subset.
- This results in  $$\ (2^n\ )$$ possible subsets, where n is the number of elements in `nums`.
- The DFS function is called for each subset, leading to a total time complexity of $$O(n * 2^n)$$, where n accounts for the time to copy subsets.

## Space Complexity:
- The space complexity is $$O(n)$$ for the recursion stack in the worst case (the depth of the recursion tree).
- Additionally, the space complexity for storing all subsets in `res` is $$O(2^n * n)$$ because there are $$\ (2^n\ )$$ subsets, and each subset can have up to n elements.
- Dominant space complexity: $$O(2^n * n)$$.
# My submission
<a href= https://leetcode.com/problems/subsets/submissions/1264511457>![image.png](https://assets.leetcode.com/users/images/cf7ea0b9-ddcb-4de4-9e17-645022b56db7_1716348245.3612823.png)
</a>

# Code:
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []
        subset = []

        def dfs(i):
            if i >= len(nums):
                res.append(subset.copy())
                return
            # decision to include nums[i]
            subset.append(nums[i])
            dfs(i + 1)
            # decision NOT to include nums[i]
            subset.pop()
            dfs(i + 1)

        dfs(0)
        return res
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
