Location: https://leetcode.com/problems/longest-consecutive-sequence/description/
# Question
Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.
# Example

## Example 1:

Input: nums = [100,4,200,1,3,2]

Output: 4

Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

## Example 2:

Input: nums = [0,3,7,2,5,8,4,6,0,1]

Output: 9

## Example 3:

Input: nums = [1,0,1,2]

Output: 3

## Constraints:

0 <= nums.length <= 105\
-109 <= nums[i] <= 109
 

# My solution
```python
class Solution(object):
    def longestConsecutive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        sorted_nums = sorted(set(nums))
        curr_cnt = 0
        ans = 0
        curr = 0
        for ind in range(len(sorted_nums)):
            if sorted_nums[ind] == sorted_nums[curr]+1 or sorted_nums[ind] == sorted_nums[curr]:
                if ind != 0:
                    curr += 1
                curr_cnt += 1
            else:
                ans = max(ans, curr_cnt)
                curr_cnt = 1
                curr = ind
        return max(ans, curr_cnt)
```
