Location: https://leetcode.com/problems/majority-element/description/
# Question
Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.
# Example

## Example 1:

Input: nums = [3,2,3]

Output: 3
## Example 2:

Input: nums = [2,2,1,1,1,2,2]

Output: 2

Constraints:

n == nums.length\
1 <= n <= 5 * 104\
-109 <= nums[i] <= 109
 

# My solution
```python
import collections 
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        cnt = collections.Counter(nums)
        return max(cnt, key = cnt.get)
        
```
