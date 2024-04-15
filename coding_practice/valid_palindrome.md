Location: https://leetcode.com/problems/valid-palindrome/
# Question
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

# Example
## Example 1:

Input: s = "A man, a plan, a canal: Panama"

Output: true

Explanation: "amanaplanacanalpanama" is a palindrome.

## Example 2:

Input: s = "race a car"

Output: false

Explanation: "raceacar" is not a palindrome.

## Example 3:

Input: s = " "

Output: true

Explanation: s is an empty string "" after removing non-alphanumeric characters. Since an empty string reads the same forward and backward, it is a palindrome.

# My solution
```python
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        s = "".join([st for st in s if st.isalnum()]).lower()
        if len(s) == 0:
            return True
        first = 0
        last = len(s) - 1
        while first < last:
            if s[first] != s[last]:
                return False
            else:
                first += 1
                last -= 1
        return True
```

# Best solution
```python
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        p = re.sub('[^a-z0-9]', '', s.lower())
        # print(p)
        return p == p[::-1]
```
