
# Approach
<!-- Describe your approach to solving the problem. -->
The code defines a function that calculates the minimum number of pushes needed for a word on a keypad. 

Here’s how it works:

1. It counts how many times each letter appears in the word.
2. It sorts these counts in descending order.
3. It initializes the number of presses needed to 1 and a limit to track how many letters have been processed on a single "row" of the keypad.
4. It loops through each letter count:
   - If 8 letters have been processed, it increases the number of presses needed and resets the limit.
   - It adds to the total pushes needed by multiplying the current number of presses by the count of the letter.
5. Finally, it returns the total number of pushes needed.

In simple terms, the function finds out how many times you need to press buttons to type the word, based on how often each letter appears.
# Complexity
- Time complexity: $$O(n + k\ * \ log k)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(k)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
`If there are k unique letters.`
# Code
```
class Solution:
    def minimumPushes(self, word: str) -> int:
        count = Counter(word)
        keypad = sorted(count.values(), reverse = True)
        press = 1
        limit = 0
        res = 0
        for i in keypad:
            if limit == 8:
                press += 1
                limit = 0
            res += press * i
            limit += 1
        return res
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)

