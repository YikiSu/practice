Location: https://leetcode.com/problems/subarray-product-less-than-k/description/
# Question
Given an array of integers nums and an integer k, return the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than k.
# Example

## Example 1:

Input: nums = [10,5,2,6], k = 100

Output: 8

Explanation: The 8 subarrays that have product less than 100 are:\
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]\
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.

## Example 2:

Input: nums = [1,2,3], k = 0

Output: 0

## Constraints:

1 <= nums.length <= 3 * 104\
1 <= nums[i] <= 1000\
0 <= k <= 106
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def numSubarrayProductLessThanK(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        ans = 0
        left, right = 0, 0
        prefix = 1
        while left < len(nums) and right < len(nums):
            if nums[left] >= k:
                prefix = 1
                left += 1
                right = left
            elif prefix*nums[right] < k:
                # print(left)
                # print(right)
                # print(prefix)
                ans += (right-left+1)
                prefix *= nums[right]
                right += 1
            else:
                prefix = prefix/nums[left]
                left += 1
        return ans
        # for ind, num in enumerate(nums):
        #     if num < k:
        #         ans += 1
        #     if ind == len(nums)-1:
        #         continue
        #     else:
        #         right = ind + 1
        #         prefix = num
        #         while right < len(nums):
        #             if prefix * nums[right] < k:
        #                 ans += 1
        #                 prefix *= nums[right]
        #                 right += 1
        #             else:
        #                 break
        # return ans
```
