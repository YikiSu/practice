Location: https://leetcode.com/problems/sort-matrix-by-diagonals/description/?envType=daily-question&envId=2025-10-16
# Question
You are given an n x n square matrix of integers grid. Return the matrix such that:

- The diagonals in the bottom-left triangle (including the middle diagonal) are sorted in non-increasing order.
- The diagonals in the top-right triangle are sorted in non-decreasing order.

 
# Example

## Example 1:

Input: grid = [[1,7,3],[9,8,2],[4,5,6]]

Output: [[8,2,3],[9,6,7],[4,5,1]]

Explanation:

The diagonals with a black arrow (bottom-left triangle) should be sorted in non-increasing order:

[1, 8, 6] becomes [8, 6, 1].\
[9, 5] and [4] remain unchanged.\
The diagonals with a blue arrow (top-right triangle) should be sorted in non-decreasing order:

[7, 2] becomes [2, 7].\
[3] remains unchanged.

## Example 2:

Input: grid = [[0,1],[1,2]]

Output: [[2,1],[1,0]]

Explanation:

The diagonals with a black arrow must be non-increasing, so [0, 2] is changed to [2, 0]. The other diagonals are already in the correct order.

## Example 3:

Input: grid = [[1]]

Output: [[1]]

Explanation:

Diagonals with exactly one element are already in order, so no changes are needed.
 

## Constraints:

grid.length == grid[i].length == n\
1 <= n <= 10\
-105 <= grid[i][j] <= 105
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def sortMatrix(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: List[List[int]]
        """
        n = len(grid)
        for row in range(n):
            cells = []
            r = row
            c = 0
            while r<n and c<n:
                cells.append(grid[r][c])
                r += 1
                c += 1
            cells = sorted(cells, reverse=True)
            idx = 0
            r = row
            c = 0
            while r<n and c<n:
                grid[r][c] = cells[idx]
                idx += 1
                r += 1
                c += 1
        for col in range(1, n):
            cells = []
            r = 0
            c = col
            while r<n and c<n:
                cells.append(grid[r][c])
                r += 1
                c += 1
            cells = sorted(cells)
            idx = 0
            r = 0
            c = col
            while r<n and c<n:
                grid[r][c] = cells[idx]
                r += 1
                c += 1
                idx += 1
        return grid

```
