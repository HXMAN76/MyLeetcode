# My Submission
![Screenshot 2024-04-09 092145.png](https://assets.leetcode.com/users/images/cd7a57a1-627c-4651-8e56-da5d20c46490_1712635612.7267728.png)

---


# Approach
<!-- Describe your approach to solving the problem. -->
1. Initialize `time` to 0.

2. Iterate through the `tickets` array:
3.  **If the current index ` i ` is less than or equal to ` k `(i <= k):**
Increment time by the minimum of `tickets[k]` and `tickets[i]`
**Else (if the current index `i` is greater than `k`):**
Increment time by the minimum of `tickets[k] - 1` and `tickets[i]`
Return `time` (the total time required for the person at index k to buy all their tickets).
# Complexity
- Time complexity: $$O(n)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution(object):
    def timeRequiredToBuy(self, tickets, k):
        """
        :type tickets: List[int]
        :type k: int
        :rtype: int
        """
        time = 0
        for i in range(len(tickets)):
            if i <= k:
                time += min(tickets[i],tickets[k])
            else:
                time += min(tickets[k] - 1,tickets[i])
        return time
```

---


# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Until the `k-th` person gets required tickets we should append time also we can iterate through the list and decrement the list by one until `k-th` element becomes zero.
# Approach
1. Create a varible to store `time`.
2. Check for a condition that if `k-th` element is equal to 1 if equal return `k+1` because that is the time taken for a `k-th` person to buy 1 ticket.
3. use a `while` loop and iterate till `k == 0` and use a `for` loop to decrement the list and increment `time`.
4. return `time`.

# Complexity
- Time complexity: $$O(n * m)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Another way
```
class Solution:
    def timeRequiredToBuy(self, tickets, k):
        n = len(tickets)
        time = 0

        # If person k only needs one ticket, return the time to buy it
        if tickets[k] == 1:
            return k + 1

        # Continue buying tickets until person k buys all their tickets
        while tickets[k] > 0:
            for i in range(n):
                # Buy a ticket at index 'i' if available
                if tickets[i] != 0:
                    tickets[i] -= 1
                    time += 1

                # If person k bought all their tickets, return the time
                if tickets[k] == 0:
                    return time

        return time
      
```

---

