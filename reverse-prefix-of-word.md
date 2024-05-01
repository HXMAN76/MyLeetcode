# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission
> ***Click to see my submission...***

<a href = https://leetcode.com/problems/reverse-prefix-of-word/submissions/1246188541/?envType=daily-question&envId=2024-05-01>

![image.png](https://assets.leetcode.com/users/images/abb3f810-c2b4-4fab-a934-79637d5228ae_1714535203.3220408.png)
</a>


# Lets Code it down
```
class Solution:
    def reversePrefix(self, word: str, ch: str) -> str:
        if ch in word: #to ensure that 'ch' is in word
            res = "" #result storing variable
            idx = word.index(ch) #find the index
            if idx == 0: #that is if ch in start of the word
                return word
            res = word[idx::-1]
            if len(word) == len(res): #if whole word is reversed
                return res
            temp = "" #to capture remaining words
            temp = word[idx+1:]              
            return res+temp
        return word # returns the same word if ch is not present    
```
# Advanced method
```
class Solution:
    def reversePrefix(self, word: str, ch: str) -> str:
        x=0
        for i in range(len(word)):
            if word[x]==ch:
                return word[x::-1]+word[x+1:]
            x+=1
        return word
```
