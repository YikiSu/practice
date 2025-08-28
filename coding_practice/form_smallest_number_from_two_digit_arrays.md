Location: https://leetcode.com/problems/form-smallest-number-from-two-digit-arrays/description/
# Question
Given two arrays of unique digits nums1 and nums2, return the smallest number that contains at least one digit from each array.

 
# Example

## Example 1:

Input: nums1 = [4,1,3], nums2 = [5,7]

Output: 15

Explanation: The number 15 contains the digit 1 from nums1 and the digit 5 from nums2. It can be proven that 15 is the smallest number we can have.

## Example 2:

Input: nums1 = [3,5,2,6], nums2 = [3,1,7]

Output: 3

Explanation: The number 3 contains the digit 3 which exists in both arrays.

## Constraints:

1 <= nums1.length, nums2.length <= 9\
1 <= nums1[i], nums2[i] <= 9\
All digits in each array are unique.
 

# My solution 
```python
class Solution(object):
    def minNumber(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: int
        """
        inter = set(nums1).intersection(set(nums2))
        if len(inter) > 0:
            return min(inter)
        else:
            return min(int(str(min(nums1))+str(min(nums2))), int(str(min(nums2))+str(min(nums1))))
```
