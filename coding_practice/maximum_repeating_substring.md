Location: https://leetcode.com/problems/maximum-repeating-substring/description/?envType=problem-list-v2&envId=dynamic-programming

# Question
For a string sequence, a string word is k-repeating if word concatenated k times is a substring of sequence. The word's maximum k-repeating value is the highest value k where word is k-repeating in sequence. If word is not a substring of sequence, word's maximum k-repeating value is 0.

Given strings sequence and word, return the maximum k-repeating value of word in sequence.

# Example

## Example 1:

Input: sequence = "ababc", word = "ab"\
Output: 2\
Explanation: "abab" is a substring in "ababc".
## Example 2:

Input: sequence = "ababc", word = "ba"\
Output: 1\
Explanation: "ba" is a substring in "ababc". "baba" is not a substring in "ababc".

## Example 3:

Input: sequence = "ababc", word = "ac"\
Output: 0\
Explanation: "ac" is not a substring in "ababc". 

# My solution (follow solutions of others)
```python
class Solution(object):
    def maxRepeating(self, sequence, word):
        """
        :type sequence: str
        :type word: str
        :rtype: int
        """
        # starting = 0
        # ans = 0
        # while starting < len(sequence):
        #     if sequence[starting] == word[0]:
        #         if sequence[starting:starting+len(word)] == word:
        #             ans += 1
        #             starting = starting+len(word)
        #         else:
        #             starting += 1
        #     else:
        #         starting += 1
        # return ans
        ans = 0
        while True:
            if word*(ans+1) not in sequence:
                return ans
            ans += 1
        return ans

```

