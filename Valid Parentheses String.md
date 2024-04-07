# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
> We can count each of the characters and if parentheses counts are same the * character doesn't count,else make the * to increment or decrement a count.

# Approach
<!-- Describe your approach to solving the problem. -->
One way to approach this problem is to use a greedy strategy.
Keep the track of variables to iterate the string we can use variables
`open` and `close`.
1. ***Initialise the parameters to zero***
2. ***Iterate through the string***
3. ***If `'('` is found increment open and close by 1,if `')'` is found decrement the variables by 1 and if `'*'` is found increment close by 1 and decrement open by 1.***
4. ***While iteration if close becomes negative (it means there are more closing parentheses than opening ones.)then return false, also if open becomes negative reset it to 0 since we can't have negative open parentheses count.***
5. ***After the iteration check if open is eqaul to zero if zero then return true else false.***

---


# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My Submission
![Screenshot 2024-04-07 092950.png](https://assets.leetcode.com/users/images/b6dfaee7-48f7-415a-8186-924eb9401050_1712462452.9499447.png)

# Code
```
class Solution(object):
    def checkValidString(self, s):
        """
        :type s: str
        :rtype: bool
        """
        open = 0
        close = 0
        for i in s:
            if i  == '(':
                open += 1
                close += 1
            elif i == ')':
                open -= 1
                close -= 1
            elif i == '*':
                open -= 1
                close += 1
            else:
                return False
            if close < 0:
                return False
            if open < 0:
                open = 0
        return open == 0 
        
```
> Have a nice day...
