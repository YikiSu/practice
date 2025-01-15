Location: https://leetcode.com/problems/equal-row-and-column-pairs/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Given a 0-indexed n x n integer matrix grid, return the number of pairs (ri, cj) such that row ri and column cj are equal.

A row and column pair is considered equal if they contain the same elements in the same order (i.e., an equal array).

 
# Example

## Example 1:

Input: grid = [[3,2,1],[1,7,6],[2,7,7]]

Output: 1

Explanation: There is 1 equal row and column pair:
- (Row 2, Column 1): [2,7,7]

## Example 2:

Input:  grid = [[3,1,2,2],[1,4,4,5],[2,4,2,2],[2,4,2,2]]

Output: 3

Explanation: There are 3 equal row and column pairs:
- (Row 0, Column 0): [3,1,2,2]
- (Row 2, Column 2): [2,4,2,2]
- (Row 3, Column 2): [2,4,2,2]
  

Constraints:

- n == grid.length == grid[i].length
- 1 <= n <= 200
- 1 <= grid[i][j] <= 105
 

# My solution (followed solutions of others)
```python
import collections
class Solution(object):
    def equalPairs(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        columns = []
        cnt = 0
        for i in range(len(grid)):
            columns.append([x[i] for x in grid])
        gc = collections.Counter(map(tuple, grid))
        cc = collections.Counter(map(tuple, columns))
        return sum(gc[t]*cc[t] for t in gc)

        
```
