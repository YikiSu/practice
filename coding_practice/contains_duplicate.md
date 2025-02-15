Location: https://leetcode.com/problems/contains-duplicate/description/?envType=problem-list-v2&envId=array
# Question
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
 
# Example

## Example 1:

Input: nums = [1,2,3,1]

Output: true

Explanation: The element 1 occurs at the indices 0 and 3.
## Example 2:

Input: nums = [1,2,3,4]

Output: false

Explanation: All elements are distinct.

## Example 3:

Input: nums = [1,1,1,3,3,4,3,2,4,2]

Output: true
 
Constraints:

1 <= nums.length <= 105\
-109 <= nums[i] <= 109
 

# My solution 
```python
import collections
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        cnt = collections.Counter(nums)
        ans = 0
        for key, value in cnt.items():
            if value > 1:
                ans += 1
        return ans != 0
        
```
