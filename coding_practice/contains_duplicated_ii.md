Location: https://leetcode.com/problems/contains-duplicate-ii/description/?envType=problem-list-v2&envId=array
# Question
Given an integer array nums and an integer k, return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k.

# Example

## Example 1:

Input: nums = [1,2,3,1], k = 3

Output: true

## Example 2:

Input: nums = [1,0,1,1], k = 1

Output: true

## Example 3:

Input: nums = [1,2,3,1,2,3], k = 2

Output: false
 

Constraints:

1 <= nums.length <= 105\
-109 <= nums[i] <= 109\
0 <= k <= 105
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        # for ind, num in enumerate(nums):
        #     moving = ind + 1
        #     while moving < len(nums):
        #         if num == nums[moving] and abs(ind - moving)<=k:
        #             # print(num)
        #             # print(nums[moving])
        #             return True
        #         moving += 1
        # return False
        seen = set()
        for ind, num in enumerate(nums):
            if num in seen:
                return True
            seen.add(num)
            if len(seen) > k:
                seen.remove(nums[ind-k])
        return False

        
```
