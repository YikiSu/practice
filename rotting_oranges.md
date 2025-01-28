Location: https://leetcode.com/problems/rotting-oranges/description/?envType=study-plan-v2&envId=leetcode-75
# Question
You are given an m x n grid where each cell can have one of three values:

- 0 representing an empty cell,
- 1 representing a fresh orange, or
- 2 representing a rotten orange.

Every minute, any fresh orange that is 4-directionally adjacent to a rotten orange becomes rotten.

Return the minimum number of minutes that must elapse until no cell has a fresh orange. If this is impossible, return -1.

# Example
## Example 1:

Input: grid = [[2,1,1],[1,1,0],[0,1,1]]

Output: 4

## Example 2:

Input: grid = [[0,2]]

Output: 0

Explanation: Since there are already no fresh oranges at minute 0, the answer is just 0.

## Example 3:

Input: grid = [[2,1,1],[0,1,1],[1,0,1]]

Output: -1

Explanation: The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.

**Constraints**:

- m == grid.length
- n == grid[i].length
- 1 <= m, n <= 10
- grid[i][j] is 0, 1, or 2.
  
# My solution (follows instructions of others)
```python
class Solution(object):
    def orangesRotting(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        ans = 0
        fresh = set()
        rotten = deque()
        directions = [(0,1),(0,-1),(1,0),(-1,0)]
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == 1:
                    fresh.add((i,j))
                if grid[i][j] == 2:
                    rotten.append((i,j))
        # print(fresh)
        # print(rotten)
        while fresh and rotten:
            for ora in range(len(rotten)):
                i, j = rotten.popleft()
                # print(i)
                # print(j)
                for d in directions:
                    new_d = i + d[0], j + d[1]
                    if new_d in fresh:
                        fresh.remove(new_d)
                        rotten.append(new_d)
            ans += 1
        return -1 if fresh else ans
     
```
