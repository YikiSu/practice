Location: https://leetcode.com/problems/intersection-of-two-arrays-ii/description/?envType=problem-list-v2&envId=binary-search
# Question
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.

 
# Example

## Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]

Output: [2,2]

## Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]

Output: [4,9]

Explanation: [9,4] is also accepted.

## Constraints:

1 <= nums1.length, nums2.length <= 1000\
0 <= nums1[i], nums2[i] <= 1000
 

# My solution 
```python
import collections
class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        ans = []
        cnt_1 = collections.Counter(nums1)
        cnt_2 = collections.Counter(nums2)
        for key, val in cnt_1.items():
            if key in cnt_2.keys():
                num = min(val, cnt_2[key])
                ans += [key]*num
        return ans
        
```
