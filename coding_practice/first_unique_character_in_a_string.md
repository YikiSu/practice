Location: https://leetcode.com/problems/first-unique-character-in-a-string/description/
# Question
Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.

# Example

## Example 1:

Input: s = "leetcode"

Output: 0

Explanation:

The character 'l' at index 0 is the first character that does not occur at any other index.
## Example 2:

Input: s = "loveleetcode"

Output: 2

## Example 3:

Input: s = "aabb"

Output: -1
 

Constraints:

1 <= s.length <= 105\
s consists of only lowercase English letters.
 

# My solution 
```python
class Solution(object):
class Solution(object):
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        ans = {}
        repeated = set()
        for ind, st in enumerate(s):
            if st not in repeated:
                if st in ans.keys():
                    ans.pop(st)
                    repeated.add(st)
                else:
                    ans[st] = ind
        if not ans:
            return -1
        else:
            return min(ans.values())


```
