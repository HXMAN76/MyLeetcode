# Intuition  
To solve the problem of determining the minimum number of parentheses that need to be added to make a string of parentheses valid, I first thought about how parentheses work in pairs. A valid string requires that every opening parenthesis has a corresponding closing parenthesis. Therefore, the main goal is to count how many unmatched opening and closing parentheses exist in the string.  

# Approach  
The approach involves iterating through the string and maintaining two counters: one for unmatched opening parentheses (`open`) and another for unmatched closing parentheses (`stack`).   

1. For each character in the string:  
   - If it is an opening parenthesis `(`, increment the `open` counter.  
   - If it is a closing parenthesis `)`, check if there are any unmatched opening parentheses (`open > 0`):  
     - If there are, decrement the `open` counter (indicating that this closing parenthesis matches with one opening parenthesis).  
     - If there are not, increment the `stack` counter (indicating an unmatched closing parenthesis).  
   
2. At the end of the iteration, the total number of parentheses needed to make the string valid will be the sum of `open` (unmatched opening parentheses) and `stack` (unmatched closing parentheses).  

This approach ensures that we efficiently count the necessary additions in a single pass through the string.  

# Complexity  
- Time complexity: $$O(n)$$, where $$n$$ is the length of the string. We traverse the string once.  
- Space complexity: $$O(1)$$, as we are using only a fixed amount of extra space for the counters.
---
<a href = https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/submissions/1416587372/>![image.png](https://assets.leetcode.com/users/images/87135af9-3c09-481d-abb0-8d31e1d39865_1728448620.374075.png)</a>

# Code
```java []
class Solution {
    public int minAddToMakeValid(String s) {
        int open = 0;
        int stack = 0;
        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                open++;
            }
            if (ch == ')') {
                if (open > 0) {
                    open--;
                }
                else {
                    stack++;
                }
            }
        }
        return stack + open;
    }
}
```
