Location: https://leetcode.com/problems/word-subsets/description/?envType=daily-question&envId=2025-04-24
# Question
You are given two string arrays words1 and words2.

A string b is a subset of string a if every letter in b occurs in a including multiplicity.

For example, "wrr" is a subset of "warrior" but is not a subset of "world".

A string a from words1 is universal if for every string b in words2, b is a subset of a.

Return an array of all the universal strings in words1. You may return the answer in any order.

 
# Example

## Example 1:

Input: words1 = ["amazon","apple","facebook","google","leetcode"], words2 = ["e","o"]

Output: ["facebook","google","leetcode"]

## Example 2:

Input: words1 = ["amazon","apple","facebook","google","leetcode"], words2 = ["lc","eo"]

Output: ["leetcode"]

## Example 3:

Input: words1 = ["acaac","cccbb","aacbb","caacc","bcbbb"], words2 = ["c","cc","b"]

Output: ["cccbb"]
 

## Constraints:

1 <= words1.length, words2.length <= 104\
1 <= words1[i].length, words2[i].length <= 10\
words1[i] and words2[i] consist only of lowercase English letters.\
All the strings of words1 are unique.
 

# My solution 
```python
import collections
class Solution(object):
    def wordSubsets(self, words1, words2):
        """
        :type words1: List[str]
        :type words2: List[str]
        :rtype: List[str]
        """
        cnt2 = collections.defaultdict(int)
        for word in words2:
            curr = collections.defaultdict(int)
            for st in word:
                curr[st] += 1
            for key, val in curr.items():
                if key not in cnt2:
                    cnt2[key] = val
                else:
                    cnt2[key] = max(cnt2[key], val)
        # print(cnt2)
        ans = []
        for word in words1:
            # print(word)
            include = True
            for key, val in cnt2.items():
                if key not in word or word.count(key)<val:
                    # print(key)
                    # print(word.count(key))
                    include = False
                    break
            if include:
                ans.append(word)
        return ans
```
