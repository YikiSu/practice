Location: https://leetcode.com/problems/maximum-frequency-of-an-element-after-performing-operations-i/description/?envType=daily-question&envId=2025-10-21
# Question
You are given an integer array nums and two integers k and numOperations.

You must perform an operation numOperations times on nums, where in each operation you:

Select an index i that was not selected in any previous operations.\
Add an integer in the range [-k, k] to nums[i].\
Return the maximum possible frequency of any element in nums after performing the operations.

 
# Example

## Example 1:

Input: nums = [1,4,5], k = 1, numOperations = 2

Output: 2

Explanation:

We can achieve a maximum frequency of two by:

Adding 0 to nums[1]. nums becomes [1, 4, 5].\
Adding -1 to nums[2]. nums becomes [1, 4, 4].

## Example 2:

Input: nums = [5,11,20,20], k = 5, numOperations = 1

Output: 2

Explanation:

We can achieve a maximum frequency of two by:

Adding 0 to nums[1].

## Constraints:

1 <= nums.length <= 105\
1 <= nums[i] <= 105\
0 <= k <= 105\
0 <= numOperations <= nums.length
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def maxFrequency(self, nums, k, numOperations):
        """
        :type nums: List[int]
        :type k: int
        :type numOperations: int
        :rtype: int
        """
        currMax = nums[0]
        for i in range(1,len(nums)):
            if nums[i] > currMax:
                currMax = nums[i]

        l = currMax + k + 2
        freq = [0]*l
        prefix = [0]*l

        for num in nums:
            freq[num] += 1
        
        prefix[0] = freq[0]

        for i in range(1,l):
            prefix[i] = prefix[i-1] + freq[i]

        res = 0
        for i in range(l):
            left = max(0,i-k)
            right = min(l-1, i+k)

            total = prefix[right]
            if left>0:
                total -= prefix[left-1]
            res = max(res, freq[i] + min(numOperations, total-freq[i]))
        return res
```
