Location: https://leetcode.com/problems/find-the-pivot-integer/description/
# Question
Given a positive integer n, find the pivot integer x such that:

The sum of all elements between 1 and x inclusively equals the sum of all elements between x and n inclusively.

Return the pivot integer x. If no such integer exists, return -1. It is guaranteed that there will be at most one pivot index for the given input.

 
# Example

## Example 1:

Input: n = 8

Output: 6

Explanation: 6 is the pivot integer since: 1 + 2 + 3 + 4 + 5 + 6 = 6 + 7 + 8 = 21.

## Example 2:

Input: n = 1

Output: 1

Explanation: 1 is the pivot integer since: 1 = 1.

## Example 3:

Input: n = 4

Output: -1

Explanation: It can be proved that no such integer exist.
 

## Constraints:

1 <= n <= 1000
 

# My solution 
```python
class Solution(object):
    def pivotInteger(self, n):
        """
        :type n: int
        :rtype: int
        """
        nums = [num for num in range(1, n+1)]
        l, r = 0, n-1
        lsum, rsum = nums[l], nums[r]
        while l<=r:
            if lsum == rsum and nums[l] == nums[r]:
                return nums[l]
            elif lsum<rsum:
                l += 1
                lsum += nums[l]
            else:
                r -= 1
                rsum += nums[r]
        return -1
```
