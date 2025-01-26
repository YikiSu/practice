Location: https://leetcode.com/problems/evaluate-division/description/?envType=study-plan-v2&envId=leetcode-75
# Question
You are given an array of variable pairs equations and an array of real numbers values, where equations[i] = [Ai, Bi] and values[i] represent the equation Ai / Bi = values[i]. Each Ai or Bi is a string that represents a single variable.

You are also given some queries, where queries[j] = [Cj, Dj] represents the jth query where you must find the answer for Cj / Dj = ?.

Return the answers to all queries. If a single answer cannot be determined, return -1.0.

Note: The input is always valid. You may assume that evaluating the queries will not result in division by zero and that there is no contradiction.

Note: The variables that do not occur in the list of equations are undefined, so the answer cannot be determined for them.

# Example
## Example 1:

Input: equations = [["a","b"],["b","c"]], values = [2.0,3.0], queries = [["a","c"],["b","a"],["a","e"],["a","a"],["x","x"]]

Output: [6.00000,0.50000,-1.00000,1.00000,-1.00000]

Explanation: 
</br>Given: a / b = 2.0, b / c = 3.0
</br>queries are: a / c = ?, b / a = ?, a / e = ?, a / a = ?, x / x = ? 
</br>return: [6.0, 0.5, -1.0, 1.0, -1.0 ]
</br>note: x is undefined => -1.0
## Example 2:

Input: equations = [["a","b"],["b","c"],["bc","cd"]], values = [1.5,2.5,5.0], queries = [["a","c"],["c","b"],["bc","cd"],["cd","bc"]]

Output: [3.75000,0.40000,5.00000,0.20000]

## Example 3:

Input: equations = [["a","b"]], values = [0.5], queries = [["a","b"],["b","a"],["a","c"],["x","y"]]

Output: [0.50000,2.00000,-1.00000,-1.00000]

# My solution (follows instructions of others)
```python
import collections
class Solution(object):
    def calcEquation(self, equations, values, queries):
        """
        :type equations: List[List[str]]
        :type values: List[float]
        :type queries: List[List[str]]
        :rtype: List[float]
        """
        var = collections.defaultdict(dict)
        for ind, equas in enumerate(equations):
            a = equas[0]
            b = equas[1]
            var[a][b] = values[ind]
            var[b][a] = 1/values[ind]
        def dfs(src, dst):
            if not (src in var and dst in var):
                return -1
            q, seen = [(src, 1)], set()
            for c, value in q:
                if c == dst:
                    return value
                seen.add(c)
                for d in var[c]:
                    if d not in seen:
                        q.append([d, value*var[c][d]])
            return -1
        return [dfs(c,d) for c, d in queries]
                   
```
