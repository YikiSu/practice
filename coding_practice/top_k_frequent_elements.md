Location: https://leetcode.com/problems/top-k-frequent-elements/description/?envType=problem-list-v2&envId=heap-priority-queue
# Question
Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

# Example

## Example 1:

Input: nums = [1,1,1,2,2,3], k = 2

Output: [1,2]
## Example 2:

Input: nums = [1], k = 1

Output: [1]


Constraints:

1 <= nums.length <= 105\
-104 <= nums[i] <= 104\
k is in the range [1, the number of unique elements in the array].\
It is guaranteed that the answer is unique.
 

# My solution 
```python
from collections import Counter
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        # cnt = Counter(nums)
        # pq = []
        # for key, value in cnt.items():
        #     heapq.heappush(pq, (-value, key))
        # ans = []
        # for i in range(k):
        #     ct, val = heapq.heappop(pq)
        #     ans.append(val)
        # return ans
        cnt = Counter(nums)
        return sorted(cnt, key=cnt.get, reverse=True)[:k]
        
```
