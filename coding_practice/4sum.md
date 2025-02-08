Location: https://leetcode.com/problems/4sum/description/?envType=problem-list-v2&envId=array
# Question
Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:
- 0 <= a, b, c, d < n
- a, b, c, and d are distinct.
- nums[a] + nums[b] + nums[c] + nums[d] == target\
You may return the answer in any order.

 
# Example

## Example 1:

Input: nums = [1,0,-1,0,-2,2], target = 0

Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]

## Example 2:

Input: nums = [2,2,2,2,2], target = 8

Output: [[2,2,2,2]]


Constraints:

1 <= nums.length <= 200\
-109 <= nums[i] <= 109\
-109 <= target <= 109
 

# My solution 
```python
class Solution(object):
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        nums.sort()
        ans = []
        for left in range(len(nums)-3):
            for midleft in range(left+1, len(nums)-2):
                mid = midleft + 1
                right = len(nums) - 1
                while mid < right:
                    if nums[left]+nums[midleft]+nums[mid]+nums[right] > target:
                        right -= 1
                    elif nums[left]+nums[midleft]+nums[mid]+nums[right] < target:
                        mid += 1
                    else:
                        if sorted([nums[left],nums[midleft],nums[mid],nums[right]]) not in ans:
                            ans.append(sorted([nums[left],nums[midleft],nums[mid],nums[right]]))
                        mid += 1
                        right -= 1
        return ans

        
```
