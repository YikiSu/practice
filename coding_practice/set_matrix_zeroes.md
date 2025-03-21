Location: https://leetcode.com/problems/set-matrix-zeroes/description/?envType=problem-list-v2&envId=hash-table
# Question
Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.

You must do it in place.

 
# Example

## Example 1:

Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]\
Output: [[1,0,1],[0,0,0],[1,0,1]]

## Example 2:

Input: matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]\
Output: [[0,0,0,0],[0,4,5,0],[0,3,1,0]]

Constraints:

m == matrix.length\
n == matrix[0].length\
1 <= m, n <= 200\
-231 <= matrix[i][j] <= 231 - 1
 

# My solution 
```python
import collections
class Solution(object):
    def setZeroes(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: None Do not return anything, modify matrix in-place instead.
        """
        # print(list(range(4)))
        check_ = collections.defaultdict(set)
        for row in range(len(matrix)):
            for col in range(len(matrix[0])):
                if matrix[row][col] == 0:
                    check_[row] = set(range(len(matrix[0])))
                    for i in range(len(matrix)):
                        if i not in check_.keys():
                            check_[i] = set([col])
                        else:
                            check_[i].add(col)
        for row, cols in check_.items():
            for col in cols:
                matrix[row][col] = 0


```
