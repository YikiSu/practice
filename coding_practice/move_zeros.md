Location: https://leetcode.com/problems/move-zeroes/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

 
# Example

## Example 1:

Input: nums = [0,1,0,3,12]

Output: [1,3,12,0,0]

## Example 2:

Input: nums = [0]

Output: [0]
 

Constraints:

- 1 <= nums.length <= 104
- -231 <= nums[i] <= 231 - 1
 

# My solution
```python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        length = len(nums)
        ind = 0
        while ind < length:
            if nums[ind] == 0 and ind == 0:
                nums[:] = nums[ind+1:] + [0]
                length -= 1
            elif nums[ind] == 0:
                nums[:] = nums[:ind] + nums[ind+1:] + [0]
                length -= 1
            else:
                ind += 1
```
