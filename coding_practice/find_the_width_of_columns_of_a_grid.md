Location: https://leetcode.com/problems/find-the-width-of-columns-of-a-grid/description/
# Question
You are given a 0-indexed m x n integer matrix grid. The width of a column is the maximum length of its integers.

For example, if grid = [[-10], [3], [12]], the width of the only column is 3 since -10 is of length 3.

Return an integer array ans of size n where ans[i] is the width of the ith column.

The length of an integer x with len digits is equal to len if x is non-negative, and len + 1 otherwise.
 
# Example

## Example 1:

Input: grid = [[1],[22],[333]]

Output: [3]

Explanation: In the 0th column, 333 is of length 3.

## Example 2:

Input: grid = [[-15,1,3],[15,7,12],[5,6,-2]]

Output: [3,1,2]

Explanation: \
In the 0th column, only -15 is of length 3.\
In the 1st column, all integers are of length 1. \
In the 2nd column, both 12 and -2 are of length 2.

## Constraints:

m == grid.length\
n == grid[i].length\
1 <= m, n <= 100 \
-109 <= grid[r][c] <= 109
 

# My solution 
```python
class Solution(object):
    def findColumnWidth(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: List[int]
        """
        col = [0] * len(grid[0])
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if len(str(grid[i][j])) > col[j]:
                    col[j] = len(str(grid[i][j]))
        return col
```
