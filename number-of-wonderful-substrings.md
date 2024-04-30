# Steps:
1. **Initialize Variables:**
`count`: Initialize an array of size 1024 to store the count of different states. The state here represents the count of characters in the substring. Since there are 10 lowercase letters, 10 bits are used to represent the state (hence 1024 combinations). Initialize `count[0]` to 1, representing the empty string where all characters occur an even number of times.
`mask`: Initialize a variable to represent the current state of the substring. Initially set to 0.
`res`: Initialize the result variable to 0.

2. **Iterate Through Word:**
Loop through each character c in the given word.
3. **Update Mask:**
Update the mask by XORing it with a bit shifted version of the current character c's position in the alphabet. This operation toggles the bit representing whether the character has an odd or even count in the current substring.
4. **Update Result:**
Increment the result res by the count of occurrences of the current mask state in the count array. This represents the number of wonderful substrings found so far.
Additionally, add the count of substrings where exactly one character occurs an odd number of times by summing over all possible single-bit flips of the current mask.
5. **Update Count:**
Increment the count of the current mask state by 1, indicating that we've seen this state once more.
6. Return Result:
Once the loop is complete, return the final result `res`, which represents the total number of wonderful substrings in the given word.
6. **Edge Cases Handling:**
The code initializes `count[0]` to handle the case of an empty string where all characters occur an even number of times.
The loop efficiently handles substrings of varying lengths by updating the state mask and counting substrings with different character counts.
# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ 1\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
>where n is number of characters present in the string
# My Submission
<a href = https://leetcode.com/problems/number-of-wonderful-substrings/submissions/1245397681/>![Screenshot 2024-04-30 084857.png](https://assets.leetcode.com/users/images/a9edf466-3c14-45e2-89ca-1651c8c19c34_1714447176.1005387.png)</a>


# Lets Code it down
```
class Solution:
    def wonderfulSubstrings(self, word: str) -> int:
        count = [0] * 1024 #to store how many time the state occurs
        count[0] = 1 #empty string gives case where all characters occurs even number of times
        mask = 0
        res = 0
        for c in word:
            mask ^= 1 << (ord(c) - ord('a')) #update the state
            res += count[mask] #to add the count of same previous state
            res += sum(count[mask ^ 1 << i] for i in range(10))
            count[mask] += 1 # add 1 to count of times we've seen current state
        return res
```
> ***Have a nice day...***
Upvote if you understood to solve.


