
# Intuition
The goal of this problem is to insert the greatest common divisor (GCD) of each pair of consecutive nodes in a linked list. My first thought was to iterate through the list while keeping track of the current node and the next node. For each pair, I would calculate the GCD and create a new node for it, linking it between the two original nodes.

# Approach
1. **Base Case**: If the list has only one node, return the head since no GCD can be inserted.
2. **Iteration**: Use two pointers, `node1` and `node2`, to traverse the list. `node1` starts at the head, and `node2` starts at the second node.
3. **GCD Calculation**: For each pair of nodes, calculate the GCD of their values.
4. **Node Insertion**: Create a new node with the GCD value and insert it between `node1` and `node2`.
5. **Advance Pointers**: Move `node1` to `node2` and `node2` to the next node.
6. **Continue Until End**: Repeat until `node2` reaches the end of the list.

# Complexity
- Time complexity: $$O(n)$$, where $$n$$ is the number of nodes in the linked list, as we traverse the list once.
- Space complexity: $$O(n)$$ in the worst case, as we create a new node for each GCD calculated, resulting in additional space used for the new nodes.
---
<a href = https://leetcode.com/problems/insert-greatest-common-divisors-in-linked-list/submissions/1385384733/>![image.png](https://assets.leetcode.com/users/images/d25a0202-113f-49e6-9579-05537a755fc0_1725974049.6375022.png)</a>

# Code
```java []
class Solution {
    public ListNode insertGreatestCommonDivisors(ListNode head) {
        if (head.next == null) return head;
        
        ListNode node1 = head;
        ListNode node2 = head.next;

        while (node2 != null){
            int val = gcd(node1.val, node2.val);
            ListNode gcdnode = new ListNode(val);
            
            node1.next = gcdnode;
            gcdnode.next = node2;

            node1 = node2;
            node2 = node2.next;
        }
        return head;
    }
    private int gcd(int num1, int num2){
        while (num2 != 0){
            int temp = num2;
            num2 = num1 % num2;
            num1 = temp;
        }
        return num1;
    }
}
```
---
```java []
class Solution {
    public int gcd(int a, int b) {  
        while (b != 0) {  
            int temp = b;  
            b = a % b;  
            a = temp;  
        }  
        return a;  
    }  

    public ListNode insertGreatestCommonDivisors(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        ListNode current = head;
        while (current.next != null) {
            int gcdValue = gcd(current.val, current.next.val);
            ListNode newNode = new ListNode(gcdValue);
            newNode.next = current.next;
            current.next = newNode;
            current = current.next.next;
        }
        return head;
    }
}
```
