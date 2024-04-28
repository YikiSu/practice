Location: https://leetcode.com/problems/product-of-array-except-self/description/?envType=study-plan-v2&envId=leetcode-75

# Question
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

# Example

## Example 1:

Input: nums = [1,2,3,4]\
Output: [24,12,8,6]
## Example 2:

Input: nums = [-1,1,0,-3,3]\
Output: [0,0,9,0,0]

 # My solution (didn't know how to do, follow the instructions of the best solutions)
 ```python
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        length = len(nums)
        res = [1]*length
        for i in range(1, length):
            res[i] = res[i-1]*nums[i-1]
        right = nums[-1]
        for i in range(length-2, -1, -1):
            res[i] = res[i]*right
            right = right * nums[i]

        return res
```
