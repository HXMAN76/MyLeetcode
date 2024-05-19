## Algorithm:

1. **Initialize Variables:**
   - `sumVal` to store the sum of the original node values.
   - `count` to keep track of the number of nodes with a positive net change.
   - `positiveMinimum` to keep track of the smallest positive net change, initialized to a very large value.
   - `negativeMaximum` to keep track of the largest negative net change, initialized to a very small value.

2. **Iterate Over Node Values:**
   - For each node value in `nums`:
     - Calculate `operatedNodeValue` as the XOR of the node value and `k`.
     - Update `sumVal` by adding the original node value.
     - Calculate `netChange` as the difference between `operatedNodeValue` and the original node value.
     - If `netChange` is positive:
       - Update `positiveMinimum` to be the minimum of `positiveMinimum` and `netChange`.
       - Update `sumVal` by adding `netChange`.
       - Increment `count`.
     - Otherwise, update `negativeMaximum` to be the maximum of `negativeMaximum` and `netChange`.

3. **Check the Count of Positive Net Changes:**
   - If `count` is even, return `sumVal`.
   - Otherwise, return the maximum of `sumVal - positiveMinimum` and `sumVal + negativeMaximum`.

## Time Complexity:
- The algorithm iterates over the list `nums` exactly once, resulting in a time complexity of $$O(n)$$, where n is the number of elements in `nums`.
- The other operations (calculations and comparisons) within the loop take constant time.

## Space Complexity:
- The space complexity is $$O(1)$$ because the algorithm uses a constant amount of extra space regardless of the input size.
---
## My Submission
<a href = https://leetcode.com/problems/find-the-maximum-sum-of-node-values/submissions/1261729908/>![image.png](https://assets.leetcode.com/users/images/6f885e6f-d7b5-4480-aa77-3134827ec6a0_1716085639.2538853.png)</a>
## Let's Code it down
```
class Solution:
    def maximumValueSum(self, nums: List[int], k: int, edges: List[List[int]]) -> int:
        sumVal = 0
        count = 0
        positiveMinimum = 1 << 30
        negativeMaximum = -1 * (1 << 30)

        for nodeValue in nums:
            operatedNodeValue = nodeValue ^ k
            sumVal += nodeValue
            netChange = operatedNodeValue - nodeValue
            if netChange > 0:
                positiveMinimum = min(positiveMinimum, netChange)
                sumVal += netChange
                count += 1
            else:
                negativeMaximum = max(negativeMaximum, netChange)

        # If the number of positive netChange values is even, return the sum.
        if count % 2 == 0:
            return sumVal

        # Otherwise return the maximum of both discussed cases.
        return max(sumVal - positiveMinimum, sumVal + negativeMaximum)


```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
