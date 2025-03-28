Location: https://leetcode.com/problems/determine-if-two-strings-are-close/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Two strings are considered close if you can attain one from the other using the following operations:

- Operation 1: Swap any two existing characters.
</br>For example, abcde -> aecdb
- Operation 2: Transform every occurrence of one existing character into another existing character, and do the same with the other character.
</br>For example, aacabb -> bbcbaa (all a's turn into b's, and all b's turn into a's)
You can use the operations on either string as many times as necessary.

Given two strings, word1 and word2, return true if word1 and word2 are close, and false otherwise.

 
# Example

## Example 1:

Input:  word1 = "abc", word2 = "bca"

Output: true

Explanation: You can attain word2 from word1 in 2 operations.
</br>Apply Operation 1: "abc" -> "acb"
</br>Apply Operation 1: "acb" -> "bca"

## Example 2:

Input:  word1 = "a", word2 = "aa"

Output: false

Explanation: It is impossible to attain word2 from word1, or vice versa, in any number of operations.

## Example 3:

Input: word1 = "cabbba", word2 = "abbccc"

Output: true

Explanation: 
</br>You can attain word2 from word1 in 3 operations.
</br>Apply Operation 1: "cabbba" -> "caabbb"
</br>Apply Operation 2: "caabbb" -> "baaccc"
</br>Apply Operation 2: "baaccc" -> "abbccc"
 
 

Constraints:

- 1 <= nums.length <= 104
- -1000 <= nums[i] <= 1000
 

# My solution 
```python
import collections
class Solution(object):
    def closeStrings(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: bool
        """
        if len(word2) > len(word1):
            return False
        cnt1 = collections.Counter(word1)
        cnt2 = collections.Counter(word2)
        return sorted(cnt1.values()) == sorted(cnt2.values()) and sorted(cnt1.keys())==sorted(cnt2.keys())
        
```
