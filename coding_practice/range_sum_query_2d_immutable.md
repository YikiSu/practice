Location: https://leetcode.com/problems/range-sum-query-2d-immutable/description/?envType=problem-list-v2&envId=prefix-sum
# Question
Given a 2D matrix matrix, handle multiple queries of the following type:

Calculate the sum of the elements of matrix inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).
Implement the NumMatrix class:

NumMatrix(int[][] matrix) Initializes the object with the integer matrix matrix.
int sumRegion(int row1, int col1, int row2, int col2) Returns the sum of the elements of matrix inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).
You must design an algorithm where sumRegion works on O(1) time complexity.
# Example

## Example 1:

Input\
["NumMatrix", "sumRegion", "sumRegion", "sumRegion"]\
[[[[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]], [2, 1, 4, 3], [1, 1, 2, 2], [1, 2, 2, 4]]

Output\
[null, 8, 11, 12]

Explanation\
NumMatrix numMatrix = new NumMatrix([[3, 0, 1, 4, 2], [5, 6, 3, 2, 1], [1, 2, 0, 1, 5], [4, 1, 0, 1, 7], [1, 0, 3, 0, 5]]);\
numMatrix.sumRegion(2, 1, 4, 3); // return 8 (i.e sum of the red rectangle)\
numMatrix.sumRegion(1, 1, 2, 2); // return 11 (i.e sum of the green rectangle)\
numMatrix.sumRegion(1, 2, 2, 4); // return 12 (i.e sum of the blue rectangle)

## Constraints:

m == matrix.length\
n == matrix[i].length\
1 <= m, n <= 200\
-104 <= matrix[i][j] <= 104\
0 <= row1 <= row2 < m\
0 <= col1 <= col2 < n\
At most 104 calls will be made to sumRegion.
 

# My solution 
```python
class NumMatrix(object):

    def __init__(self, matrix):
        """
        :type matrix: List[List[int]]
        """
        self.dp = [[0]*len(matrix[0]) for _ in range(len(matrix))]
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if i == 0:
                    self.dp[i][j] = matrix[i][j]
                else:
                    self.dp[i][j] = self.dp[i-1][j] + matrix[i][j]
        # print(self.dp)

    def sumRegion(self, row1, col1, row2, col2):
        """
        :type row1: int
        :type col1: int
        :type row2: int
        :type col2: int
        :rtype: int
        """
        if row1 != 0:
            return sum(self.dp[row2][col1:col2+1]) - sum(self.dp[row1-1][col1:col2+1])
        else:
            return sum(self.dp[row2][col1:col2+1]) 



# Your NumMatrix object will be instantiated and called as such:
# obj = NumMatrix(matrix)
# param_1 = obj.sumRegion(row1,col1,row2,col2)
```
