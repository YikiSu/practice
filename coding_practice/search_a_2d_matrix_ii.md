Location: https://leetcode.com/problems/search-a-2d-matrix-ii/description/
# Question
Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:

- Integers in each row are sorted in ascending from left to right.
- Integers in each column are sorted in ascending from top to bottom.

 
# Example

## Example 1:

Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5

Output: true

## Example 2:

Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 20

Output: false

## Constraints:

m == matrix.length\
n == matrix[i].length\
1 <= n, m <= 300\
-109 <= matrix[i][j] <= 109\
All the integers in each row are sorted in ascending order.\
All the integers in each column are sorted in ascending order.\
-109 <= target <= 109
 

# My solution 
```python
class Solution(object):
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        col = len(matrix[0])-1
        row = 0
        l, r = 0, col
        while row < len(matrix):
            while l<=r and matrix[row][l] <= target and matrix[row][r] >= target:
                mid = (l+r)//2
                if matrix[row][mid] == target:
                    return True
                elif matrix[row][mid] > target:
                    r = mid-1
                else:
                    l = mid + 1
            row += 1
            l, r = 0, col
        return False
```
