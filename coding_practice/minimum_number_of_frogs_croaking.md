Location: https://leetcode.com/problems/minimum-number-of-frogs-croaking/description/
# Question
You are given the string croakOfFrogs, which represents a combination of the string "croak" from different frogs, that is, multiple frogs can croak at the same time, so multiple "croak" are mixed.

Return the minimum number of different frogs to finish all the croaks in the given string.

A valid "croak" means a frog is printing five letters 'c', 'r', 'o', 'a', and 'k' sequentially. The frogs have to print all five letters to finish a croak. If the given string is not a combination of a valid "croak" return -1.
# Example

## Example 1:

Input: croakOfFrogs = "croakcroak"

Output: 1 

Explanation: One frog yelling "croak" twice.

## Example 2:

Input: croakOfFrogs = "crcoakroak"

Output: 2 

Explanation: The minimum number of frogs is two. \
The first frog could yell "crcoakroak".\
The second frog could yell later "crcoakroak".

## Example 3:

Input: croakOfFrogs = "croakcrook"

Output: -1

Explanation: The given string is an invalid combination of "croak" from different frogs.
 

Constraints:

1 <= croakOfFrogs.length <= 105\
croakOfFrogs is either 'c', 'r', 'o', 'a', or 'k'.
 

# My solution (follows hints on ChatGPT)
```python
import collections
class Solution(object):
    def minNumberOfFrogs(self, croakOfFrogs):
        """
        :type croakOfFrogs: str
        :rtype: int
        """
        curr = ""
        mapping = {
            'c':"",
            'r':'c',
            'o':'cr',
            'a':'cro',
            'k':'croa'
        }
        connections = {
            "":0,
            'c':0,
            'cr':0,
            'cro':0,
            'croa':0,
            'croak':0
        }
        c_cnt = 0
        active_frogs = 0
        for ind, st in enumerate(croakOfFrogs):
            if st == "c":
                c_cnt += 1
                if c_cnt > active_frogs:
                    active_frogs += 1
            if curr == mapping[st]:
                curr += st
            else:
                connections[curr] += 1
                curr = ""
                if curr == mapping[st]:
                    curr += st
                else:
                    if connections[mapping[st]] > 0:
                        connections[curr] += 1
                        curr = mapping[st] + st
                        connections[mapping[st]] -= 1
                    else:
                        return -1
            if curr == "croak":
                if c_cnt > active_frogs:
                    active_frogs += 1
                c_cnt -= 1
            if ind == len(croakOfFrogs) - 1 and curr != 'croak':
                connections[curr] += 1
        for key, value in connections.items():
            if value > 0 and key != "" and key!="croak":
                return -1
        return active_frogs
        
```
