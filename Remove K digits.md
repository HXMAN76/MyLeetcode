<!-- Describe your first thoughts on how to solve this problem. -->
# Intution:
1. The problem requires us to minimize the resulting number by removing k digits from the given number num.
2. A greedy approach is suitable because at each step (processing each digit), we make a locally optimal choice (keeping the smallest possible digit) with the aim of achieving the overall optimal solution (smallest resulting number).
3. By prioritizing smaller digits for the most significant places (leftmost positions), we ensure that the resulting number is minimized.

# Approach
<!-- Describe your approach to solving the problem. -->
> - Initialize an empty array.
> - Traverse each digit of num.
> - For each digit, use `while` loop to check if the `array` is not empty and `k` is greater than zero, check if the current `i-th number` is smaller than the top of the stack (`array`). If so, pop from the array and decrement `k` by 1.
> - Push the current `i-th number` into the `array`.
> - After processing all numbers, handle remaining `k` (it can not zero sometimes due to the possibilty of numbers being equal) by popping from the `array`.
> - Construct the resulting number from the array using `join` and remove any leading zeros using `strip`.
> - Return the smallest possible number as a `string`.

# Complexity
- Time complexity: $$O(n \ * \ m)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:$$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My Submission
![Screenshot 2024-04-11 095851.png](https://assets.leetcode.com/users/images/8d818285-0243-449b-bcab-b8ef6aa53019_1712810884.6312995.png)


---


# Let's Code it down
```
class Solution(object):
    def removeKdigits(self, num, k):
        """
        :type num: str
        :type k: int
        :rtype: str
        """
        new = []
        for i in num:
            while new and k > 0 and new[-1] > i:
                new.pop()
                k -= 1
            new.append(i)
        if k > 0:
            new = new[:-k]
        
        result = ''.join(new).lstrip('0')
        
        if result:
            return result
        else:
            return '0'
            
```

> First, solve the problem. Then, write the code.
Have a nice day, Upvoting will make mine a nicer one.

