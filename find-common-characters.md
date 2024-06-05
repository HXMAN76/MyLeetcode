## Algorithm Explanation

### Problem Statement
Given an array of strings `words`, return a list of all characters that show up in all strings within the list (including duplicates). You may return the answer in any order.

### Approach
1. **Count Frequencies**:
    - Create a `count` method that takes a string and returns a list of 26 integers representing the frequency of each character (from 'a' to 'z') in the string.
    - The frequency list is indexed by the position of the character in the alphabet (i.e., 0 for 'a', 1 for 'b', etc.).

2. **Find Intersection**:
    - Create an `intersection` method that takes two frequency lists and returns a new list where each element is the minimum of the corresponding elements from the two input lists. This effectively finds the common minimum frequency for each character between two words.

3. **Compute Common Characters**:
    - Initialize the frequency list with the character counts from the first word.
    - Iterate through the remaining words, updating the frequency list to be the intersection of itself and the character counts of the current word.
    - After processing all words, the frequency list will contain the minimum frequency of each character that appears in every word.

4. **Construct Result**:
    - Initialize an empty result list.
    - For each character (from 'a' to 'z'), add the character to the result list as many times as its frequency in the final frequency list.
    - Return the result list.

### Time Complexity
- **Counting Frequencies**: The `count` function iterates through each character in the word, so it has a time complexity of $$(O(L)$$, where $$(L)$$ is the length of the word.
- **Finding Intersection**: The `intersection` function compares two lists of size 26, which takes  $$(O(1))$$ time.
- **Main Function**:
  - Counting frequencies for each word takes $$\ (O(W * L) \ )$$, where $$W$$ is the number of words and $$L$$ is the maximum length of a word.
  - Updating the frequency list for each word also takes $$\ (O(W * L) \ )$$ because each word's frequency list is calculated and intersected.
  - Constructing the result list takes $$(O(26)$$ = $$O(1)$$.

Therefore, the overall time complexity is $$\ (O(W * L) \ )$$.

### Space Complexity
- **Frequency Lists**: Each frequency list has a fixed size of 26, which is $$O(1)$$ space.
- **Result List**: In the worst case, the result list can contain all characters of all words, which would be $$\ (O(W * L) \ )$$.
- **Auxiliary Space**: Apart from the input and output storage, additional space for variables is negligible.

Therefore, the overall space complexity is $$\ (O(W * L) \ )$$ in the worst case.

### Example
**Input**: `["bella","label","roller"]`

**Output**: `["e","l","l"]`

**Explanation**:
1. Frequency of "bella": [1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
2. Frequency of "label": [1, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
3. Frequency of "roller": [1, 0, 0, 0, 0, 0, 0, 0, 1, 0, 1, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0]
4. Intersection: [1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0] -> 'e'
5. Final result: `["e","l","l"]`

# My Submission
<a href = https://leetcode.com/problems/find-common-characters/submissions/1278222802/>![image.png](https://assets.leetcode.com/users/images/a146337e-79ed-4a70-8da8-fb92f077d059_1717572968.562069.png)</a>
# Code
```
class Solution(object):
    def count(self, word):
        frequency = [0] * 26
        for char in word:
            frequency[ord(char) - ord('a')] += 1
        return frequency

    def intersection(self, freq1, freq2):
        return [min(f1, f2) for f1, f2 in zip(freq1, freq2)]

    def commonChars(self, words):
        # Initialize the frequency array with the count of the first word
        last = self.count(words[0])
        
        # Update the frequency array by taking intersections with counts of remaining words
        for word in words[1:]:
            last = self.intersection(last, self.count(word))
        
        # Construct the result list
        result = []
        for i in range(26):
            result.extend([chr(i + ord('a'))] * last[i])
        
        return result
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
