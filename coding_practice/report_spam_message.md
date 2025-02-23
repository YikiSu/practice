Location: https://leetcode.com/problems/report-spam-message/description/
# Question
You are given an array of strings message and an array of strings bannedWords.

An array of words is considered spam if there are at least two words in it that exactly match any word in bannedWords.

Return true if the array message is spam, and false otherwise.
 
# Example

## Example 1:

Input: message = ["hello","world","leetcode"], bannedWords = ["world","hello"]

Output: true

Explanation:

The words "hello" and "world" from the message array both appear in the bannedWords array.

## Example 2:

Input: message = ["hello","programming","fun"], bannedWords = ["world","programming","leetcode"]

Output: false

Explanation:

Only one word from the message array ("programming") appears in the bannedWords array.

Constraints:

1 <= message.length, bannedWords.length <= 105\
1 <= message[i].length, bannedWords[i].length <= 15\
message[i] and bannedWords[i] consist only of lowercase English letters.
 

# My solution 
```python
import collections
class Solution(object):
    def reportSpam(self, message, bannedWords):
        """
        :type message: List[str]
        :type bannedWords: List[str]
        :rtype: bool
        """
        m_cnt = collections.Counter(message)
        b_cnt = collections.Counter(bannedWords)
        ans = 0
        for s, cnt in m_cnt.items():
            if b_cnt[s] and cnt >= 2:
                return True
            elif b_cnt[s]:
                ans += 1
                if ans >= 2:
                    return True
        return False
                
```
