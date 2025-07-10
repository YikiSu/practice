Location: https://leetcode.com/problems/detect-capital/description/
# Question
We define the usage of capitals in a word to be right when one of the following cases holds:

- All letters in this word are capitals, like "USA".
- All letters in this word are not capitals, like "leetcode".
- Only the first letter in this word is capital, like "Google".

Given a string word, return true if the usage of capitals in it is right.
 
# Example

## Example 1:

Input: word = "USA"

Output: true

## Example 2:

Input: word = "FlaG"

Output: false

## Constraints:

1 <= word.length <= 100\
word consists of lowercase and uppercase English letters.
 

# My solution 
```python
class Solution(object):
    def detectCapitalUse(self, word):
        """
        :type word: str
        :rtype: bool
        """
        first = False
        other_c = False
        other_l = False
        all_l = False
        for ind, w in enumerate(word):
            if ind == 0 and w.isupper():
                first = True
            elif ind == 0 and w.islower():
                all_l = True
            elif w.isupper():
                if first and ind==1:
                    other_c = True
                elif first and other_c:
                    continue
                else:
                    return False
            elif w.islower():
                if ind == 1 and first:
                    other_l = True
                elif (first and other_l) or all_l:
                    continue
                else:
                    return False
            else:
                return False
        return True

```
