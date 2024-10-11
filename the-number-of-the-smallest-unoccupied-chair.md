# Intuition  
To solve the problem of determining which chair the target friend will sit in upon arrival, we need to simulate the seating process as friends arrive and leave. Each friend occupies a chair upon arrival and vacates it after their designated time. The key is to efficiently manage the availability of chairs and ensure that the target friend is seated in the smallest numbered chair possible.  

# Approach  
1. **Sort the Arrival Times**: First, we sort the list of friends based on their arrival times to process them in the correct order.  
2. **Use a Priority Queue**: We maintain a priority queue to track when chairs will become available again. This allows us to efficiently free up chairs when friends leave.  
3. **Use a TreeSet for Available Chairs**: We utilize a TreeSet to keep track of which chairs are available at any given time. This allows us to quickly retrieve the smallest available chair when a new friend arrives.  
4. **Simulate the Process**: As we iterate through the sorted list of friends:  
   - We free up any chairs that have become available by the time the current friend arrives.  
   - We assign the smallest available chair to the current friend or incrementally assign a new chair if none are available.  
   - If the current friend is the target friend, we return the chair number assigned to them.  

# Complexity  
- Time complexity: $$O(n \log n)$$, where $$n$$ is the number of friends. This accounts for sorting the arrival times and the operations on the priority queue and TreeSet.  
- Space complexity: $$O(n)$$, for storing the priority queue and TreeSet that keep track of the chairs and their availability.
---
<a href = https://leetcode.com/problems/the-number-of-the-smallest-unoccupied-chair/submissions/1418792340/>![image.png](https://assets.leetcode.com/users/images/76dfdfb6-dd1c-42a1-91a0-7b0ec44d59c8_1728634434.5788245.png)</a>


# Code
```java []
public class Solution {

    public int smallestChair(int[][] times, int targetFriend) {
        int targetArrival = times[targetFriend][0];
        Arrays.sort(times, (a, b) -> a[0] - b[0]);

        int nextChair = 0;
        PriorityQueue<int[]> leavingQueue = new PriorityQueue<>(
            (a, b) -> a[0] - b[0]
        );
        TreeSet<Integer> availableChairs = new TreeSet<>();

        for (int[] time : times) {
            int arrival = time[0];
            int leave = time[1];

            // Free up chairs based on current time
            while (
                !leavingQueue.isEmpty() && leavingQueue.peek()[0] <= arrival
            ) {
                availableChairs.add(leavingQueue.poll()[1]);
            }

            int currentChair;
            // Assign chair from available set or increment new chair
            if (!availableChairs.isEmpty()) {
                currentChair = availableChairs.first();
                availableChairs.remove(currentChair);
            } else {
                currentChair = nextChair++;
            }

            // Push current leave time and chair
            leavingQueue.offer(new int[] { leave, currentChair });

            // Check if it's the target friend
            if (arrival == targetArrival) return currentChair;
        }

        return 0;
    }
}
```
