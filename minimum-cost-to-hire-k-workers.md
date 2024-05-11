# Algorithm
- Initialize variables `n` to store the size of the input arrays (quality and wage), `totalCost` to store the minimum total cost (initially set to the maximum possible value) and `currentTotalQuality`to keep track of the sum of qualities of the current set of workers.
- Create a array `wageToQualityRatio` to store the wage-to-quality ratio and the quality of each worker as pairs.
- Calculate the wage-to-quality ratio for each worker and store it in `wageToQualityRatio`.
- Sort `wageToQualityRatio` in ascending order based on the wage-to-quality ratio.
- Create a priority queue `highestQualityWorkers` (max heap) to store the workers with the highest qualities.
- Iterate through the sorted `wageToQualityRatio`:
    - Push the current worker's quality to `highestQualityWorkers`.
    - Update `currentTotalQuality` by adding the current worker's quality.
    - If the size of `highestQualityWorkers` exceeds `k`:
        - Remove the worker with the highest quality from `highestQualityWorkers`. Update `currentTotalQuality` by subtracting the removed worker's quality.
    - If the size of `highestQualityWorkers` is equal to `k`:
Calculate the total cost for the current set of workers by multiplying `currentTotalQuality` by the wage-to-quality ratio of the current worker.
    - Update `totalCost` if the calculated cost is smaller than the current minimum cost.
- After iterating through all workers, return `totalCost`, which holds the minimum total cost for hiring `k` workers.
- Return `totalCost`.
# Complexity
- Time complexity: $$O(n\ log\ n+n\ log\ k)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: $$O(n\  +\ k)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# My submission
<a href = https://leetcode.com/problems/minimum-cost-to-hire-k-workers/submissions/1254846510/>![image.png](https://assets.leetcode.com/users/images/b2336fb2-431d-44a1-a82e-6da0e6a4dd1d_1715398378.2021499.png)</a>

# Let's Code it down
```
class Solution:
    def mincostToHireWorkers(self, quality: List[int], wage: List[int], k: int) -> float:
        n = len(quality)
        total_cost = float("inf")
        current_total_quality = 0
        wage_to_quality_ratio = []

        # Calculate wage-to-quality ratio for each worker
        for i in range(n):
            wage_to_quality_ratio.append((wage[i] / quality[i], quality[i]))

        # Sort workers based on their wage-to-quality ratio
        wage_to_quality_ratio.sort(key=lambda x: x[0])

        # Use a heap to keep track of the highest quality workers
        highest_quality_workers = []

        # Iterate through workers
        for i in range(n):
            heapq.heappush(highest_quality_workers, -wage_to_quality_ratio[i][1])
            current_total_quality += wage_to_quality_ratio[i][1]

            # If we have more than k workers, 
            # remove the one with the highest quality
            if len(highest_quality_workers) > k:
                current_total_quality += heapq.heappop(highest_quality_workers)

            # If we have exactly k workers, 
            # calculate the total cost and update if it's the minimum
            if len(highest_quality_workers) == k:
                total_cost = min(
                    total_cost, current_total_quality * wage_to_quality_ratio[i][0]
                )

        return total_cost
```
>***Have a nice day... <3***

![img](https://i.imgflip.com/415oth.gif)
