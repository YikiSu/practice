Location: https://leetcode.com/problems/count-subarrays-where-max-element-appears-at-least-k-times/description/?envType=daily-question&envId=2025-04-29
# Question
You are given an integer array nums and a positive integer k.

Return the number of subarrays where the maximum element of nums appears at least k times in that subarray.

A subarray is a contiguous sequence of elements within an array.

 
# Example

## Example 1:

Input: nums = [1,3,2,3,3], k = 2

Output: 6

Explanation: The subarrays that contain the element 3 at least 2 times are: [1,3,2,3], [1,3,2,3,3], [3,2,3], [3,2,3,3], [2,3,3] and [3,3].

## Example 2:

Input: nums = [1,4,2,1], k = 3

Output: 0

Explanation: No subarray contains the element 4 at least 3 times.

## Constraints:

1 <= nums.length <= 105\
1 <= nums[i] <= 106\
1 <= k <= 105
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def countSubarrays(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        max_ = max(nums)
        l = 0
        ans = 0
        cnt = 0
        for ind, num in enumerate(nums):
            if num == max_:
                cnt += 1
            while cnt >= k:
                if nums[l] == max_:
                    cnt -= 1
                l += 1
            ans += l
        return ans
       
```
