# Intuition  
The problem involves counting the number of transformations that can be made on a string consisting of '0's and '1's. Each '0' in the string can be transformed based on the number of preceding '1's (or "black balls"). The intuition is that for every '0' encountered, the number of transformations possible is equal to the number of '1's that have been seen before it. Therefore, as we traverse the string, we can maintain a count of '1's and use that to calculate the total transformations for each '0'.  

# Approach  
To solve the problem, we will iterate through the string character by character. We will maintain two variables:   
- `res` to accumulate the total number of transformations.  
- `blackballs` to count the number of '1's encountered so far.  

For each character in the string:  
- If the character is '0', we add the current count of `blackballs` to `res`, as this represents the number of transformations possible for this '0'.  
- If the character is '1', we increment the `blackballs` counter.  

At the end of the iteration, `res` will contain the total number of transformations possible, which we return as the result.  

# Complexity  
- Time complexity: $$O(n)$$  
  - The algorithm processes each character in the string exactly once.  
  
- Space complexity: $$O(1)$$  
  - We use a constant amount of space for the variables `res` and `blackballs`, regardless of the input size.
---
<a href = https://leetcode.com/problems/separate-black-and-white-balls/submissions/1423154521/>![image.png](https://assets.leetcode.com/users/images/f1e70ad5-9606-4089-9646-f650f07e6054_1729004083.1821449.png)</a>

# Code
```java []
class Solution {
    public long minimumSteps(String s) {
        long res = 0;
        int blackballs = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '0') {
                res += (long) blackballs; 
            }
            else {
                blackballs++;
            }
        }
        return res;
    }
}
```
