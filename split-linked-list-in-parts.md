
# Intuition
The problem requires us to split a linked list into `k` consecutive parts. The key is to ensure that each part is as evenly sized as possible. If the total number of nodes in the linked list is not divisible by `k`, some parts will have one extra node. The main challenge is to traverse the list while keeping track of the parts and their sizes.

# Approach
1. **Calculate the Size of the Linked List**: First, we traverse the linked list to determine its total size. This helps us understand how many nodes we need to distribute among the `k` parts.

2. **Determine Part Sizes**: 
   - Calculate the minimum size of each part as `size / k`.
   - Determine how many parts will have an extra node by calculating `size % k`.

3. **Split the List**: 
   - Initialize a pointer to traverse the list and another pointer to keep track of the previous node.
   - For each part, assign the appropriate number of nodes based on the calculated sizes. 
   - After assigning nodes to a part, sever the connection to the rest of the list by setting the `next` pointer of the last node in the current part to `null`.

4. **Store the Parts**: Each part is stored in an array which is returned at the end.

# Complexity
- Time complexity: $$O(n)$$, where `n` is the total number of nodes in the linked list. We traverse the list a couple of times, but each traversal is linear.
- Space complexity: $$O(k)$$, as we are using an array of size `k` to store the heads of the resulting parts.
---
<a href = https://leetcode.com/problems/split-linked-list-in-parts/submissions/1382635734/>![image.png](https://assets.leetcode.com/users/images/c9445e12-cb66-4a24-ac9c-ef90bc4dd775_1725761726.8820157.png)</a>

# Code
```java []
class Solution {

    public ListNode[] splitListToParts(ListNode head, int k) {
        ListNode[] ans = new ListNode[k];

        // get total size of linked list
        int size = 0;
        ListNode current = head;
        while (current != null) {
            size++;
            current = current.next;
        }

        // minimum size for the k parts
        int splitSize = size / k;

        // Remaining nodes after splitting the k parts evenly.
        // These will be distributed to the first (size % k) nodes
        int numRemainingParts = size % k;

        current = head;
        ListNode prev = current;
        for (int i = 0; i < k; i++) {
            // create the i-th part
            ListNode newPart = current;
            // calculate size of i-th part
            int currentSize = splitSize;
            if (numRemainingParts > 0) {
                numRemainingParts--;
                currentSize++;
            }

            // traverse to end of new part
            int j = 0;
            while (j < currentSize) {
                prev = current;
                current = current.next;
                j++;
            }
            // cut off the rest of linked list
            if (prev != null) {
                prev.next = null;
            }

            ans[i] = newPart;
        }

        return ans;
    }
}
```
