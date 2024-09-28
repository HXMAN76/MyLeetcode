# Intuition  
The problem requires the implementation of a circular deque (double-ended queue) that allows insertion and deletion of elements from both ends efficiently. My first thought was to use a doubly linked list, which allows easy manipulation of nodes from both the front and rear. This structure supports the required operations in constant time, making it suitable for the deque implementation.  

# Approach  
1. **Node Structure**: Define a `Node` class that contains the value, a reference to the next node, and a reference to the previous node.  
2. **Deque Structure**: Define a `MyCircularDeque` class that maintains pointers to the head (front) and rear (back) of the deque, as well as the current size and the maximum capacity.  
3. **Operations**:  
   - **Insert Front**: If the deque is not full, create a new node and update the head pointer. If the deque was empty, also update the rear pointer.  
   - **Insert Last**: Similar to insert front, but update the rear pointer instead.  
   - **Delete Front**: If the deque is not empty, update the head pointer to the next node. If it was the last element, also update the rear pointer to null.  
   - **Delete Last**: Update the rear pointer to the previous node, and handle the case where the deque becomes empty.  
   - **Get Front and Get Rear**: Simply return the values of the head and rear nodes, respectively, while checking if the deque is empty.  
   - **Check Empty and Full**: Provide methods to check if the deque is empty or full based on the size and capacity.  

# Complexity  
- Time complexity:   
  - All operations (insertions, deletions, and retrievals) are performed in constant time, i.e., $$O(1)$$.  
  
- Space complexity:   
  - The space complexity is $$O(n)$$, where $$n$$ is the number of elements in the deque, since we are storing the elements in nodes of the doubly linked list.

# Code
```java []
class Node {

    public int val;
    public Node next;
    public Node prev;

    public Node(int val, Node next, Node prev) {
        this.val = val;
        this.next = next;
        this.prev = prev;
    }
}

class MyCircularDeque {

    Node head;
    Node rear;
    int size;
    int capacity;

    public MyCircularDeque(int k) {
        size = 0;
        capacity = k;
    }

    public boolean insertFront(int value) {
        if (isFull()) return false;
        if (head == null) {
            // first element in list
            head = new Node(value, null, null);
            rear = head;
        } else {
            // add new head
            Node newHead = new Node(value, head, null);
            head.prev = newHead;
            head = newHead;
        }
        size++;
        return true;
    }

    public boolean insertLast(int value) {
        if (isFull()) return false;
        if (head == null) {
            // first element in list
            head = new Node(value, null, null);
            rear = head;
        } else {
            // add new element to end
            rear.next = new Node(value, null, rear);
            rear = rear.next;
        }
        size++;
        return true;
    }

    public boolean deleteFront() {
        if (isEmpty()) return false;
        if (size == 1) {
            head = null;
            rear = null;
        } else {
            head = head.next;
        }
        size--;
        return true;
    }

    public boolean deleteLast() {
        if (isEmpty()) return false;
        if (size == 1) {
            head = null;
            rear = null;
        } else {
            // update rear to the previous node
            rear = rear.prev;
        }
        size--;
        return true;
    }

    public int getFront() {
        if (isEmpty()) return -1;
        return head.val;
    }

    public int getRear() {
        if (isEmpty()) return -1;
        return rear.val;
    }

    public boolean isEmpty() {
        return size == 0;
    }

    public boolean isFull() {
        return size == capacity;
    }
}
```
