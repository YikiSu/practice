Location: https://leetcode.com/problems/pascals-triangle/description/
# Question
Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:
 
# Example

## Example 1:

Input: numRows = 5

Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]

## Example 2:

Input: numRows = 1

Output: [[1]]


Constraints:

1 <= numRows <= 30
 

# My solution 
```python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        res = [[1]+[0]*(numRows-1) for i in range(numRows)]
        ans = []
        for row in range(numRows):
            if row == 0:
                ans.append(res[0][:row+1])
            else:
                for col in range(1, numRows):
                    res[row][col] = res[row-1][col-1]+res[row-1][col]
                ans.append(res[row][:row+1])
        return ans        
```
