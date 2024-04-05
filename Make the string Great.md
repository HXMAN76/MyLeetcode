# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Since strings are immutable we can create a mutable data type to store each char of a string while we store we can just give conditions so that characters when joined together form good string.

# Approach
<!-- Describe your approach to solving the problem. -->
We know that the Ascii difference between an uppercase and lowercase is 32.
We can create a list that stores each character and for iteration, check if the current character's Ascii value difference from the last character in the list, if the difference is 32 then pop out the last character , else append the character to list.
Return the list using the help of the join function.

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My submission
 
![Screenshot 2024-04-05 104058.png](https://assets.leetcode.com/users/images/3eb9d2ed-3ff6-4009-9ce2-fae34337d78a_1712294379.166079.png)

---


# Let's Code it 👨‍💻
```
class Solution(object):
    def makeGood(self, s):
        """
        :type s: str
        :rtype: str
        """
        lst = []
        for char in s:
            if len(lst) == 0:
                lst.append(char)
            elif lst and abs(ord(char) - ord(lst[-1])) == 32:
                lst.pop()
            else:
                lst.append(char)
        return "".join(lst)
```
