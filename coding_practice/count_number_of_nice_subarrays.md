Location: https://leetcode.com/problems/count-number-of-nice-subarrays/description/
# Question
Given an array of integers nums and an integer k. A continuous subarray is called nice if there are k odd numbers on it.

Return the number of nice sub-arrays.
# Example

## Example 1:

Input: nums = [1,1,2,1,1], k = 3

Output: 2

Explanation: The only sub-arrays with 3 odd numbers are [1,1,2,1] and [1,2,1,1].

## Example 2:

Input: nums = [2,4,6], k = 1

Output: 0

Explanation: There are no odd numbers in the array.

## Example 3:

Input: nums = [2,2,2,1,2,2,1,2,2,2], k = 2

Output: 16
 

## Constraints:

1 <= nums.length <= 50000\
1 <= nums[i] <= 10^5\
1 <= k <= nums.length

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def numberOfSubarrays(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        ans = 0
        cnt = collections.defaultdict(int)
        cnt[0] += 1
        prefix_sum = 0
        for num in nums:
            prefix_sum += num%2 
            if prefix_sum - k in cnt:
                ans += cnt[prefix_sum - k]
            cnt[prefix_sum] += 1
        return ans
```
