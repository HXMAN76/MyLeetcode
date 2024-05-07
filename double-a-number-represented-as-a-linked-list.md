# Algorithm 
`doubleIt(head)` function:
1. Call the `reverse_list(head)` helper function to reverse the input linked list and store it in a variable`reverse`.
2. Initialize two pointers, `current` and `prev`, to keep track of the current node and the previous node, respectively. Also, initialize a `carry` variable to 0.
3. Traverse the reversed linked list:
    - For each node in the reversed list:
        -  Calculate the new value for the `current node` by doubling the current value and adding the `carry`.
        - Update the current node's value with the new value `modulo 10`.
        - Update the `carry` variable based on the new value (1 if the new value is greater than 9, 0 otherwise).
        - Move the `previous` and `current` pointers to the next nodes.
        - If there's a non-zero carry left after the loop, create a new node with the `carry` value and attach it to the end of the list.
        - Reverse the list back to its original order: Call the `reverse_list(reversedList)` function to reverse the list back to its original order and store the result in `res`.
4. Return the result list.

`reverse_list(node)`function:

1. Initialize three pointers `previous` (initially NULL), `current `(initially node), and `next_node` (to temporarily store the next node).
2. Traverse the list and reverse the links:
    - While the `current` pointer is not `NULL`:
        - Store the next node in `next_node`.
        - Reverse the link by setting `current->next` to `previous`.
        - Move the `previous` and `current` pointers to the next nodes.
        - After the loop, `previous` will be the new head of the reversed list.
3. return the `previous`.

# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ 1\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My Submission
<a href = https://leetcode.com/problems/double-a-number-represented-as-a-linked-list/submissions/1251443596/>![image.png](https://assets.leetcode.com/users/images/570a448f-089a-4cea-b631-66eba37cd8b9_1715057358.4964502.png)</a>

# Code
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverse_list(self, node: ListNode) -> ListNode:
        previous, current = None, node
        # Traverse the original linked list
        while current:
            # Store the next node
            next_node = current.next
            # Reverse the link
            current.next = previous
            # Move to the next nodes
            previous, current = current, next_node
        # Previous becomes the new head of the reversed list
        return previous

    def doubleIt(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # Reverse the linked list
        reverse = self.reverse_list(head)
        # Initialize variables to track carry and previous node
        carry = 0
        current,previous = reverse, None

        # Traverse the reversed linked list
        while current:
            # Calculate the new value for the current node
            val = current.val * 2 + carry
            # Update the current node's value
            current.val = val % 10
            # Update carry for the next iteration
            if val > 9:
                carry = 1
            else:
                carry = 0
            # Move to the next node
            prev, current = current,current.next
        # If there's a carry after the loop, add an extra node
        if carry:
            prev.next = ListNode(carry)
        # Reverse the list again to get the original order
        res = self.reverse_list(reverse)

        return res
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
