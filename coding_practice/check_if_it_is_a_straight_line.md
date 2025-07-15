Location: https://leetcode.com/problems/check-if-it-is-a-straight-line/description/
# Question
You are given an array coordinates, coordinates[i] = [x, y], where [x, y] represents the coordinate of a point. Check if these points make a straight line in the XY plane.

 
# Example

## Example 1:

Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]

Output: true

## Example 2:

Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]

Output: false

## Constraints:

2 <= coordinates.length <= 1000\
coordinates[i].length == 2\
-10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4\
coordinates contains no duplicate point.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def checkStraightLine(self, coordinates):
        """
        :type coordinates: List[List[int]]
        :rtype: bool
        """
        ind = 2
        slope = [coordinates[1][0]-coordinates[0][0], coordinates[1][1]-coordinates[0][1]]
        coordinates = sorted(coordinates, key=lambda x:[x[0], x[1]])
        while ind < len(coordinates):
            if slope[0]*(coordinates[ind][1]-coordinates[1][1]) != (coordinates[ind][0]-coordinates[1][0])*slope[1] :
                return False
            ind += 1
        return True
```
