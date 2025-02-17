Location: https://leetcode.com/problems/maximum-amount-of-money-robot-can-earn/description/
# Question
You are given an m x n grid. A robot starts at the top-left corner of the grid (0, 0) and wants to reach the bottom-right corner (m - 1, n - 1). The robot can move either right or down at any point in time.

The grid contains a value coins[i][j] in each cell:

- If coins[i][j] >= 0, the robot gains that many coins.
- If coins[i][j] < 0, the robot encounters a robber, and the robber steals the absolute value of coins[i][j] coins.
</br>The robot has a special ability to neutralize robbers in at most 2 cells on its path, preventing them from stealing coins in those cells.

Note: The robot's total coins can be negative.

Return the maximum profit the robot can gain on the route.

 
# Example

## Example 1:
Input: coins = [[0,1,-1],[1,-2,3],[2,-3,4]]

Output: 8

Explanation:

An optimal path for maximum coins is:

Start at (0, 0) with 0 coins (total coins = 0).\
Move to (0, 1), gaining 1 coin (total coins = 0 + 1 = 1).\
Move to (1, 1), where there's a robber stealing 2 coins. The robot uses one neutralization here, avoiding the robbery (total coins = 1).\
Move to (1, 2), gaining 3 coins (total coins = 1 + 3 = 4).\
Move to (2, 2), gaining 4 coins (total coins = 4 + 4 = 8).

## Example 2:

Input: coins = [[10,10,10],[10,10,10]]

Output: 40

Explanation:

An optimal path for maximum coins is:

Start at (0, 0) with 10 coins (total coins = 10).\
Move to (0, 1), gaining 10 coins (total coins = 10 + 10 = 20).\
Move to (0, 2), gaining another 10 coins (total coins = 20 + 10 = 30).\
Move to (1, 2), gaining the final 10 coins (total coins = 30 + 10 = 40).
 

Constraints:

m == coins.length\
n == coins[i].length\
1 <= m, n <= 500\
-1000 <= coins[i][j] <= 1000
 

# My solution (follows instructions on solutions)
```python
import numpy as np
class Solution(object):
    def maximumAmount(self, coins):
        """
        :type coins: List[List[int]]
        :rtype: int
        """
        m, n = len(coins), len(coins[0])
        ans = [[[-np.inf]*3 for _ in range(n)] for _ in range(m)]
        for i in range(3):
            ans[0][0][i] = 0 if coins[0][0] < 0 and i > 0 else coins[0][0]
        for i in range(m):
            for j in range(n):
                for k in range(3):
                    if i == 0 and j == 0:
                        continue
                    best_from_top = ans[i-1][j][k] if i > 0 else -np.inf
                    best_from_left = ans[i][j-1][k] if j > 0 else -np.inf

                    if coins[i][j] >= 0:
                        ans[i][j][k] = max(best_from_top, best_from_left) + coins[i][j]
                    else:
                        best_without_neutralizing = max(best_from_top, best_from_left) + coins[i][j]
                        best_with_neutralizing = -np.inf
                        if k > 0:
                            best_from_top_k = ans[i-1][j][k-1] if i > 0 else -np.inf
                            best_from_left_k = ans[i][j-1][k-1] if j > 0 else -np.inf
                            best_with_neutralizing = max(best_from_top_k, best_from_left_k)

                        ans[i][j][k] = max(best_without_neutralizing, best_with_neutralizing)
                        
        return max(ans[-1][-1])
```
