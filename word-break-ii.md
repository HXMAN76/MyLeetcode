## Algorithm:

### Function: `wordBreak`
1. **Base Case:**
   - If the string `s` is empty or the `wordDict` is empty, return an empty list.

2. **Initialization:**
   - Convert `wordDict` to a set `words` for faster lookup.
   - Initialize an empty list `self.res` to store the results.

3. **Helper Function:**
   - Define a recursive helper function `helper(start, current)` to build valid sentences.
   - **Base Case:** If `start` equals the length of `s`, append the joined `current` list to `self.res` and return.
   - **Recursive Case:** Iterate over the substring from `start` to the end of `s`:
     - If the substring `s[start:i+1]` is in `words`, recursively call `helper` with the updated start position `i+1` and the current list `current` appended with the substring `s[start:i+1]`.

4. **Call Helper Function:**
   - Call `helper(0, [])` to start the recursion.

5. **Return Result:**
   - Return `self.res` containing all possible sentences formed by words in `wordDict`.

## Time Complexity:
- The time complexity is $$O(2^n)$$, where `n` is the length of the string `s`.
- This complexity arises because each substring can either be included in the current sentence or not, leading to a branching factor of 2.

## Space Complexity:
- The space complexity is $$O(n)$$, where `n` is the length of the string `s`.
- This includes the recursion stack and the space used for storing the results.

# My Submission
<a href = https://leetcode.com/problems/word-break-ii/submissions/1267122538/>![image.png](https://assets.leetcode.com/users/images/0c4fa356-b441-4939-a992-d9b826419e39_1716610107.556072.png)</a>

# Code
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> List[str]:
        if not s or not wordDict:
            return []

        words = set()
        for word in wordDict:
            words.add(word)

        self.res = []

        def helper(start, current):
            if start == len(s):
                self.res.append(" ".join(current[:]))
                return

            for i in range(start, len(s)):
                if s[start:i+1] in words:
                    # current.append(s[start:i+1])
                    helper(i+1, current + [s[start:i+1]])

        helper(0, [])
        return self.res

        
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
