Location: https://leetcode.com/problems/camelcase-matching/description/
# Question
Given an array of strings queries and a string pattern, return a boolean array answer where answer[i] is true if queries[i] matches pattern, and false otherwise.

A query word queries[i] matches pattern if you can insert lowercase English letters into the pattern so that it equals the query. You may insert a character at any position in pattern or you may choose not to insert any characters at all.
 
# Example

## Example 1:

Input: queries = ["FooBar","FooBarTest","FootBall","FrameBuffer","ForceFeedBack"], pattern = "FB"

Output: [true,false,true,true,false]

Explanation: "FooBar" can be generated like this "F" + "oo" + "B" + "ar".\
"FootBall" can be generated like this "F" + "oot" + "B" + "all".\
"FrameBuffer" can be generated like this "F" + "rame" + "B" + "uffer".

## Example 2:

Input: queries = ["FooBar","FooBarTest","FootBall","FrameBuffer","ForceFeedBack"], pattern = "FoBa"

Output: [true,false,true,false,false]

Explanation: "FooBar" can be generated like this "Fo" + "o" + "Ba" + "r".\
"FootBall" can be generated like this "Fo" + "ot" + "Ba" + "ll".

## Example 3:

Input: queries = ["FooBar","FooBarTest","FootBall","FrameBuffer","ForceFeedBack"], pattern = "FoBaT"

Output: [false,true,false,false,false]

Explanation: "FooBarTest" can be generated like this "Fo" + "o" + "Ba" + "r" + "T" + "est".
 

## Constraints:

1 <= pattern.length, queries.length <= 100\
1 <= queries[i].length <= 100\
queries[i] and pattern consist of English letters.
 

# My solution 
```python
class Solution(object):
    def camelMatch(self, queries, pattern):
        """
        :type queries: List[str]
        :type pattern: str
        :rtype: List[bool]
        """
        ans = []
        for i, word in enumerate(queries):
            # print(word)
            ind = 0
            for st in word:
                # print(st)
                if ind < len(pattern) and st == pattern[ind]:
                    ind += 1
                elif st.isupper():
                    ans.append(False)
                    break
            #     print(ind)
            # print(ans)
            if len(ans) != i+1:
                if ind != len(pattern):
                    ans.append(False)
                else:
                    ans.append(True)
        return ans
        
```
