Location: https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/description/
# Question
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

 
# Example

## Example 1:

Input: s1 = "bank", s2 = "kanb"

Output: true

Explanation: For example, swap the first character with the last character of s2 to make "bank".

## Example 2:

Input: s1 = "attack", s2 = "defend"

Output: false

Explanation: It is impossible to make them equal with one string swap.

## Example 3:

Input: s1 = "kelb", s2 = "kelb"

Output: true

Explanation: The two strings are already equal, so no string swap operation is required.

## Constraints:

1 <= s1.length, s2.length <= 100\
s1.length == s2.length\
s1 and s2 consist of only lowercase English letters.
 

# My solution
```python
class Solution(object):
    def areAlmostEqual(self, s1, s2):
        """
        :type s1: str
        :type s2: str
        :rtype: bool
        """
        st = {}
        ans = 0
        for i in range(len(s1)):
            if s1[i] != s2[i]:
                if s2[i] not in st.keys():
                    st[s1[i]] = s2[i]
                elif s2[i] in st.keys() and st[s2[i]]==s1[i]:
                    ans += 1
                    st.pop(s2[i])
            if ans > 1:
                return False
        # print(ans)
        # print(st)
        return ans <= 1 and len(st) == 0
```
