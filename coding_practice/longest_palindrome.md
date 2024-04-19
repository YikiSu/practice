Location: https://leetcode.com/problems/longest-palindrome/
# Question
Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.

Letters are case sensitive, for example, "Aa" is not considered a palindrome here.

 # Example

## Example 1:

Input: s = "abccccdd"

Output: 7

Explanation: One longest palindrome that can be built is "dccaccd", whose length is 7.

## Example 2:

Input: s = "a"
Output: 1
Explanation: The longest palindrome that can be built is "a", whose length is 1.

# My solution
```python
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: int
        """
        counts = collections.Counter(s)
        two_num = 0
        one_num = 0
        for l in s:
            if counts[l] > 1:
                two_num += 2
                counts[l] -= 2
            elif counts[l]>0 and one_num == 0:
                one_num += 1
        return two_num + one_num
```

# Fastest solution
```python
class Solution(object):
    def longestPalindrome(self, s):
        
        mapi={}
        for i in s:
            if i in mapi:
                mapi[i]+=1
            else:
                mapi[i]=1
        letters=0
        flag=True
        for i in mapi:
            if mapi[i]%2==0:
                letters+=mapi[i]
            elif mapi[i]%2!=0 and flag:
                letters+=mapi[i]
                flag=False
            else:
                letters+=mapi[i]-1
        return letters

```
