# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
*To solve this problem think of a set of clothes like shirt and pants:*
**If number of shirts equals to number of pants then its ordered self to make self ordered we count all the shirt and pant from top to bottom and again from bottom to top whenever there is no pant to  shirt or vise-versa we remove them from self but never add them back.**

# Approach
<!-- Describe your approach to solving the problem. -->
1. Create a array and store each character of string in then iterate that string and if open parentheses is found increase the count, if close parentheses is found and count not equal to zero decrease the count else mark the string with some character to show the extra closed parentheses
2. Do the same for open parentheses by reverse iterating.
3. return the processed array as a string where marked characters are not converted.


# Complexity
- Time complexity:$$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:$$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My Submission
![Screenshot 2024-04-06 110812.png](https://assets.leetcode.com/users/images/d3fc404f-6026-4dd1-954e-4d5f51a0c1e6_1712381940.0090866.png)


---


# let's Code it down
```
class Solution(object):
    def minRemoveToMakeValid(self, s):
        """
        :type s: str
        :rtype: str
        """
        count = 0
        string = list(s)
        for i in range(len(s)):
            if s[i]  == '(':
                count += 1 
            elif s[i] == ')':
                if count == 0:
                    string[i] = '*'
                else:
                    count -= 1
        for i in range(len(string)-1 , -1, -1):
            if count > 0 and string[i] == '(':
                string[i] = '*'
                count -= 1

        return ''.join(c for c in string if c !='*')   
```
