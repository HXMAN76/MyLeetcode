## Algorithm:

### Problem Statement:
Given two strings `s` and `t` of the same length and an integer `maxCost`, return the maximum length of a substring of `s` that can be changed to be the same as the corresponding substring of `t` with a cost less than or equal to `maxCost`. The cost of changing the i-th character from `s` to `t` is `|s[i] - t[i]|`.

### Approach:
The problem can be solved using the sliding window technique:

1. **Initialize Variables:**
   - `left` to track the left boundary of the window.
   - `maxSubstring` to store the maximum length of valid substring found.
   - `strLen` to store the length of string `s`.
   - `totalCost` to accumulate the cost of changes in the current window.

2. **Expand the Right Boundary:**
   - Iterate over each character in the string `s` using `right` as the right boundary of the window.
   - Add the cost of changing the current character `s[right]` to `t[right]` to `totalCost`.

3. **Shrink the Left Boundary:**
   - If `totalCost` exceeds `maxCost`, increment `left` to shrink the window from the left until `totalCost` is within `maxCost`.

4. **Update Maximum Substring Length:**
   - Update `maxSubstring` with the maximum length of the current valid window.

5. **Return Result:**
   - Return `maxSubstring` as the result.
# My Submission
<a href = https://leetcode.com/problems/get-equal-substrings-within-budget/submissions/1270027203/>![image.png](https://assets.leetcode.com/users/images/97446e12-f490-4a22-b963-ec9be0a050b2_1716870108.5836883.png)</a>
# Code:
```python
class Solution:
    def equalSubstring(self, s: str, t: str, maxCost: int) -> int:
        left = 0
        maxSubstring = 0
        strLen = len(s)
        totalCost = 0
        for right in range(strLen):
            totalCost += abs(ord(s[right]) - ord(t[right]))
            while totalCost > maxCost:
                totalCost -= abs(ord(s[left]) - ord(t[left]))
                left += 1
            maxSubstring = max(maxSubstring, right - left + 1)
        return maxSubstring
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)get-equal-substrings-within-budget/
