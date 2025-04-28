Location: https://leetcode.com/problems/maximum-subarray/description/
# Question
Given an integer array nums, find the subarray with the largest sum, and return its sum.
 
# Example

## Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]

Output: 6

Explanation: The subarray [4,-1,2,1] has the largest sum 6.

## Example 2:

Input: nums = [1]

Output: 1

Explanation: The subarray [1] has the largest sum 1.

## Example 3:

Input: nums = [5,4,-1,7,8]

Output: 23

Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
 
 

## Constraints:

1 <= nums.length <= 105\
-104 <= nums[i] <= 104
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        res = -float('inf')
        pre_sum = 0
        # l = 0
        # for ind, num in enumerate(nums):
        #     print(pre_sum)
        #     print(l)
        #     print(res)
        #     pre_sum += num
        #     while pre_sum <= res and l <= ind:
        #         pre_sum -= nums[l]
        #         l += 1
        #     res = max(res, pre_sum)
        # return res
        for num in nums:
            pre_sum += num
            res = max(res, pre_sum)
            if pre_sum < 0:
                pre_sum = 0
        return res
```
