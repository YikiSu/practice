Location: https://leetcode.com/problems/find-common-characters/description/
# Question
Given a string array words, return an array of all characters that show up in all strings within the words (including duplicates). You may return the answer in any order.
# Example

## Example 1:

Input: words = ["bella","label","roller"]

Output: ["e","l","l"]

## Example 2:

Input: words = ["cool","lock","cook"]

Output: ["c","o"]

## Constraints:

1 <= words.length <= 100\
1 <= words[i].length <= 100\
words[i] consists of lowercase English letters.
 

# My solution 
```python
import collections
class Solution(object):
    def commonChars(self, words):
        """
        :type words: List[str]
        :rtype: List[str]
        """
        pre = collections.Counter(words[0])
        for word in words[1:]:
            curr = collections.Counter(word)
            pre = {key:min(val, pre[key]) for key, val in curr.items() if key in pre.keys()}
        # print(pre)
        ans = []
        for key, val in pre.items():
            ans += [key]*val
        return ans
```
