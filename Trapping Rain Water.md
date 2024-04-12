# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
> 1. *An element of the array can store water if there are higher bars on the left and the right.* 
> 2. *The amount of water to be stored in every position can be found by finding the heights of bars on the left and right sides.* 
> 3. *The total amount of water stored is the summation of the water stored in each index.*

---

# Approach
<!-- Describe your approach to solving the problem. -->
We can keep a track of the array from start and end using 2 variables
`front_max` and `back_max` which is an element of array `height`.
1. Use while loop to iterate from the start of array till end.
2. if `front_max` is LESS THAN that `back_max` (ie.,front wall level is less that back wall level):
        - Increment the index `front` by 1
        - find the max of current value and next value
        - add the max value to `res` *(Note : subract with the next value before addition)*
3. else 
        - Decrement the index `back` by 1
        - find the max of current value and previous value
        - add the max value to `res` *(Note : subract with the previous value before addition)*
# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---



# My Submission
![Screenshot 2024-04-12 104233.png](https://assets.leetcode.com/users/images/6ae5ad11-41c0-4ed4-8a3c-8716a6a1f323_1712900095.2765446.png)

---


# Let's Code it down
```
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        if not height:
            return 0
        front, back = 0, len(height) - 1
        res = 0
        front_max, back_max = height[front], height[back]
        while front < back:
            if front_max < back_max:
                front += 1
                front_max = max(front_max, height[front])
                res += front_max - height[front]
            else:
                back -= 1
                back_max = max(back_max, height[back])
                res += back_max - height[back]
        return res
```

> Have a nice day, Upvoting would make mine too.
