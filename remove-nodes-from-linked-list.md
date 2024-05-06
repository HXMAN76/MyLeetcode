# Algorithm
 - This approach involves using a stack to keep track of the nodes in the linked list. While traversing the linked list, nodes are pushed onto the stack. 
 - If a node with a greater value is found, nodes are popped from the stack until finding a node with a greater value or until the stack becomes empty. 
- Then, the current node is connected to the top of the stack.

**Detailed Steps:**
1. Initialize an empty stack and start traversing the linked list from the head.
2. While traversing, push each node onto the stack.
3. For each node, compare its value with the value on top of the stack.
4. If the value of the current node is greater than the value on top of the stack, pop nodes from the stack until finding a node with a greater value or until the stack becomes empty.
5. Connect the current node to the top of the stack.
6. Finally, construct the modified linked list from the stack.

---

# Complexity
- Time complexity: $$O(\ n\ )$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(\ n\ )$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My submission
<a href = https://leetcode.com/problems/remove-nodes-from-linked-list/submissions/1250582230/>![image.png](https://assets.leetcode.com/users/images/dcf3c7a3-6ac8-4480-98ef-ac14f0e12302_1714973919.1584594.png)</a>

---


# Lets Code it down
```
class Solution:
    def removeNodes(self, head: Optional[ListNode]) -> Optional[ListNode]:
        stack = []
        current = head
        
        while current:
            while stack and stack[-1].val < current.val:
                stack.pop()
            
            stack.append(current)
            current = current.next
        
        dummy = ListNode(0)
        prev = dummy
        
        for node in stack:
            prev.next = node
            prev = prev.next
        
        prev.next = None
        
        return dummy.next
```
