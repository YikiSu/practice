Location: https://leetcode.com/problems/combination-sum-iii/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

- Only numbers 1 through 9 are used.
- Each number is used at most once.

Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.
# Example

## Example 1:

Input: k = 3, n = 7

Output: [[1,2,4]]

Explanation:
</br>1 + 2 + 4 = 7
</br>There are no other valid combinations.

## Example 2:

Input: k = 3, n = 9

Output: [[1,2,6],[1,3,5],[2,3,4]]

Explanation: 
</br>1 + 2 + 6 = 9
</br>1 + 3 + 5 = 9
</br>2 + 3 + 4 = 9
</br>There are no other valid combinations.

## Example 3:

Input: k = 4, n = 1

Output: []

Explanation: There are no valid combinations.
Using 4 different numbers in the range [1,9], the smallest sum we can get is 1+2+3+4 = 10 and since 10 > 1, there are no valid combination.

Constraints:

- 2 <= k <= 9
- 1 <= n <= 60
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def combinationSum3(self, k, n):
        """
        :type k: int
        :type n: int
        :rtype: List[List[int]]
        """
        def dfs(nums, k, n, path, res):
            if k<0 or n<0:
                return
            if k==0 and n == 0:
                res.append(path)
            for i in range(len(nums)):
                dfs(nums[i+1:], k-1, n-nums[i], path+[nums[i]], res)
        res = []
        dfs(list(range(1, 10)), k, n, [], res)
        return res
            
```
