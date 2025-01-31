Location: https://leetcode.com/problems/minimum-domino-rotations-for-equal-row/description/
# Question
In a row of dominoes, tops[i] and bottoms[i] represent the top and bottom halves of the ith domino. (A domino is a tile with two numbers from 1 to 6 - one on each half of the tile.)

We may rotate the ith domino, so that tops[i] and bottoms[i] swap values.

Return the minimum number of rotations so that all the values in tops are the same, or all the values in bottoms are the same.

If it cannot be done, return -1.

# Example

## Example 1:

Input: tops = [2,1,2,4,2,2], bottoms = [5,2,6,2,3,2]

Output: 2

Explanation: The first figure represents the dominoes as given by tops and bottoms: before we do any rotations.
If we rotate the second and fourth dominoes, we can make every value in the top row equal to 2, as indicated by the second figure.
## Example 2:

Input: tops = [3,5,1,2,3], bottoms = [3,6,3,3,4]

Output: -1

Explanation: In this case, it is not possible to rotate the dominoes to make one row of values equal.


Constraints:
- 2 <= tops.length <= 2 * 104
- bottoms.length == tops.length
- 1 <= tops[i], bottoms[i] <= 6

# My solution (follows instructions on solutions)
```python
import collections
import numpy as np
class Solution(object):
    def minDominoRotations(self, tops, bottoms):
        """
        :type tops: List[int]
        :type bottoms: List[int]
        :rtype: int
        """

        top_cnt = collections.Counter(tops)
        bo_cnt = collections.Counter(bottoms)
        same = 0
        for i in range(len(tops)):
            if tops[i] == bottoms[i]:
                same += 1
        for i in range(1, max(max(top_cnt), max(bo_cnt))+1):
            if top_cnt[i]+bo_cnt[i]-same == len(tops):
                return len(tops)-max(top_cnt[i], bo_cnt[i])
        return -1

        

```
