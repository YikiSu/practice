Location: https://leetcode.com/problems/first-completely-painted-row-or-column/description/?envType=daily-question&envId=2025-04-24
# Question
You are given a 0-indexed integer array arr, and an m x n integer matrix mat. arr and mat both contain all the integers in the range [1, m * n].

Go through each index i in arr starting from index 0 and paint the cell in mat containing the integer arr[i].

Return the smallest index i at which either a row or a column will be completely painted in mat.

 
# Example

## Example 1:

Input: arr = [1,3,4,2], mat = [[1,4],[2,3]]

Output: 2

Explanation: The moves are shown in order, and both the first row and second column of the matrix become fully painted at arr[2].

## Example 2:

Input: arr = [2,8,7,4,1,3,5,6,9], mat = [[3,2,5],[1,4,6],[8,7,9]]

Output: 3

Explanation: The second column becomes fully painted at arr[3].

## Constraints:

m == mat.length\
n = mat[i].length\
arr.length == m * n\
1 <= m, n <= 105\
1 <= m * n <= 105\
1 <= arr[i], mat[r][c] <= m * n\
All the integers of arr are unique.\
All the integers of mat are unique.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def firstCompleteIndex(self, arr, mat):
        """
        :type arr: List[int]
        :type mat: List[List[int]]
        :rtype: int
        """
        rows = [len(mat[0])]*len(mat)
        cols = [len(mat)]*len(mat[0])
        pos = {}
        for i in range(len(mat)):
            for j in range(len(mat[0])):
                pos[mat[i][j]] = [i, j]
        for ind, num in enumerate(arr):
            r, l = pos[num][0], pos[num][1]
            rows[r] -= 1
            cols[l] -= 1
            if rows[r] <=0 or cols[l] <= 0:
                return ind
        
```
