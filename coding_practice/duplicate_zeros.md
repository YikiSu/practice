Location: https://leetcode.com/problems/duplicate-zeros/description/
# Question
Given a fixed-length integer array arr, duplicate each occurrence of zero, shifting the remaining elements to the right.

Note that elements beyond the length of the original array are not written. Do the above modifications to the input array in place and do not return anything.

 
# Example

## Example 1:

Input: arr = [1,0,2,3,0,4,5,0]

Output: [1,0,0,2,3,0,0,4]

Explanation: After calling your function, the input array is modified to: [1,0,0,2,3,0,0,4]

## Example 2:

Input: arr = [1,2,3]

Output: [1,2,3]

Explanation: After calling your function, the input array is modified to: [1,2,3]
## Constraints:

1 <= arr.length <= 104\
0 <= arr[i] <= 9
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def duplicateZeros(self, arr):
        """
        :type arr: List[int]
        :rtype: None Do not return anything, modify arr in-place instead.
        """
        n = len(arr)
        l = 0
        while l < n:
            if arr[l] == 0:
                # arr = arr[:l+1]+[0]+arr[l+1:n-1]
                arr.pop()
                arr.insert(l+1, 0)
                l += 2
            else:
                l += 1
```
