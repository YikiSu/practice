Location: https://leetcode.com/problems/3sum-closest/description/?envType=problem-list-v2&envId=array
# Question
Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.

 
# Example

## Example 1:

Input: nums = [-1,2,1,-4], target = 1\
Output: 2\
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

## Example 2:

Input: nums = [0,0,0], target = 1\
Output: 0\
Explanation: The sum that is closest to the target is 0. (0 + 0 + 0 = 0).

Constraints:

3 <= nums.length <= 500\
-1000 <= nums[i] <= 1000\
-104 <= target <= 104
 

# My solution (chatgpt helps me correct it)
```python
import numpy as np
class Solution(object):
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        smallest = np.inf
        ans = 0
        nums.sort()
        for left in range(len(nums)-2):
            mid = left + 1
            right = len(nums)-1
            while mid < right:
                cursum = nums[left]+nums[right]+nums[mid]
                curdiff = abs(cursum - target)
                if curdiff < smallest:
                    ans = cursum
                    smallest = curdiff
                if cursum > target:
                    right -= 1
                else:
                    mid += 1
        return ans        
```
