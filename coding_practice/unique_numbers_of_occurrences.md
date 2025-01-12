Location: [https://leetcode.com/problems/evaluate-reverse-polish-notation/description/](https://leetcode.com/problems/unique-number-of-occurrences/description/?envType=study-plan-v2&envId=leetcode-75)

# Question
Given an array of integers arr, return true if the number of occurrences of each value in the array is unique or false otherwise.

 # Example

## Example 1:

Input: arr = [1,2,2,1,1,3]
</br>Output: true
</br>Explanation: The value 1 has 3 occurrences, 2 has 2 and 3 has 1. No two values have the same number of occurrences.
## Example 2:

Input: arr = [1,2]
</br>Output: false
## Example 3:

Input: arr = [-3,0,1,-3,1,1,1,-3,10,0]
</br>Output: true

# Constraints
- 1 <= arr.length <= 1000
- -1000 <= arr[i] <= 1000

# My solution 
```pythonimport collections
class Solution(object):
    def uniqueOccurrences(self, arr):
        """
        :type arr: List[int]
        :rtype: bool
        """
        cnt = collections.Counter(arr)
        return len(cnt.values()) == len(set(cnt.values()))
```
