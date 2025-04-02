Location: https://leetcode.com/problems/minimum-size-subarray-sum/
# Question
Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.
# Example

## Example 1:

Input: target = 7, nums = [2,3,1,2,4,3]

Output: 2

Explanation: The subarray [4,3] has the minimal length under the problem constraint.

## Example 2:

Input: target = 4, nums = [1,4,4]

Output: 1

## Example 3:

Input: target = 11, nums = [1,1,1,1,1,1,1,1]

Output: 0
 

## Constraints:

1 <= target <= 109\
1 <= nums.length <= 105\
1 <= nums[i] <= 104
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def minSubArrayLen(self, target, nums):
        """
        :type target: int
        :type nums: List[int]
        :rtype: int
        """
        ans = float('inf')
        left, right = 0, 1
        prefix = nums[left]
        if prefix >= target:
            ans = 1
        while left < len(nums) and right < len(nums):
            if prefix + nums[right] < target:
                prefix += nums[right]
                right += 1
            else:
                ans = min(ans, right-left+1)
                prefix -= nums[left]
                left += 1
        return ans if ans != float('inf') else 0
        
```
