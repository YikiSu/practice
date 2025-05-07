Location: https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/?envType=daily-question&envId=2025-05-07
# Question
Given an array nums, return true if the array was originally sorted in non-decreasing order, then rotated some number of positions (including zero). Otherwise, return false.

There may be duplicates in the original array.

Note: An array A rotated by x positions results in an array B of the same length such that B[i] == A[(i+x) % A.length] for every valid index i.

 
# Example

## Example 1:

Input: nums = [3,4,5,1,2]

Output: true

Explanation: [1,2,3,4,5] is the original sorted array.\
You can rotate the array by x = 3 positions to begin on the element of value 3: [3,4,5,1,2].

## Example 2:

Input: nums = [2,1,3,4]

Output: false

Explanation: There is no sorted array once rotated that can make nums.

## Example 3:

Input: nums = [1,2,3]

Output: true

Explanation: [1,2,3] is the original sorted array.\
You can rotate the array by x = 0 positions (i.e. no rotation) to make nums.
 

## Constraints:

1 <= nums.length <= 100\
1 <= nums[i] <= 100
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def check(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        # curr = 0
        # for ind in range(1, len(nums)):
        #     print(curr)
        #     if nums[ind] < nums[ind-1]+1:
        #         curr += 1
        #     if curr > 1:
        #         return False
        # return True
        ans = sorted(nums)
        for ind in range(len(nums)):
            if nums[ind:] + nums[:ind] == ans:
                return True
        return False
```
