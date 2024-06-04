## Algorithm

### Problem Statement:
Given a string `s`, find the length of the longest palindrome that can be built with the letters of `s`. 

### Approach:
To find the longest palindrome length, follow these steps:

1. **Initialize a Set:**
   - Use a set `char_set` to keep track of characters with odd frequencies.
   - Initialize `length` to keep track of the length of the longest palindrome.

2. **Iterate Over Characters:**
   - For each character `char` in the string `s`:
     - If `char` is already in `char_set`, remove it from the set and increase `length` by 2 (since we found a pair).
     - If `char` is not in `char_set`, add it to the set.

3. **Adjust for Odd Frequency Characters:**
   - After processing all characters, if there are any characters left in `char_set` (meaning there is at least one character with an odd frequency), add 1 to `length` to account for the middle character of the palindrome.

4. **Return Result:**
   - Return the total `length` of the longest palindrome.
## My Submission
<a href = https://leetcode.com/problems/longest-palindrome/submissions/1277065663/>![image.png](https://assets.leetcode.com/users/images/ac4c2a6b-4e3a-4551-9660-44782a2c3fbc_1717478280.9525857.png)</a>
# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```python
class Solution:
    def longestPalindrome(self, s: str) -> int:
        # Initialize a set to keep track of characters with odd frequencies
        char_set = set()
        # Initialize the length of the longest palindrome
        length = 0
        
        # Iterate over each character in the string
        for char in s:
            # If the character is already in the set, remove it and increase the length by 2
            if char in char_set:
                char_set.remove(char)
                length += 2
            # If the character is not in the set, add it to the set
            else:
                char_set.add(char)
        
        # If there are any characters left in the set, add 1 to the length for the middle character
        if char_set:
            length += 1
        
        # Return the total length of the longest palindrome
        return length
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
