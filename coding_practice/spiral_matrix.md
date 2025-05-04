Location: https://leetcode.com/problems/spiral-matrix/description/
# Question
Given an m x n matrix, return all elements of the matrix in spiral order.

 
# Example

## Example 1:

Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]

Output: [1,2,3,6,9,8,7,4,5]

## Example 2:

Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]

Output: [1,2,3,4,8,12,11,10,9,5,6,7]

## Constraints:

m == matrix.length\
n == matrix[i].length\
1 <= m, n <= 10\
-100 <= matrix[i][j] <= 100
 

# My solution 
```python
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        ans = []
        r, c = 0, 0
        direction = [1,1]
        seen = set()
        size =  len(matrix[0])*len(matrix)
        m = len(matrix[0])
        n = len(matrix)
        while len(ans) < size:
            ans.append(matrix[r][c])
            seen.add((r,c))
            if direction == [1,1]:
                c += 1
                if (r,c) in seen or c == m:
                    c -= 1
                    r += 1
                    direction = [1, -1]
            elif direction == [1, -1]:
                r += 1
                if (r,c) in seen or r == n:
                    c -= 1
                    r -= 1
                    direction = [-1,-1]
            elif direction == [-1, -1]:
                c -= 1
                if (r,c) in seen or c < 0:
                    r -= 1
                    c += 1
                    direction = [-1, 1]
            else:
                r -= 1
                if (r,c) in seen or r < 0:
                    c += 1
                    r += 1
                    direction = [1, 1]
        return ans
```
