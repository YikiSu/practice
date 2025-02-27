Location: https://leetcode.com/problems/count-servers-that-communicate/description/
# Question
You are given a map of a server center, represented as a m * n integer matrix grid, where 1 means that on that cell there is a server and 0 means that it is no server. Two servers are said to communicate if they are on the same row or on the same column.

Return the number of servers that communicate with any other server. 
# Example

## Example 1:

Input: grid = [[1,0],[0,1]]

Output: 0

Explanation: No servers can communicate with others.

## Example 2:

Input: grid = [[1,0],[1,1]]

Output: 3

Explanation: All three servers can communicate with at least one other server.

## Example 3:

Input: grid = [[1,1,0,0],[0,0,1,0],[0,0,1,0],[0,0,0,1]]

Output: 4

Explanation: The two servers in the first row can communicate with each other. The two servers in the third column can communicate with each other. The server at right bottom corner can't communicate with any other server.
 

Constraints:

m == grid.length\
n == grid[i].length\
1 <= m <= 250\
1 <= n <= 250\
grid[i][j] == 0 or 1
 

# My solution (follows instructions on ChatGPT)
```python
class Solution(object):
    def countServers(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        row_cnt = [0]*len(grid)
        column_cnt = [0]*len(grid[0])
        for i in range(len(grid)):
            row_cnt[i] = sum(grid[i])
        for j in range(len(grid[0])):
            curr = 0
            for i in range(len(grid)):
                curr += grid[i][j]
            column_cnt[j] = curr
        ans = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j]==1 and (row_cnt[i]>1 or column_cnt[j]>1):
                    ans += 1
        return ans
        
```
