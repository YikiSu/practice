Location: https://leetcode.com/problems/check-if-n-and-its-double-exist/description/?envType=daily-question&envId=2025-04-18
# Question
Given an array arr of integers, check if there exist two indices i and j such that :

- i != j
- 0 <= i, j < arr.length
- arr[i] == 2 * arr[j]
 
# Example

## Example 1:

Input: arr = [10,2,5,3]

Output: true

Explanation: For i = 0 and j = 2, arr[i] == 10 == 2 * 5 == 2 * arr[j]

## Example 2:

Input: arr = [3,1,7,11]

Output: false

Explanation: There is no i and j that satisfy the conditions.

## Constraints:

2 <= arr.length <= 500\
-103 <= arr[i] <= 103
 

# My solution 
```python
class Solution(object):
    def checkIfExist(self, arr):
        """
        :type arr: List[int]
        :rtype: bool
        """
        for ind, num in enumerate(arr):
            if num*2 in arr:
                # print(arr.index(num*2))    
                if ind != arr.index(num*2):
                    return True
        return False
```
