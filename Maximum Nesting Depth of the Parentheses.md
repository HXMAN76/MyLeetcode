# Question
A string is a valid parentheses string (denoted VPS) if it meets one of the following:

It is an empty string "", or a single character not equal to "(" or ")",
It can be written as AB (A concatenated with B), where A and B are VPS's, or
It can be written as (A), where A is a VPS.
We can similarly define the nesting depth depth(S) of any VPS S as follows:

depth("") = 0
depth(C) = 0, where C is a string with a single character not equal to "(" or ")".
depth(A + B) = max(depth(A), depth(B)), where A and B are VPS's.
depth("(" + A + ")") = 1 + depth(A), where A is a VPS.
For example, "", "()()", and "()(()())" are VPS's (with nesting depths 0, 1, and 2), and ")(" and "(()" are not VPS's.

Given a VPS represented as string s, return the nesting depth of s.
# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
*My Approach started by assuming the string as a building where "(" and ")" are go up and come down stairs which means the depths are just floor number and there is also condition that , number of "(" should be equal to ")".*

# Approach
<!-- Describe your approach to solving the problem. -->
1. Create two variables and assign them to zero, One is to hold the max value and another is to hold current depth value.
2. Iterate through the string:
**Condition 1:** If u get an open parentheses increase the depth level by 1
**Condition 2:** If u get a closed parentheses decrease the depth level by 1 , also depth should not go to less than zero which means there is extra parentheses.
3. Make the comparison between the increased depth value to max_depth value and return it.


# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---

## My Submission 
![Screenshot 2024-04-04 093534.png](https://assets.leetcode.com/users/images/1dbac51e-350f-4b74-9ec6-85a08dcb2387_1712203580.044442.png)

---



# Lets code it down 👨‍💻
```
class Solution(object):
    def maxDepth(self, s):
        """
        :type s: str
        :rtype: int
        """
        depth = 0
        max_depth = 0
        for i in s:
            if i == "(":
                depth = depth + 1
                max_depth = max(max_depth, depth) 
            if i == ")":
                depth = depth - 1
                if depth < 0:
                    return -1
        return max_depth

        
```
