## Algorithm:

### Function: `maxScoreWords`
1. **Initialization:**
   - Initialize `count` and `letters_count` as lists of size 26 (for each letter in the alphabet) with all elements set to 0.
   - Populate `count` with the frequency of each letter in the `letters` list.
   - Initialize `self.ans` to 0 to keep track of the maximum score.

2. **Backtracking Call:**
   - Call the `backtracking` function with initial values: `words`, `score`, `count`, `letters_count`, position `0`, and temporary score `0`.

### Function: `backtracking`
1. **Base Case:**
   - For each letter (from 'a' to 'z'), if `letters_count[i]` exceeds `count[i]`, return (invalid word usage).

2. **Update Maximum Score:**
   - Update `self.ans` with the maximum value between `self.ans` and `temp`.

3. **Recursive Case:**
   - Iterate through each word starting from the current position `pos`:
     - For each character in the word, update `letters_count` and add the corresponding score to `temp`.
     - Recursively call `backtracking` with the next position `i + 1` and updated `temp`.
     - After recursion, backtrack by resetting `letters_count` and `temp` to their previous values.

### Return Result:
- Return `self.ans` as the maximum score achievable with the given words and letters.

## Time Complexity:
- The time complexity is $$O(2^n * m)$$, where `n` is the number of words and `m` is the average length of a word.
- This complexity arises because each word can either be included or excluded, resulting in $$2^n$$ combinations, and checking each combination takes $$O(m)$$ time.

## Space Complexity:
- The space complexity is $$O(n + m)$$, where `n` is the number of words and `m` is the average length of a word.
- This includes the recursion stack and the auxiliary space used for `count` and `letters_count` lists.
## My Submission
<a href = https://leetcode.com/problems/maximum-score-words-formed-by-letters/submissions/1266307099/>![image.png](https://assets.leetcode.com/users/images/d0117e90-4e8e-4cb4-9143-bdb6d1e5698a_1716522890.0355394.png)</a>

---
## Code:
```python
class Solution:
    def maxScoreWords(self, words: List[str], letters: List[str], score: List[int]) -> int:
        count = [0] * 26
        letters_count = [0] * 26
        
        for c in letters:
            count[ord(c) - ord('a')] += 1
        
        self.ans = 0
        self.backtracking(words, score, count, letters_count, 0, 0)
        return self.ans
    
    def backtracking(self, words, score, count, letters_count, pos, temp):
        for i in range(26):
            if letters_count[i] > count[i]:
                return
        
        self.ans = max(self.ans, temp)
        
        for i in range(pos, len(words)):
            for c in words[i]:
                letters_count[ord(c) - ord('a')] += 1
                temp += score[ord(c) - ord('a')]
            
            self.backtracking(words, score, count, letters_count, i + 1, temp)
            
            for c in words[i]:
                letters_count[ord(c) - ord('a')] -= 1
                temp -= score[ord(c) - ord('a')]


```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
