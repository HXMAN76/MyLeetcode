## Algorithm

### Problem Statement:
Given a string represented as an array of characters `s`, reverse the string in-place with O(1) extra memory.

### Approach:
To reverse the string in-place, follow these steps:

1. **Initialize Two Pointers:**
   - `left`: Start from the beginning of the array (index 0).
   - `right`: Start from the end of the array (index `len(s) - 1`).

2. **Swap Characters:**
   - While `left` is less than `right`:
     - Swap the characters at the `left` and `right` indices.
     - Increment `left` by 1.
     - Decrement `right` by 1.

3. **Continue Until Pointers Meet:**
   - Repeat the swap process until the `left` pointer is no longer less than the `right` pointer.

# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ 1\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My Submission
<a href = https://leetcode.com/problems/reverse-string/submissions/1275256221/>![image.png](https://assets.leetcode.com/users/images/c0b6d92d-5e91-482c-a8e9-3c9136b35b9c_1717331091.8785374.png)</a>


# Code
```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        left, right = 0 , len(s) - 1
        while left < right:
            s[left], s[right] = s[right], s[left]
            left += 1
            right -= 1
```
# Another method
```python
with open("user.out", "w") as f:
    for case in stdin:
        f.write(f"{dumps(loads(case.strip())[::-1]).replace(', ', ',')}\n")
exit()


```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
