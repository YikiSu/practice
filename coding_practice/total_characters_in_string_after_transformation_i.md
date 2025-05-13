Location: https://leetcode.com/problems/total-characters-in-string-after-transformations-i/description/?envType=daily-question&envId=2025-05-13
# Question
You are given a string s and an integer t, representing the number of transformations to perform. In one transformation, every character in s is replaced according to the following rules:

If the character is 'z', replace it with the string "ab".
Otherwise, replace it with the next character in the alphabet. For example, 'a' is replaced with 'b', 'b' is replaced with 'c', and so on.
Return the length of the resulting string after exactly t transformations.

Since the answer may be very large, return it modulo 109 + 7.

 
# Example

## Example 1:

Input: s = "abcyy", t = 2

Output: 7

Explanation:

First Transformation (t = 1):\
'a' becomes 'b'\
'b' becomes 'c'\
'c' becomes 'd'\
'y' becomes 'z'\
'y' becomes 'z'\
String after the first transformation: "bcdzz"\
Second Transformation (t = 2):\
'b' becomes 'c'\
'c' becomes 'd'\
'd' becomes 'e'\
'z' becomes "ab"\
'z' becomes "ab"\
String after the second transformation: "cdeabab"\
Final Length of the string: The string is "cdeabab", which has 7 characters.

## Example 2:

Input: s = "azbk", t = 1

Output: 5

Explanation:

First Transformation (t = 1):\
'a' becomes 'b'\
'z' becomes "ab"\
'b' becomes 'c'\
'k' becomes 'l'\
String after the first transformation: "babcl"\
Final Length of the string: The string is "babcl", which has 5 characters.

## Constraints:

1 <= s.length <= 105\
s consists only of lowercase English letters.\
1 <= t <= 105
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def lengthAfterTransformations(self, s, t):
        """
        :type s: str
        :type t: int
        :rtype: int
        """
        # cnt = collections.Counter(s)
        # for _ in range(t):
        #     curr = collections.defaultdict(int)
        #     for key,val in cnt.items():
        #         if key != "z":
        #             # curr[chr(ord(key)+1)] += val
        #             curr[chr(ord(key)+1)] = (curr[chr(ord(key)+1)]+val)%(10**9 + 7)
        #         else:
        #             curr['a'] = (curr["a"]+val)%(10**9 + 7)
        #             curr['b'] = (curr["b"]+val)%(10**9 + 7)
        #     cnt = curr
        # return sum(cnt.values())%(10**9 + 7)
        freq = [0] * 26
        MOD = 10**9 + 7
        for c in s:
            freq[ord(c) - ord('a')] += 1
        
        for _ in range(t):
            new_freq = [0] * 26
            # Handle 'z' -> 'a' + 'b'
            new_freq[0] = (new_freq[0] + freq[25]) % MOD
            new_freq[1] = (new_freq[1] + freq[25]) % MOD
            # Handle other letters: 'a' -> 'b', 'b' -> 'c', ..., 'y' -> 'z'
            for i in range(25):
                new_freq[i + 1] = (new_freq[i + 1] + freq[i]) % MOD
            freq = new_freq
        
        return sum(freq) % MOD
```
