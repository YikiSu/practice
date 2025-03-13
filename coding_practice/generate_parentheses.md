Location: https://leetcode.com/problems/generate-parentheses/description/
# Question
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
# Example

## Example 1:

Input: n = 3

Output: ["((()))","(()())","(())()","()(())","()()()"]

## Example 2:

Input: n = 1

Output: ["()"]

## Constraints:

1 <= n <= 8
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        ans = []
        def backtrack(s, open_cnt, close_cnt):
            if len(s) == 2*n:
                ans.append(s)
            if open_cnt < n:
                backtrack(s+"(", open_cnt+1, close_cnt)
            if close_cnt < open_cnt:
                backtrack(s+")", open_cnt, close_cnt+1)
        backtrack("", 0, 0)
        return ans
```
