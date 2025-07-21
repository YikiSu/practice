Location: https://leetcode.com/problems/delete-characters-to-make-fancy-string/description/?envType=daily-question&envId=2025-07-21
# Question
A fancy string is a string where no three consecutive characters are equal.

Given a string s, delete the minimum possible number of characters from s to make it fancy.

Return the final string after the deletion. It can be shown that the answer will always be unique.

 
# Example

## Example 1:

Input: s = "leeetcode"

Output: "leetcode"

Explanation:\
Remove an 'e' from the first group of 'e's to create "leetcode".\
No three consecutive characters are equal, so return "leetcode".

## Example 2:

Input: s = "aaabaaaa"

Output: "aabaa"

Explanation:\
Remove an 'a' from the first group of 'a's to create "aabaaaa".\
Remove two 'a's from the second group of 'a's to create "aabaa".\
No three consecutive characters are equal, so return "aabaa".

## Example 3:

Input: s = "aab"

Output: "aab"

Explanation: No three consecutive characters are equal, so return "aab".
 

## Constraints:

1 <= s.length <= 105\
s consists only of lowercase English letters.
 

# My solution
```python
class Solution(object):
    def makeFancyString(self, s):
        """
        :type s: str
        :rtype: str
        """
        ans = ""
        curr = []
        for st in s:
            if not curr or st == curr[-1]:
                curr.append(st)
            elif curr and st != curr[-1]:
                ans += "".join(curr[:2])
                curr = [st]
        return ans + "".join(curr[:2])
```
