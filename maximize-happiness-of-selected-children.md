# Algorithm
1. **Sort the List in Descending Order:** To efficiently select the children with the highest happiness values, we sort the list of happiness values in descending order.

2. **Initialize Variables:** Initialize total_happiness_sum to keep track of the sum of happiness values of the selected children. Initialize turns to keep track of the number of turns taken.

3. **Iterate for K Turns:** We iterate for k turns, where in each turn, we:
        - Access the happiness value of the child at index i (where i ranges from 0 to k-1 due to sorting).
        - Decrement the happiness value by the number of turns taken so far. This accounts for the decrement in happiness for all unselected children.
        - Add the adjusted happiness value to total_happiness_sum. Ensure that negative happiness values are not considered by taking the maximum of 0 and the computed value.
        - Increment the turns variable to prepare for the next iteration.
4. **Return Total Happiness Sum:** After k turns, return the total happiness sum, which represents the maximum sum of happiness values achievable by selecting k children.
# Complexity
- Time complexity: $$O(\ k\ *\ n\ *\ log(\ n\ )\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My submission
<a href = https://leetcode.com/problems/maximize-happiness-of-selected-children/submissions/1253144155/>![Screenshot 2024-05-09 083338.png](https://assets.leetcode.com/users/images/49ce35bb-cf07-40ff-9986-8321f8a27b8e_1715226843.5414786.png)</a>
# Let's Code it down
```
class Solution:
    def maximumHappinessSum(self, happiness: List[int], k: int) -> int:
        # Sort in descending order
        happiness.sort(reverse=True)

        total_happiness_sum = 0
        turns = 0

        # Calculate the maximum happiness sum
        for i in range(k):
            # Adjust happiness and ensure it's not negative
            total_happiness_sum += max(happiness[i] - turns, 0)

            # Increment turns for the next iteration
            turns += 1

        return total_happiness_sum
```
# The best code
```
class Solution:
    def maximumHappinessSum(self, happiness: List[int], k: int) -> int:
        children = sorted(happiness, reverse=True)

        # Fast calc if no child hits zero happiness
        # Could do binary search to see if I can do half, quarter, etc this way
        if children[k-1] >= k-1:
            return sum(children[:k]) - ((0 + k-1) * k // 2)

        # Else slow way
        res = 0
        for i, h in enumerate(children[:k]):
            if h - i <= 0:
                break
            res += h - i

        return res
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
