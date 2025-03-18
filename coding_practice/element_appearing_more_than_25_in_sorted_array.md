Location: https://leetcode.com/problems/element-appearing-more-than-25-in-sorted-array/description/
# Question
Given an integer array sorted in non-decreasing order, there is exactly one integer in the array that occurs more than 25% of the time, return that integer.
 
# Example

## Example 1:

Input: arr = [1,2,2,6,6,6,6,7,10]

Output: 6

## Example 2:

Input: arr = [1,1]

Output: 1

## Constraints:

1 <= arr.length <= 104\
0 <= arr[i] <= 105
 

# My solution 
```python
import collections
class Solution(object):
    def findSpecialInteger(self, arr):
        """
        :type arr: List[int]
        :rtype: int
        """
        cnt = collections.Counter(arr)
        for key in sorted(cnt, reverse= True):
            if cnt[key] > len(arr)*0.25:
                return key
```
