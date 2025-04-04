Location: https://leetcode.com/problems/insert-interval/description/
# Question
You are given an array of non-overlapping intervals intervals where intervals[i] = [starti, endi] represent the start and the end of the ith interval and intervals is sorted in ascending order by starti. You are also given an interval newInterval = [start, end] that represents the start and end of another interval.

Insert newInterval into intervals such that intervals is still sorted in ascending order by starti and intervals still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return intervals after the insertion.

Note that you don't need to modify intervals in-place. You can make a new array and return it.
 
# Example

## Example 1:

Input: intervals = [[1,3],[6,9]], newInterval = [2,5]

Output: [[1,5],[6,9]]

## Example 2:

Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]

Output: [[1,2],[3,10],[12,16]]

Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].

## Constraints:

0 <= intervals.length <= 104\
intervals[i].length == 2\
0 <= starti <= endi <= 105\
intervals is sorted by starti in ascending order.\
newInterval.length == 2\
0 <= start <= end <= 105
 

# My solution 
```python
class Solution(object):
    def insert(self, intervals, newInterval):
        """
        :type intervals: List[List[int]]
        :type newInterval: List[int]
        :rtype: List[List[int]]
        """
        newint = sorted(intervals+[newInterval], key = lambda x:x[0])
        ans = []
        while newint:
            curr = newint.pop(0)
            if not ans:
                ans.append(curr)
            
            left = curr[0]
            right = curr[1]
            pre_left = ans[-1][0]
            pre_right = ans[-1][1]
            if pre_left <= left and pre_right < right and left <= pre_right:
                ans.pop(-1)
                ans.append([pre_left, right])
            elif left <= pre_left and pre_right > right and left < pre_right:
                ans.pop(-1)
                ans.append([left, pre_right])
            elif pre_left <=left and pre_right>=right:
                continue
            elif left > pre_right:
                ans.append(curr)
        return ans
        
```
