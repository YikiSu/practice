Location: https://leetcode.com/problems/merge-strings-alternately/?envType=study-plan-v2&envId=leetcode-75

# Question
You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

 # Example

## Example 1:

Input: word1 = "abc", word2 = "pqr"\
Output: "apbqcr"\
Explanation: The merged string will be merged as so:\
word1:  a   b   c\
word2:    p   q   r\
merged: a p b q c r

## Example 2:

Input: word1 = "ab", word2 = "pqrs"\
Output: "apbqrs"\
Explanation: Notice that as word2 is longer, "rs" is appended to the end.\
word1:  a   b \
word2:    p   q   r   s\
merged: a p b q   r   s

## Example 3:

Input: word1 = "abcd", word2 = "pq"\
Output: "apbqcd"\
Explanation: Notice that as word1 is longer, "cd" is appended to the end.\
word1:  a   b   c   d\
word2:    p   q \
merged: a p b q c   d

# My solution
```python
class Solution(object):
    def mergeAlternately(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: str
        """
        length1 = len(word1)
        length2 = len(word2)
        res = ""
        if length1 >= length2:
            for i in range(0, length2):
                res += word1[i]+word2[i]
            try:
                res += word1[length2:]
            except:
                pass
        else:
            for i in range(0, length1):
                res += word1[i]+word2[i]
            try:
                res += word2[length1:]
            except:
                pass
        return res
```

# Fastest solution
```python
class Solution(object):
    def mergeAlternately(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: str
        """
        merged = ""
        i = 0
        for c in list(word1):
            merged += c + (list(word2)[i] if i < len(word2) else "")
            i += 1
            
        if len(word2) > len(word1):
            merged += word2[i:]
        
        return merged
```
