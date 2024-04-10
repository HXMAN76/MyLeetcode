# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
The goal is to reveal the deck in increasing order. We start by sorting the `deck` in increasing order, so we can work backward to the special order. We create an array `result` to store the cards in the special order.

We can use two pointers, one for `deck` and one for `result`, to add cards from the deck to the `result`.

On the first pass through the deck, we reveal every other card. We can fill cards into every other index in `result` so that the cards will be revealed in increasing order.

---


# Approach
<!-- Describe your approach to solving the problem. -->
The approach is through **Two Pointers**
1. Create a two variables one for the `deck` and another for `result`,Create a variable `skip` and initialise to False, sort the `deck` array.
2. Using while loop iterate the array `deck` and fill the cards to `result`, To decide to add card or skip the index we can use the `skip` variable.
3. While inserting elements in `result` the index updation for result may go `out of bound` due to multiple iterations so we divide it by the `length of deck`.

---


# Complexity
- Time complexity: $$O(n \ log \ n)$$
> Sorting the deck takes $$O(n \ log \ ⁡n)$$,
The loop to place cards at the correct index in `result` runs 
$$O(n \ log⁡ \ n)$$ times. Each pass through the `result` array takes $$O(n)$$, and with each pass, half as many indices still need to be filled.
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n) \ or \ O(n \ log \ n)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

---


# My Submission
![Screenshot 2024-04-10 110125.png](https://assets.leetcode.com/users/images/8062c313-c51e-4d3c-9180-6079653c3973_1712727296.219238.png)


---


# Let's Code it 
```
class Solution(object):
    def deckRevealedIncreasing(self, deck):
        """
        :type deck: List[int]
        :rtype: List[int]
        """
        N = len(deck)
        result  = [0] * N
        skip = False
        index_in_deck = 0
        index_in_result = 0

        deck.sort()

        while index_in_deck < N:
            #if there is a gap in result
            if result[index_in_result] == 0:
                #Add a card
                if not skip:
                    result[index_in_result] = deck[index_in_deck]
                    index_in_deck += 1
                #Make the skip to alternative
                skip = not skip
            index_in_result += 1
            index_in_result %= N
        
        return result
        
```
> Please Upvote me and have a good day.


