Location: https://leetcode.com/problems/unique-paths-ii/description/
# Question
You are given an m x n integer array grid. There is a robot initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

An obstacle and space are marked as 1 or 0 respectively in grid. A path that the robot takes cannot include any square that is an obstacle.

Return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The testcases are generated so that the answer will be less than or equal to 2 * 109.
 
# Example

## Example 1:

Input: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]

Output: 2

Explanation: There is one obstacle in the middle of the 3x3 grid above.\
There are two ways to reach the bottom-right corner:\
1. Right -> Right -> Down -> Down\
2. Down -> Down -> Right -> Right

## Example 2:

Input: obstacleGrid = [[0,1],[0,0]]

Output: 1
 

Constraints:

m == obstacleGrid.length\
n == obstacleGrid[i].length\
1 <= m, n <= 100\
obstacleGrid[i][j] is 0 or 1.
 

# My solution 
```python
class Solution(object):
    def uniquePathsWithObstacles(self, obstacleGrid):
        """
        :type obstacleGrid: List[List[int]]
        :rtype: int
        """
        ans = [[0] * len(obstacleGrid[0]) for _ in range(len(obstacleGrid))]
        for j in range(len(obstacleGrid[0])):
            if j == 0 and obstacleGrid[0][j] != 1:
                ans[0][j] = 1
            elif j > 0 and obstacleGrid[0][j] != 1 and ans[0][j-1] == 1:
                ans[0][j] = 1
            else:
                ans[0][j] = 0
        for i in range(len(obstacleGrid)):
            if i == 0 and obstacleGrid[i][0] != 1:
                ans[i][0] = 1
            elif i > 0 and obstacleGrid[i][0] != 1 and ans[i-1][0] == 1:
                ans[i][0] = 1
            else:
                ans[i][0] = 0
        for i in range(1, len(obstacleGrid)):
            for j in range(1, len(obstacleGrid[0])):
                if obstacleGrid[i][j] != 1:
                    ans[i][j] = ans[i][j-1]+ans[i-1][j]
                else:
                    ans[i][j] = 0
        return ans[-1][-1]
        
```
