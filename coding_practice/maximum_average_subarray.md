Location: https://leetcode.com/problems/maximum-average-subarray-i/description/?envType=study-plan-v2&envId=leetcode-75

# Question
You are given an integer array nums consisting of n elements, and an integer k.

Find a contiguous subarray whose length is equal to k that has the maximum average value and return this value. Any answer with a calculation error less than 10-5 will be accepted.

 

 # Example

## Example 1:

- Input: nums = [1,12,-5,-6,50,3], k = 4
- Output: 12.75000
- Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75
## Example 2:

- Input: nums = [5], k = 1
- Output: 5.00000
- Explanation: (4 + (13 / 5)) = 6

# Constraints:
- n == nums.length
- 1 <= k <= n <= 105
- -104 <= nums[i] <= 104

# My solution (follow instructions of others)
```python
import numpy as np
class Solution(object):
    def findMaxAverage(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: float
        """
        if len(nums) == 1:
            return float(nums[0])
        starting = 0
        ending = k
        ans = float(sum(nums[:k]))/k
        avg = float(sum(nums[:k]))/k
        while ending < len(nums):
            avg -= float(nums[starting])/k
            avg += float(nums[ending])/k 
            ans = max(ans, avg)
            starting += 1
            ending += 1
        return ans

```
