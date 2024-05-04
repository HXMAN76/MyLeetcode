# Algorithm 
1. **Sort the array:** The function first sorts the array of people in ascending order. This is crucial for the algorithm to work efficiently. 
    ```
    people.sort()
    ```
2. **Initialize pointers:** Two pointers, `start` and `end`, are initialized at the beginning and end of the sorted array, respectively.
    ```
    start = 0
    end = len(people) - 1
    ```
3. **Iterate through the array:** A while loop is used to iterate through the array from both ends (`start` from the beginning and `end` from the end) until they meet or cross each other.
    ```
    while(start <= end):
        #the code here
    ```
4. **Check if two people can fit in a boat:** Within the loop, it checks if the weight of the person at index `start` and the person at index `end` is less than or equal to the given `limit`.
    ```
    if ( people[end] + people[start] <= limit ):
        # code here
    ```
5. **Move pointer:** Regardless of whether two people can fit in a boat or not, the pointer `end` is decremented in each iteration to consider the next person from the heavier end of the array.
    ```
    end -= 1
    ```
6. **Count res:** Increment the `res` variable in each iteration to keep track of the number of boats required.
    ```
    res += 1
    ```
# Complexity
- **Time complexity:** $$O(n\ *\ log(\ n\ ))$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- **Space complexity:** $$O(\ 1\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission
<a href = https://leetcode.com/problems/boats-to-save-people/submissions/1248742612/>![image.png](https://assets.leetcode.com/users/images/0ed104cd-25a2-44d3-987e-c162ae190372_1714797345.512432.png)</a>

# Let's Code it down
```
class Solution:
    def numRescueBoats(self, people: List[int], limit: int) -> int:
        people.sort()
        res = 0
        start = 0
        end = len(people) - 1
        while(start <= end):
            if ( people[end] + people[start] <= limit ):
                start += 1
            end -= 1
            res += 1
        return res       
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
