Location: https://leetcode.com/problems/number-of-equivalent-domino-pairs/description/?envType=daily-question&envId=2025-05-04
# Question
Given a list of dominoes, dominoes[i] = [a, b] is equivalent to dominoes[j] = [c, d] if and only if either (a == c and b == d), or (a == d and b == c) that is, one domino can be rotated to be equal to another domino.

Return the number of pairs (i, j) for which 0 <= i < j < dominoes.length, and dominoes[i] is equivalent to dominoes[j].

 
# Example

## Example 1:

Input: dominoes = [[1,2],[2,1],[3,4],[5,6]]

Output: 1

## Example 2:

Input: dominoes = [[1,2],[1,2],[1,1],[1,2],[2,2]]

Output: 3

## Constraints:

1 <= dominoes.length <= 4 * 104\
dominoes[i].length == 2\
1 <= dominoes[i][j] <= 9
 

# My solution 
```python
class Solution(object):
    def numEquivDominoPairs(self, dominoes):
        """
        :type dominoes: List[List[int]]
        :rtype: int
        """
        dominoes = [sorted(pair) for pair in dominoes]
        cnt = collections.defaultdict(int)
        if len(dominoes) == 1:
            return 0
        ans = 0
        for d in dominoes:
            cnt[(d[0], d[1])] += 1
        for key, val in cnt.items():
            ans += (val*(val-1))/2
        return ans
```
