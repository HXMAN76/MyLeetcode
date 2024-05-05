# Algorithm
>*It simply updates the value of the current node to the value of the next node, and then updates the next pointer to skip the next node.*
# Complexity
- Time complexity: $$O(1)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(1)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
# My submissions: 
<a href = https://leetcode.com/problems/delete-node-in-a-linked-list/submissions/1249843580/>![image.png](https://assets.leetcode.com/users/images/ba423e2f-5772-4435-b56f-5d654bcfcb6a_1714897128.164835.png)</a>
# Lets code it down
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
void deleteNode(struct ListNode* node) {
    node->val = node->next->val;
    node->next =  node->next->next;
}
```
# In Python

<a href = https://leetcode.com/problems/delete-node-in-a-linked-list/submissions/1249842356/>![Screenshot 2024-05-05 134458.png](https://assets.leetcode.com/users/images/b5b749a8-601d-4cde-bd4e-791e5b0e9ad9_1714897252.3458793.png)</a>

```
# Definition for singly-linked list.
# class ListNode:
    # def __init__(self, x):
        # self.val = x
        # self.next = None

class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val = node.next.val
        node.next = node.next.next    
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
