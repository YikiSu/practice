Location: https://leetcode.com/problems/group-anagrams/description/?envType=problem-list-v2&envId=hash-table
# Question
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

# Example

## Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

Explanation: 
- There is no string in strs that can be rearranged to form "bat".
- The strings "nat" and "tan" are anagrams as they can be rearranged to form each other.
- The strings "ate", "eat", and "tea" are anagrams as they can be rearranged to form each other.

## Example 2:

Input: strs = [""]

Output: [[""]]


## Example 3:

Input: strs = ["a"]

Output: [["a"]]
 

Constraints:

1 <= strs.length <= 104\
0 <= strs[i].length <= 100\
strs[i] consists of lowercase English letters.
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        if len(strs) == 1: return [strs]
        ans = collections.defaultdict(list)
        for st in strs:
            checked_ = "".join(sorted(st))
            if checked_ not in ans.keys():
                ans[checked_] = [st]
            else:
                ans[checked_].append(st)
            
        return [value for key, value in ans.items()]
                
```
