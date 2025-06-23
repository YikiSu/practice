Location: https://leetcode.com/problems/search-a-2d-matrix/description/
# Question
You are given an m x n integer matrix matrix with the following two properties:

- Each row is sorted in non-decreasing order.
- The first integer of each row is greater than the last integer of the previous row.

Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

 
# Example

## Example 1:

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3

Output: true

## Example 2:

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13

Output: false

## Constraints:

m == matrix.length\
n == matrix[i].length\
1 <= m, n <= 100\
-104 <= matrix[i][j], target <= 104
 

# My solution 
```python
class Solution(object):
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        row = 0
        col = len(matrix[0])-1
        # print(matrix[0][col])
        while row < len(matrix):
            if target <= matrix[row][col] and target >= matrix[row][0]:
                l, r = 0, col
                while l <= r:
                    mid = (r+l)//2
                    if matrix[row][mid] == target:
                        return True
                    elif matrix[row][mid] > target:
                        r = mid-1
                    else:
                        l = mid+1
                return False
            row += 1
        return False
```
