## Algorithm Explanation

### Problem Statement
Given a deck of cards represented by a list `hand` and an integer `groupSize`, determine if the deck can be rearranged into groups of `groupSize` consecutive cards.

### Approach
1. **Check Grouping Feasibility**:
    - First, check if the length of `hand` is divisible by `groupSize`. If not, it's impossible to form groups, so return `False`.

2. **Count Card Frequencies**:
    - Use a `Counter` to count the occurrences of each card in `hand`.

3. **Sort Unique Card Values**:
    - Extract and sort the unique card values from the `Counter`.

4. **Form Consecutive Groups**:
    - Iterate through the sorted card values.
    - For each card value, if there are still cards of this value available (i.e., `count[key] > 0`), try to form a group starting from this card.
    - Check if there are enough cards to form a consecutive group of size `groupSize`. If any card in the range has fewer occurrences than required, return `False`.
    - Deduct the count of cards used to form the group.

5. **Return Result**:
    - If all groups are successfully formed, return `True`.

### Time Complexity
- Counting card frequencies takes \(O(n)\), where \(n\) is the length of `hand`.
- Sorting the unique card values takes \(O(m \log m)\), where \(m\) is the number of unique card values.
- Forming consecutive groups involves iterating over the unique card values and checking counts, which takes \(O(m \cdot \text{groupSize})\).
  
Overall, the time complexity is \(O(n + m \log m + m \cdot \text{groupSize})\).

### Space Complexity
- The space required for the `Counter` and sorted keys is \(O(m)\), where \(m\) is the number of unique card values.
- No additional space proportional to the input size is used, thus the overall space complexity is \(O(m)\).

### Example
**Input**: `hand = [1,2,3,6,2,3,4,7,8]`, `groupSize = 3`

**Output**: `True`

**Explanation**:
1. Count card frequencies: `{1:1, 2:2, 3:2, 4:1, 6:1, 7:1, 8:1}`
2. Sorted unique card values: `[1, 2, 3, 4, 6, 7, 8]`
3. Form groups:
    - Group starting from 1: [1, 2, 3]
    - Group starting from 2: [2, 3, 4]
    - Group starting from 6: [6, 7, 8]
4. All groups are successfully formed, so return `True`.

# My Solution
<a href = https://leetcode.com/problems/hand-of-straights/submissions/1279158305/>![image.png](https://assets.leetcode.com/users/images/b41f239c-f163-4ae7-80d9-ae305d420292_1717652540.8991861.png)</a>

# Code
```python
class Solution:
    def isNStraightHand(self, hand: List[int], groupSize: int) -> bool:
        # Step 1: Check if grouping is possible
        if len(hand) % groupSize != 0:
            return False
        
        # Step 2: Count the occurrences of each card
        count = Counter(hand)
        
        # Step 3: Sort the unique card values
        sorted_keys = sorted(count.keys())
        
        # Step 4: Form consecutive groups
        for key in sorted_keys:
            if count[key] > 0:  # If this card is still available
                start_count = count[key]
                # Check and form a group starting from `key`
                for i in range(key, key + groupSize):
                    if count[i] < start_count:
                        return False
                    count[i] -= start_count
        
        # Step 5: Return True if all groups are formed successfully
        return True
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
