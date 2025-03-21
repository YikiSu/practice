Location: https://leetcode.com/problems/most-common-word/description/?envType=problem-list-v2&envId=hash-table
# Question
Given a string paragraph and a string array of the banned words banned, return the most frequent word that is not banned. It is guaranteed there is at least one word that is not banned, and that the answer is unique.

The words in paragraph are case-insensitive and the answer should be returned in lowercase.
# Example

## Example 1:

Input: paragraph = "Bob hit a ball, the hit BALL flew far after it was hit.", banned = ["hit"]

Output: "ball"

Explanation: \
"hit" occurs 3 times, but it is a banned word.\
"ball" occurs twice (and no other word does), so it is the most frequent non-banned word in the paragraph. \
Note that words in the paragraph are not case sensitive,\
that punctuation is ignored (even if adjacent to words, such as "ball,"), \
and that "hit" isn't the answer even though it occurs more because it is banned.

## Example 2:

Input: paragraph = "a.", banned = []

Output: "a"

## Constraints:

1 <= paragraph.length <= 1000\
paragraph consists of English letters, space ' ', or one of the symbols: "!?',;.".\
0 <= banned.length <= 100\
1 <= banned[i].length <= 10\
banned[i] consists of only lowercase English letters.
 

# My solution (follows instructions on solutions)
```python
import collections
import re
class Solution(object):
    def mostCommonWord(self, paragraph, banned):
        """
        :type paragraph: str
        :type banned: List[str]
        :rtype: str
        """
        cnt = collections.Counter([st.lower().replace("!","").replace("?","").replace("'","").replace(",","").replace(";","").replace(".","") for st in re.findall(r'\b\w+\b', paragraph.lower())])
        # print(cnt)
        # print(sorted(cnt, key=cnt.get, reverse=True))
        for key in sorted(cnt, key=cnt.get, reverse=True):
            if key not in banned:
                return key
        
```
