Location: https://leetcode.com/problems/uncommon-words-from-two-sentences/description/
# Question
A sentence is a string of single-space separated words where each word consists only of lowercase letters.

A word is uncommon if it appears exactly once in one of the sentences, and does not appear in the other sentence.

Given two sentences s1 and s2, return a list of all the uncommon words. You may return the answer in any order.

 
# Example

## Example 1:

Input: s1 = "this apple is sweet", s2 = "this apple is sour"

Output: ["sweet","sour"]

Explanation:

The word "sweet" appears only in s1, while the word "sour" appears only in s2.

## Example 2:

Input: s1 = "apple apple", s2 = "banana"

Output: ["banana"]

## Constraints:

1 <= s1.length, s2.length <= 200\
s1 and s2 consist of lowercase English letters and spaces.\
s1 and s2 do not have leading or trailing spaces.\
All the words in s1 and s2 are separated by a single space.
 

# My solution 
```python
import collections
class Solution(object):
    def uncommonFromSentences(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: List[str]
        """
        cnt1 = collections.Counter(s1.split())
        cnt2 = collections.Counter(s2.split())
        inters = set(cnt1.keys()).intersection(set(cnt2.keys()))
        curr = [w for w, c in cnt1.items() if c == 1] + [w for w, c in cnt2.items() if c == 1]
        return [word for word in curr if word not in inters]
```
