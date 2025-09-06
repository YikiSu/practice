Location: https://leetcode.com/problems/diagonal-traverse/description/?envType=daily-question&envId=2025-09-05
# Question
Given an m x n matrix mat, return an array of all the elements of the array in a diagonal order.

 
# Example

## Example 1:

Input: mat = [[1,2,3],[4,5,6],[7,8,9]]

Output: [1,2,4,7,5,3,6,8,9]

## Example 2:

Input: mat = [[1,2],[3,4]]

Output: [1,2,3,4]

## Constraints:

m == mat.length\
n == mat[i].length\
1 <= m, n <= 104\
1 <= m * n <= 104\
-105 <= mat[i][j] <= 105

# My solution 
```python
class Solution(object):
    def findDiagonalOrder(self, mat):
        """
        :type mat: List[List[int]]
        :rtype: List[int]
        """
        ans = []
        r, c = len(mat), len(mat[0])
        dire = 1
        for row in range(r):
            cur = [row, 0]
            pre = [mat[cur[0]][cur[1]]]
            while True:
                cur[0] -=1
                cur[1] += 1
                if cur[0] >= 0 and cur[0] < r and cur[1] >= 0 and cur[1] < c:
                    pre.append(mat[cur[0]][cur[1]])
                else:
                    ans += pre[::dire]
                    dire *= -1
                    break
        for col in range(1, c):
            cur = [r-1, col]
            pre = [mat[cur[0]][cur[1]]]
            while True:
                cur[0] -=1
                cur[1] += 1
                if cur[0] >= 0 and cur[0] < r and cur[1] >= 0 and cur[1] < c:
                    pre.append(mat[cur[0]][cur[1]])
                else:
                    ans += pre[::dire]
                    dire *= -1
                    break
        return ans
```
