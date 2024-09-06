
# Linked List Modification

## Intuition
The goal is to modify a given singly-linked list by removing nodes whose values are present in a given array. The first step is to identify the maximum value in the array to create a frequency array that helps in efficiently checking if a node's value should be retained or removed.

## Approach
1. **Find Maximum Value**: Iterate through the `nums` array to determine the maximum value. This helps in defining the size of the frequency array.
2. **Create Frequency Array**: Initialize a boolean array `freq` of size `max + 1`. For each number in `nums`, set the corresponding index in `freq` to `true`. This marks the numbers that should be removed.
3. **Traverse the Linked List**: Create a temporary node to build the modified linked list. Iterate through the original linked list:
   - If the current node's value is out of bounds (greater than or equal to `freq.length`) or not present in `freq`, add it to the new list.
   - Move to the next node.
4. **Finalize the New List**: Set the `next` pointer of the last node in the new list to `null` to terminate it properly.

## Complexity
- **Time complexity**: $$O(n + m)$$, where `n` is the number of nodes in the linked list and `m` is the length of the `nums` array. We traverse both the array and the linked list once.
- **Space complexity**: $$O(m)$$, where `m` is the length of the `nums` array, for the frequency array used to track which values to remove.
---
<a href = https://leetcode.com/problems/delete-nodes-from-linked-list-present-in-array/submissions/1381217271/>![image.png](https://assets.leetcode.com/users/images/cffedfeb-a0cd-46b6-8a4c-e4e251e5ec2b_1725637933.4811437.png)</a>
# Code
```java []
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode modifiedList(int[] nums, ListNode head) {
        int max = -1;
        for(int num : nums ){
            max = num > max ? num : max;
        }
        boolean[] freq = new boolean[max+1];

        for(int num : nums) freq[num] = true;

        ListNode temp = new ListNode();
        ListNode current = temp;

        while(head != null){
            if( head.val >= freq.length || freq[head.val] == false){
                current.next = head;
                current = current.next;
            }
            head = head.next;
        }

        current.next = null;
        return temp.next;
    }
}
```
