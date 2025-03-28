Location: https://leetcode.com/problems/merge-intervals/description/
# Question
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.
# Example

## Example 1:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]

Output: [[1,6],[8,10],[15,18]]

Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

## Example 2:

Input: intervals = [[1,4],[4,5]]

Output: [[1,5]]

Explanation: Intervals [1,4] and [4,5] are considered overlapping.

## Constraints:

1 <= intervals.length <= 104\
intervals[i].length == 2\
0 <= starti <= endi <= 104
 

# My solution (follows hints on ChatGPT)
```python
class Solution(object):
    def merge(self, intervals):
        """
        :type intervals: List[List[int]]
        :rtype: List[List[int]]
        """
        intervals = sorted(intervals, key = lambda x:x[0])
        ans = []
        if len(intervals) == 1:
            return intervals
        ans.append(intervals[0])
        for i in range(1, len(intervals)):
            pre_left = ans[-1][0]
            pre_right = ans[-1][1]
            post_left = intervals[i][0]
            post_right = intervals[i][1]
            if post_left > pre_right:
                ans.append(intervals[i])
            else:
                left = min(pre_left, post_left)
                right = max(pre_right, post_right)
                ans[-1] = [left, right]
        return ans
      
```
