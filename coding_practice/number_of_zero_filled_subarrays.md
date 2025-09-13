Location: https://leetcode.com/problems/number-of-zero-filled-subarrays/description/?envType=daily-question&envId=2025-09-13
# Question
Given an integer array nums, return the number of subarrays filled with 0.

A subarray is a contiguous non-empty sequence of elements within an array.

 
# Example

## Example 1:

Input: nums = [1,3,0,0,2,0,0,4]

Output: 6

Explanation: \
There are 4 occurrences of [0] as a subarray.\
There are 2 occurrences of [0,0] as a subarray.\
There is no occurrence of a subarray with a size more than 2 filled with 0. Therefore, we return 6.

## Example 2:

Input: nums = [0,1,1]

Output: []

Explanation: The only possible triplet does not sum up to 0.

## Example 3:

Input: nums = [2,10,2019]

Output: 0

Explanation: There is no subarray filled with 0. Therefore, we return 0.
 

## Constraints:

1 <= nums.length <= 105\
-109 <= nums[i] <= 109

# My solution 
```python
class Solution(object):
    def zeroFilledSubarray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ind = []
        ans = 0
        for i, num in enumerate(nums):
            if num == 0:
                # print(i)
                # print(ind)
                if ind and i == ind[-1]+1:
                    ind.append(i)
                elif ind and i != ind[-1]+1:
                    cur = len(ind)
                    ans += (cur*(cur+1))/2
                    ind = [i]
                else:
                    ind.append(i)
        if ind:
            cur = len(ind)
            ans += (cur*(cur+1))/2
        return ans
```
