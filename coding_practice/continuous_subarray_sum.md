Location: https://leetcode.com/problems/continuous-subarray-sum/description/?envType=problem-list-v2&envId=prefix-sum
# Question
Given an integer array nums and an integer k, return true if nums has a good subarray or false otherwise.

A good subarray is a subarray where:

- its length is at least two, and
- the sum of the elements of the subarray is a multiple of k.

Note that:

- A subarray is a contiguous part of the array.
- An integer x is a multiple of k if there exists an integer n such that x = n * k. 0 is always a multiple of k.
# Example

## Example 1:

Input: nums = [23,2,4,6,7], k = 6

Output: true

Explanation: [2, 4] is a continuous subarray of size 2 whose elements sum up to 6.

## Example 2:

Input: nums = [23,2,6,4,7], k = 6

Output: true

Explanation: [23, 2, 6, 4, 7] is an continuous subarray of size 5 whose elements sum up to 42.\
42 is a multiple of 6 because 42 = 7 * 6 and 7 is an integer.

## Example 3:

Input: nums = [23,2,6,4,7], k = 13

Output: false
 

## Constraints:

1 <= nums.length <= 105\
0 <= nums[i] <= 109\
0 <= sum(nums[i]) <= 231 - 1\
1 <= k <= 231 - 1
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def checkSubarraySum(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        cnt = collections.defaultdict(int)
        cnt[0] = -1
        total = 0
        for ind, num in enumerate(nums):
            total += num
            if k != 0:
                curr = total%k
            else:
                curr = total
            if curr in cnt:
                if ind - cnt[curr] >=2:
                    return True
            else:
                cnt[curr] = ind
        return False
        # cnt = collections.defaultdict(int)
        # dp = 0
        # cnt[0] = -1
        # for ind, num in enumerate(nums):
        #     dp = (dp+num)%k
        #     if dp in cnt.keys():
        #         if ind - cnt[dp] >= 2:
        #             return True
        #     else:
        #         cnt[dp] = ind
        # return False
        # if len(nums) == 1:
        #     return False
        # for ind, num in enumerate(nums):
        #     curr = (dp+num)%k 
        #     dp += num
        #     print(curr)
        #     if curr in cnt.keys():
        #         for i in cnt[curr]:
        #             if ind - i >= 1:
        #                 return True
        #     else:
        #         cnt[curr] = [ind]
        # return False

       
```
