Location: https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/description/
# Question
You are given an array of strings words and a string chars.

A string is good if it can be formed by characters from chars (each character can only be used once).

Return the sum of lengths of all good strings in words.

 
# Example

## Example 1:

Input: words = ["cat","bt","hat","tree"], chars = "atach"

Output: 6

Explanation: The strings that can be formed are "cat" and "hat" so the answer is 3 + 3 = 6.

## Example 2:

Input: words = ["hello","world","leetcode"], chars = "welldonehoneyr"

Output: 10

Explanation: The strings that can be formed are "hello" and "world" so the answer is 5 + 5 = 10.

## Constraints:

1 <= words.length <= 1000\
1 <= words[i].length, chars.length <= 100\
words[i] and chars consist of lowercase English letters.

# My solution 
```python
import collections
class Solution(object):
    def countCharacters(self, words, chars):
        """
        :type words: List[str]
        :type chars: str
        :rtype: int
        """
        ans = 0
        cnt = collections.Counter(chars)
        for word in words:
            curr = collections.Counter(word)
            good = True
            for key, val in curr.items():
                if cnt[key] < val:
                    good = False
                    break
            if good:
                ans += len(word)
        return ans

```
