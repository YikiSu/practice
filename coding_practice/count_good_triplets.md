Location: https://leetcode.com/problems/count-good-triplets/description/?envType=daily-question&envId=2025-04-14
# Question
Given an array of integers arr, and three integers a, b and c. You need to find the number of good triplets.

A triplet (arr[i], arr[j], arr[k]) is good if the following conditions are true:

- 0 <= i < j < k < arr.length
- |arr[i] - arr[j]| <= a
- |arr[j] - arr[k]| <= b
- |arr[i] - arr[k]| <= c

Where |x| denotes the absolute value of x.

Return the number of good triplets.

 
# Example

## Example 1:

Input: arr = [3,0,1,1,9,7], a = 7, b = 2, c = 3

Output: 4

Explanation: There are 4 good triplets: [(3,0,1), (3,0,1), (3,1,1), (0,1,1)].

## Example 2:

Input: arr = [1,1,2,2,3], a = 0, b = 0, c = 1

Output: 0

Explanation: No triplet satisfies all conditions.
 

## Constraints:

3 <= arr.length <= 100\
0 <= arr[i] <= 1000\
0 <= a, b, c <= 1000
 

# My solution 
```python
class Solution(object):
    def countGoodTriplets(self, arr, a, b, c):
        """
        :type arr: List[int]
        :type a: int
        :type b: int
        :type c: int
        :rtype: int
        """
        i, j, k = 0, 1, 2
        ans = 0
        while i < len(arr) - 2:
            # print(i)
            # print(j)
            # print(k)
            if abs(arr[i] - arr[j]) <= a and abs(arr[j]-arr[k]) <= b and abs(arr[i] - arr[k]) <= c:
                ans += 1
            if k < len(arr)-1:
                k += 1
            elif j < len(arr)-2 and k == len(arr)-1:
                j += 1
                k = j+1
            else:
                i += 1
                j = i+1
                k = j+1
        return ans
```
