Location: https://leetcode.com/problems/count-of-substrings-containing-every-vowel-and-k-consonants-ii/description/
# Question
You are given a string word and a non-negative integer k.

Return the total number of substrings of word that contain every vowel ('a', 'e', 'i', 'o', and 'u') at least once and exactly k consonants.

 
# Example

## Example 1:

Input: word = "aeioqq", k = 1

Output: 0

Explanation:

There is no substring with every vowel.

## Example 2:

Input: word = "aeiou", k = 0

Output: 1

Explanation:

The only substring with every vowel and zero consonants is word[0..4], which is "aeiou".

## Example 3:

Input: word = "ieaouqqieaouqq", k = 1

Output: 3

Explanation:

The substrings with every vowel and one consonant are:

word[0..5], which is "ieaouq".\
word[6..11], which is "qieaou".\
word[7..12], which is "ieaouq".
 

## Constraints:

5 <= word.length <= 2 * 105\
word consists only of lowercase English letters.\
0 <= k <= word.length - 5
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def countOfSubstrings(self, word, k):
        """
        :type word: str
        :type k: int
        :rtype: int
        """
        res = cons = left = cur = 0
        freq = defaultdict(int)
        vowel = 'aeiou'

        for ch in word:
            # count vowel frequency and number of consonants in the current window
            if ch in vowel:
                freq[ch] += 1
            else: 
                cons += 1
                # reset number of valid substring found in the current window since now it is no more valid
                cur = 0 

            # shrink until we have the right amount of consonants
            while cons > k:
                if word[left] not in vowel:
                    cons -= 1
                elif freq[word[left]] == 1:
                    del freq[word[left]]
                else:
                    freq[word[left]] -= 1
                left += 1

            # if we have the right amount of consonants and vowels, shrink current window as much as possible
            # each step is a probable substring if we keep finding vowels on the right
            while len(freq) == 5 and cons == k:
                cur += 1
                if word[left] not in vowel:
                    cons -= 1
                elif freq[word[left]] == 1:
                    del freq[word[left]]
                else:
                    freq[word[left]] -= 1
                left += 1
            res += cur # sum the overall number of substring in the current window
            
        return res
```
