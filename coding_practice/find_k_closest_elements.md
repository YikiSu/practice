Location: https://leetcode.com/problems/find-k-closest-elements/description/?envType=problem-list-v2&envId=heap-priority-queue
# Question
Given a sorted integer array arr, two integers k and x, return the k closest integers to x in the array. The result should also be sorted in ascending order.

An integer a is closer to x than an integer b if:

- |a - x| < |b - x|, or
- |a - x| == |b - x| and a < b

# Example

## Example 1:

Input: arr = [1,2,3,4,5], k = 4, x = 3

Output: [1,2,3,4]

## Example 2:

Input: arr = [1,1,2,3,4,5], k = 4, x = -1

Output: [1,1,2,3]

Constraints:
- 1 <= k <= arr.length
- 1 <= arr.length <= 104
- arr is sorted in ascending order.
- -104 <= arr[i], x <= 104

# My solution 
```python
class Solution(object):
    def findClosestElements(self, arr, k, x):
        """
        :type arr: List[int]
        :type k: int
        :type x: int
        :rtype: List[int]
        """
        min_heap = []
        for a in arr:
            heapq.heappush(min_heap, (abs(a-x), a))
        ans = []
        for _ in range(k):
            di, a = heapq.heappop(min_heap)
            ans.append(a)
        return sorted(ans)
```
