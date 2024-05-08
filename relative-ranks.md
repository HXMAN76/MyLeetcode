# Algorithm
1. Initialize a variable `length` to the length of the score array.
2. Initialize a hashmap `score_idx` and save the original index of each athlete based on their `score`. The key is the `score` and the value is the original index.
3. Sort the `score` array in descending order. Then, the scores will be in order from highest to lowest. Since the highest score corresponds to the lowest place, this means the places will be in order.
4. Initialize a string array `rank` of size `length` for storing the result.
5. Assign `ranks` to athletes. We use the `score_idx` hashmap to retrieve the index in the result of the athlete with `score[i]`. For each rank `i`:
    - If `i is 0`, assign the athlete the "Gold Medal".
    - If `i is 1`, assign the athlete the "Silver Medal".
    - If `i is 2`, assign the athlete the "Bronze Medal".
    - Otherwise, set rank[score_to_index[score[i]]] = str(i + 1).
6. Return `rank`.
# Complexity
- Time complexity: $$O(\ n \ log(n)\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission
<a href = https://leetcode.com/problems/relative-ranks/submissions/1252308394/>![image.png](https://assets.leetcode.com/users/images/2e17fb43-5e57-4a25-9910-451b3a78fe38_1715140748.4963908.png)</a>

# Let's Code it down
```
class Solution:
    def findRelativeRanks(self, score: List[int]) -> List[str]:
        length = len(score)
        score_ = score.copy()

        score_idx = defaultdict(int)
        for i in range(length):
            score_idx[score_[i]] = i
        score_.sort(reverse = True)
        rank = [''] * length
        for i in range(length):
            if i == 0:
                rank[score_idx[score_[i]]] = 'Gold Medal'
            elif i == 1:
                rank[score_idx[score_[i]]] = 'Silver Medal'
            elif i == 2:
                rank[score_idx[score_[i]]] = 'Bronze Medal'
            else:
                rank[score_idx[score_[i]]] = str(i + 1)
        return rank        
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
