Location: https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/description/
# Question
Given an array of integers nums and an integer limit, return the size of the longest non-empty subarray such that the absolute difference between any two elements of this subarray is less than or equal to limit.

 
# Example

## Example 1:

Input: nums = [8,2,4,7], limit = 4

Output: 2 

Explanation: All subarrays are: \
[8] with maximum absolute diff |8-8| = 0 <= 4.\
[8,2] with maximum absolute diff |8-2| = 6 > 4. \
[8,2,4] with maximum absolute diff |8-2| = 6 > 4.\
[8,2,4,7] with maximum absolute diff |8-2| = 6 > 4.\
[2] with maximum absolute diff |2-2| = 0 <= 4.\
[2,4] with maximum absolute diff |2-4| = 2 <= 4.\
[2,4,7] with maximum absolute diff |2-7| = 5 > 4.\
[4] with maximum absolute diff |4-4| = 0 <= 4.\
[4,7] with maximum absolute diff |4-7| = 3 <= 4.\
[7] with maximum absolute diff |7-7| = 0 <= 4. \
Therefore, the size of the longest subarray is 2.
## Example 2:

Input: nums = [10,1,2,4,7,2], limit = 5

Output: 4 

Explanation: The subarray [2,4,7,2] is the longest since the maximum absolute diff is |2-7| = 5 <= 5.

## Example 3:

Input: nums = [4,2,2,2,4,4,2,2], limit = 0

Output: 3
 
## Constraints:

1 <= nums.length <= 105\
1 <= nums[i] <= 109\
0 <= limit <= 109
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def longestSubarray(self, nums, limit):
        """
        :type nums: List[int]
        :type limit: int
        :rtype: int
        """
        ans = -float('inf')
        max_dp = collections.deque([])
        min_dp = collections.deque([])
        l = 0
        for ind, num in enumerate(nums):
            while max_dp and nums[max_dp[-1]] <= num:
                max_dp.pop()
            max_dp.append(ind)
            while min_dp and nums[min_dp[-1]] >= num:
                min_dp.pop()
            min_dp.append(ind)
            while max_dp and min_dp and abs(nums[max_dp[0]]-nums[min_dp[0]])>limit:
                l += 1
                if max_dp[0] < l:
                    max_dp.popleft()
                if min_dp[0] < l:
                    min_dp.popleft()
            ans = max(ans, ind-l+1)
                
        return ans

    
```
