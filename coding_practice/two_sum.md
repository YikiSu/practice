Location: https://leetcode.com/problems/two-sum/

# Question
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

# Example
## Example 1:

Input: nums = [2,7,11,15], target = 9

Output: [0,1]

Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

## Example 2:

Input: nums = [3,2,4], target = 6

Output: [1,2]

## Example 3:

Input: nums = [3,3], target = 6

Output: [0,1]

# My answer
```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        length = len(nums)
        i = 0
        moving = i+1
        while i < length-1:
            if nums[i] + nums[moving] == target:
                return [i, moving]
            elif moving == length - 1:
                i += 1
                moving = i+1
            else:
                moving += 1
```

# Solution code
```python
class Solution(object):
    def twoSum(self, nums, target):
        num_indices={}
        for i,j in enumerate(nums):
            complement= target-j
            if complement in num_indices:
                # If found, return the indices
                return num_indices[complement], i
            
            # Otherwise, store the current number and its index in the dictionary
            num_indices[j] = i
        
        # If no solution is found, return None
        return None
```
