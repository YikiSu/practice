Location: https://leetcode.com/problems/degree-of-an-array/description/
# Question
Given a non-empty array of non-negative integers nums, the degree of this array is defined as the maximum frequency of any one of its elements.

Your task is to find the smallest possible length of a (contiguous) subarray of nums, that has the same degree as nums.

 
# Example

## Example 1:

Input: nums = [1,2,2,3,1]

Output: 2

Explanation: \
The input array has a degree of 2 because both elements 1 and 2 appear twice.\
Of the subarrays that have the same degree:\
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]\
The shortest length is 2. So return 2.

## Example 2:

Input: nums = [1,2,2,3,1,4,2]

Output: 6

Explanation: \
The degree is 3 because the element 2 is repeated 3 times.\
So [2,2,3,1,4,2] is the shortest subarray, therefore returning 6.

## Constraints:

nums.length will be between 1 and 50,000.\
nums[i] will be an integer between 0 and 49,999.
 

# My solution 
```python
import collections
class Solution(object):
    def findShortestSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        cnt = collections.Counter(nums)
        max_fre = max(cnt.values())
        keys = [key for key in cnt.keys() if cnt[key]==max_fre]
        inds = collections.defaultdict(list)
        for ind, num in enumerate(nums):
            inds[num].append(ind)
        ans = float("inf")
        for key in keys:
            if len(inds[key]) == 1:
                ans = min(ans, 1)
            else:
                ans = min(ans, max(inds[key])-min(inds[key])+1)
        return ans
```
