Location: https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/?envType=problem-list-v2&envId=array
# Question
Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

 
# Example

## Example 1:

Input: nums = [5,7,7,8,8,10], target = 8\
Output: [3,4]

## Example 2:

Input: nums = [5,7,7,8,8,10], target = 6\
Output: [-1,-1]

## Example 3:

Input: nums = [], target = 0\
Output: [-1,-1]
 

Constraints:

0 <= nums.length <= 105\
-109 <= nums[i] <= 109\
nums is a non-decreasing array.\
-109 <= target <= 109
 

# My solution (follows Chatgpt)
```python
class Solution(object):
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        if not nums:
            return [-1, -1]
        def find_left():
            l, r = 0, len(nums)-1
            while l<=r:
                mid = l + (r-l)//2
                if nums[mid] >= target:
                    r = mid - 1
                else:
                    l = mid + 1
            return l
        def find_right():
            l, r = 0, len(nums)-1
            while l<=r:
                mid = l + (r-l)//2
                if nums[mid] <= target:
                    l = mid + 1
                else:
                    r = mid - 1
            return r
        left, right = find_left(), find_right()
        if left <= right and nums[left] == target:
            return [left, right]
        else:
            return [-1, -1]

        
```
