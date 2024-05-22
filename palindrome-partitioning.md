# Algorithm:

1. **Initialization:**
   - Initialize a dictionary `self.ans` to store the results of subproblems for memoization.

2. **Base Cases:**
   - If the input string `s` is already in `self.ans`, return the cached result.
   - If the length of `s` is 0, return `[[]]` as the only partition is an empty list.
   - If the length of `s` is 1, return `[[s]]` as the only partition is the string itself.

3. **Recursive Case:**
   - Initialize an empty list `result` to store the partitions.
   - Iterate over each possible prefix of `s` (from index 1 to len(s)):
     - If the prefix is a palindrome (it is equal to its reverse), create a list `left` containing this prefix.
     - Recursively partition the remaining substring `s[i:]` and store the result in `right`.
     - For each partition in `left`, combine it with each partition in `right` and append the combined list to `result`.

4. **Memoize and Return:**
   - Store the computed `result` in `self.ans[s]` for memoization.
   - Return the `result`.

## Time Complexity:
- The time complexity is O(n * 2^n), where n is the length of the input string `s`.
- This complexity arises because for each character in the string, we potentially create two branches: one that includes the character in a palindrome and one that does not.

## Space Complexity:
- The space complexity is O(n * 2^n) due to the storage of the results in the memoization dictionary and the recursion stack.
- The memoization dictionary `self.ans` can store up to O(2^n) entries, each with an average length of O(n).
---
# Sample Input:
- `s = "aab"`

## Step-by-Step Execution:

1. **Initialization:**
   - The `Solution` class is instantiated, initializing `self.ans` as an empty dictionary.

2. **First Call to `partition`:**
   - Call `partition("aab")`.

3. **Checking Memoization:**
   - `s = "aab"` is not in `self.ans`.

4. **Base Case Checks:**
   - `len("aab")` is not 0 or 1, so move to the recursive case.

5. **Recursive Case (first level):**
   - Initialize `result` as an empty list.
   - Iterate over each prefix of `"aab"`:

### First Level of Recursion:

**Iteration 1:**
- `i = 1`
  - `left` is empty initially.
  - `s[:1] = "a"` is a palindrome.
  - `left` becomes `[["a"]]`.
  - Call `partition("ab")`.

**Iteration 2:**
- `i = 2`
  - `left` is empty initially.
  - `s[:2] = "aa"` is a palindrome.
  - `left` becomes `[["aa"]]`.
  - Call `partition("b")`.

**Iteration 3:**
- `i = 3`
  - `s[:3] = "aab"` is not a palindrome, so no changes.

### Second Level of Recursion:

**Sub-call `partition("ab")`:**
  - `s = "ab"` is not in `self.ans`.
  - `len("ab")` is not 0 or 1, so move to the recursive case.
  - Initialize `result` as an empty list.
  - Iterate over each prefix of `"ab"`:

**Iteration 1:**
- `i = 1`
  - `left` is empty initially.
  - `s[:1] = "a"` is a palindrome.
  - `left` becomes `[["a"]]`.
  - Call `partition("b")`.

**Iteration 2:**
- `i = 2`
  - `s[:2] = "ab"` is not a palindrome, so no changes.

**Sub-call `partition("b")`:**
  - `s = "b"` is not in `self.ans`.
  - `len("b")` is 1, so return `[["b"]]`.

### Back to Second Level:

- Combine results from `left` and `right` for `"ab"`:
  - `left = [["a"]]` and `right = [["b"]]`.
  - Combine to form `[["a", "b"]]`.
  - Store result for `s = "ab"` in `self.ans` as `[["a", "b"]]`.

### First Level Continued:

**Sub-call `partition("b")`:**
  - `s = "b"` is already in `self.ans`, so return `[["b"]]`.

### Back to First Level:

- Combine results from `left` and `right` for `"aab"`:
  - For `i = 1`:
    - `left = [["a"]]` and `right = [["a", "b"]]`.
    - Combine to form `[["a", "a", "b"]]`.
  - For `i = 2`:
    - `left = [["aa"]]` and `right = [["b"]]`.
    - Combine to form `[["aa", "b"]]`.
  - Store result for `s = "aab"` in `self.ans` as `[["a", "a", "b"], ["aa", "b"]]`.

6. **Return Result:**
   - Return the final result `[["a", "a", "b"], ["aa", "b"]]`.

## Final Output:
- The partitions of the string `"aab"` that each substring is a palindrome are:
  - `[["a", "a", "b"], ["aa", "b"]]`.
---
# My Submission
<a href = https://leetcode.com/problems/palindrome-partitioning/submissions/1264531450>![image.png](https://assets.leetcode.com/users/images/ff033061-c98a-4c5a-ae2c-24a99eeb1662_1716350215.157369.png)</a>
# Code
```python
class Solution:
    def __init__(self):
        self.ans = {}
        
    def partition(self, s: str) -> List[List[str]]:
        if(s in self.ans):
            return self.ans[s]
        
        if(len(s) == 0):
             result = [[]]
        elif(len(s) == 1):
             result = [[s]]
        else:
            result = []
            for i in range(1, len(s) + 1):  
                left = []
                if(s[:i] == "".join(reversed(s[:i]))):
                    left.append([s[:i]])

                right = self.partition(s[i:])

                for l in left:
                    for r in right:
                        result.append(l + r)
        
        self.ans[s] = result
        return result
        
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
