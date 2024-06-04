## Algorithm

### Problem Statement:
Given two strings `s` and `t`, you need to determine the minimum number of characters that should be appended to the end of `s` to make `t` a subsequence of `s`.

### Approach:
To find the minimum number of characters to append to `s` to make `t` a subsequence of `s`, follow these steps:

1. **Initialize Pointers:**
   - Use two pointers `s_index` and `t_index` to traverse the strings `s` and `t`, respectively.
   - Initialize `s_index` and `t_index` to 0.
   - Calculate the lengths of `s` and `t`, and store them in `s_length` and `t_length`.

2. **Traverse the Strings:**
   - Use a `while` loop to iterate over `s` and `t` while both indices are within their respective lengths.
   - If the characters at the current indices of `s` and `t` match (`s[s_index] == t[t_index]`), move the `t_index` pointer to the next character in `t`.
   - Always move the `s_index` pointer to the next character in `s`.

3. **Calculate the Result:**
   - The difference `t_length - t_index` gives the number of characters in `t` that were not matched in `s`.
   - Return this difference as the result, which represents the minimum number of characters that need to be appended to `s` to make `t` a subsequence.

# Complexity
- Time complexity: $$O(n + m)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My Submission
<a href = https://leetcode.com/problems/append-characters-to-string-to-make-subsequence/submissions/1277066629/>[image.png](https://assets.leetcode.com/users/images/8ec17585-80fb-4276-839a-8619df914962_1717479171.4278662.png)</a>
# Code
```
class Solution(object):
    def appendCharacters(self, s, t):
        s_index, t_index = 0, 0
        s_length, t_length = len(s), len(t)
    
        while s_index < s_length and t_index < t_length:
            if s[s_index] == t[t_index]:
                t_index += 1
            s_index += 1
    
        return t_length - t_index
        
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
