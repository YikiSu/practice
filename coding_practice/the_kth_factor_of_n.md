Location: https://leetcode.com/problems/the-kth-factor-of-n/description/?envType=study-plan-v2&envId=amazon-spring-23-high-frequency
# Question
You are given two positive integers n and k. A factor of an integer n is defined as an integer i where n % i == 0.

Consider a list of all factors of n sorted in ascending order, return the kth factor in this list or return -1 if n has less than k factors.
 
# Example

## Example 1:

Input: n = 12, k = 3

Output: 3

Explanation: Factors list is [1, 2, 3, 4, 6, 12], the 3rd factor is 3.

## Example 2:

Input: n = 7, k = 2

Output: 7

Explanation: Factors list is [1, 7], the 2nd factor is 7.

## Example 3:

Input: n = 4, k = 4

Output: -1

Explanation: Factors list is [1, 2, 4], there is only 3 factors. We should return -1.
 
Constraints:

- 1 <= k <= n <= 1000
 

# My solution (followed solutions of others)
```python
class Solution(object):
    def kthFactor(self, n, k):
        """
        :type n: int
        :type k: int
        :rtype: int
        """
        starting = 1
        ans = []
        while starting <= n:
            if n % starting == 0:
                ans.append(starting)
                if n/starting not in ans:
                    ans.append(n/starting)
                else:
                    break
            starting += 1
        try:
            return sorted(set(ans))[k-1]
        except:
            return -1

        
```
