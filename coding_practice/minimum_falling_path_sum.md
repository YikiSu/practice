Location: https://leetcode.com/problems/minimum-falling-path-sum/description/
# Question
Given an n x n array of integers matrix, return the minimum sum of any falling path through matrix.

A falling path starts at any element in the first row and chooses the element in the next row that is either directly below or diagonally left/right. Specifically, the next element from position (row, col) will be (row + 1, col - 1), (row + 1, col), or (row + 1, col + 1).
# Example

## Example 1:

Input: matrix = [[2,1,3],[6,5,4],[7,8,9]]

Output: 13

Explanation: There are two falling paths with a minimum sum as shown.

## Example 2:

Input: matrix = [[-19,57],[-40,-5]]

Output: -59

Explanation: The falling path with a minimum sum is shown.

## Constraints:

n == matrix.length == matrix[i].length\
1 <= n <= 100\
-100 <= matrix[i][j] <= 100
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def minFallingPathSum(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: int
        """
        dp = [[0]*len(matrix) for _ in range(len(matrix))]
        dp[-1] = matrix[-1][:]
        # print(dp)
        for i in range(len(matrix)-2, -1, -1):
            for j in range(len(matrix)):
                dp[i][j] = matrix[i][j] + min(
                    dp[i+1][j], 
                    dp[i+1][j-1] if j > 0 else float('inf'),
                    dp[i+1][j+1] if j < len(matrix) - 1 else float('inf')
                )
        # print(dp)
        return min(dp[0])
```
