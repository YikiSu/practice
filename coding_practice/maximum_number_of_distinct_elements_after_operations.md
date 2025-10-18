Location: https://leetcode.com/problems/maximum-number-of-distinct-elements-after-operations/description/?envType=daily-question&envId=2025-10-18
# Question
You are given an integer array nums and an integer k.

You are allowed to perform the following operation on each element of the array at most once:

Add an integer in the range [-k, k] to the element.

Return the maximum possible number of distinct elements in nums after performing the operations.

 
# Example

## Example 1:

Input: nums = [1,2,2,3,3,4], k = 2

Output: 6

Explanation:

nums changes to [-1, 0, 1, 2, 3, 4] after performing operations on the first four elements.

## Example 2:

Input: nums = [4,4,4,4], k = 1

Output: 3

Explanation:

By adding -1 to nums[0] and 1 to nums[1], nums changes to [3, 5, 4, 4].
 

## Constraints:

1 <= nums.length <= 105\
1 <= nums[i] <= 109\
0 <= k <= 109

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def maxDistinctElements(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        nums.sort()
        starting = -float('inf')
        cnt = 0
        for num in nums:
            cur = max(starting + 1, num-k)
            if cur <= num+k:
                starting = cur
                cnt += 1
        return cnt
```
