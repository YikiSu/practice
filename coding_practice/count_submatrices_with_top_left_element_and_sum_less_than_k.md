Location: https://leetcode.com/problems/count-submatrices-with-top-left-element-and-sum-less-than-k/description/
# Question
You are given a 0-indexed integer matrix grid and an integer k.

Return the number of submatrices that contain the top-left element of the grid, and have a sum less than or equal to k.

 
# Example

## Example 1:

Input: grid = [[7,6,3],[6,6,1]], k = 18

Output: 4

Explanation: There are only 4 submatrices, shown in the image above, that contain the top-left element of grid, and have a sum less than or equal to 18.

## Example 2:

Input: grid = [[7,2,9],[1,5,0],[2,6,6]], k = 20

Output: 6

Explanation: There are only 6 submatrices, shown in the image above, that contain the top-left element of grid, and have a sum less than or equal to 20.

## Constraints:
m == grid.length \
n == grid[i].length\
1 <= n, m <= 1000\
0 <= grid[i][j] <= 1000\
1 <= k <= 109
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def countSubmatrices(self, grid, k):
        """
        :type grid: List[List[int]]
        :type k: int
        :rtype: int
        """
        cnt = 0
        row, col = len(grid), len(grid[0])
        ans = [[0]*(col+1) for _ in range(row+1)]
        for r in range(1, row+1):
            for c in range(1, col+1):
                ans[r][c] = ans[r-1][c]+ans[r][c-1]+grid[r-1][c-1]-ans[r-1][c-1]
                if ans[r][c] <= k:
                    cnt +=1
        # print(ans)
        return cnt          

```
