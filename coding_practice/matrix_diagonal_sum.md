Location: https://leetcode.com/problems/matrix-diagonal-sum/description/
# Question
Given a square matrix mat, return the sum of the matrix diagonals.

Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal.

 
# Example

## Example 1:

Input: 
mat = \
[[1,2,3],\
[4,5,6],\
[7,8,9]]

Output: 25

Explanation: Diagonals sum: 1 + 5 + 9 + 3 + 7 = 25\
Notice that element mat[1][1] = 5 is counted only once.

## Example 2:

Input: mat = \
[[1,1,1,1],\
[1,1,1,1],\
[1,1,1,1],\
[1,1,1,1]]

Output: 8

## Example 3:

Input: mat = [[5]]

Output: 5

## Constraints:

n == mat.length == mat[i].length\
1 <= n <= 100\
1 <= mat[i][j] <= 100
 

# My solution 
```python
class Solution(object):
    def diagonalSum(self, mat):
        """
        :type mat: List[List[int]]
        :rtype: int
        """
        ans = 0
        n = len(mat)
        if n%2 == 0:
            i, j = 0, 0
            while i != n and j != n:
                # print(mat[i][j])
                ans += mat[i][j]
                i += 1
                j += 1
            i, j = 0, n-1
            while i != n and j >= 0:
                ans += mat[i][j]
                i += 1
                j -= 1
        if n%2 != 0:
            i, j = 0, 0
            while i != n and j != n:
                ans += mat[i][j]
                i += 1
                j += 1
            i, j = 0, n-1
            while i != n and j >= 0:
                if i != n//2 and j!=n//2:
                    # print(mat[i][j])
                    ans += mat[i][j]
                i += 1
                j -= 1
        return ans

```
