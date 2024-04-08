# Approach
> First, we count the number of students who prefer circle sandwiches and the number of students who prefer square sandwiches.
Then, we iterate through the available sandwiches in the stack.
# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My Submission
 
![Screenshot 2024-04-08 111221.png](https://assets.leetcode.com/users/images/578ec5de-bd83-46b0-a261-a591b362722f_1712555033.9783711.png)

# Code
```
class Solution:
    def countStudents(self, students, sandwiches):
        counts = [0, 0]
        for i in students:
            counts[i] += 1

        remaining = len(sandwiches)
        for i in sandwiches:
            if counts[i] == 0:
                break
            if remaining == 0:
                break
            counts[i] -= 1
            remaining -= 1
        
        return remaining
```
