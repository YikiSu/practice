Location: https://leetcode.com/problems/sort-colors/description/?envType=problem-list-v2&envId=two-pointers
# Question
Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.
 
# Example

## Example 1:

Input: nums = [2,0,2,1,1,0]

Output: [0,0,1,1,2,2]

## Example 2:

Input: nums = [2,0,1]

Output: [0,1,2]

## Constraints:

n == nums.length\
1 <= n <= 300\
nums[i] is either 0, 1, or 2.
 
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def sortColors(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        cnt = collections.Counter(nums)
        starting = 0
        for color in sorted(cnt):
            num = cnt[color]
            for i in range(starting, starting+num):
                nums[i] = color
            starting += num
        
```
