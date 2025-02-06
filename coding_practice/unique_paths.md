Location: https://leetcode.com/problems/unique-paths/description/?envType=study-plan-v2&envId=leetcode-75
# Question
There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., grid[m - 1][n - 1]). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to 2 * 109.
# Example

## Example 1:

Input: m = 3, n = 7

Output: 28

Explanation: 
| 1  | 1    | 1    | 1    | 1    | 1    | 1    |
| -------- | ------- |------- |------- |------- |------- |------- |
| 1 | 2    |3 | 4  | 5 | 6 | 7 | 
| 1    | 3   | 6 | 10 | 15  | 21 | 28 |

## Example 2:

Input: m = 3, n = 2

Output: 3

Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down

Constraints:
- 1 <= m, n <= 100

# My solution 
```python
class Solution(object):
    def uniquePaths(self, m, n):
        """
        :type m: int
        :type n: int
        :rtype: int
        """
        row = [0]*n
        ans = [row]*m
        ans[0] = [1] * n
        for i in range(m):
            ans[i][0] = 1
        for i in range(1, m):
            for j in range(1, n):
                ans[i][j] = ans[i-1][j]+ans[i][j-1]
        return ans[-1][-1]
        

```
