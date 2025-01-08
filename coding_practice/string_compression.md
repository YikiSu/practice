Location: https://leetcode.com/problems/string-compression/description/?envType=study-plan-v2&envId=leetcode-75
# Question
Given an array of characters chars, compress it using the following algorithm:

Begin with an empty string s. For each group of consecutive repeating characters in chars:

- If the group's length is 1, append the character to s.
- Otherwise, append the character followed by the group's length.
- 
The compressed string s should not be returned separately, but instead, be stored in the input character array chars. Note that group lengths that are 10 or longer will be split into multiple characters in chars.

After you are done modifying the input array, return the new length of the array.

You must write an algorithm that uses only constant extra space.

 
# Example

## Example 1:

Input: chars = ["a","a","b","b","c","c","c"]

Output: Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]

Explanation: The groups are "aa", "bb", and "ccc". This compresses to "a2b2c3".

## Example 2:

Input: chars = ["a"]

Output: Return 1, and the first character of the input array should be: ["a"]

Explanation: The only group is "a", which remains uncompressed since it's a single character.

## Example 3:

Input: chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]

Output: Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].

Explanation: The groups are "a" and "bbbbbbbbbbbb". This compresses to "ab12".
 

Constraints:

1 <= chars.length <= 2000

chars[i] is a lowercase English letter, uppercase English letter, digit, or symbol.
 

# My solution (follows instructions on solutions)
```python
class Solution(object):
    def compress(self, chars):
        """
        :type chars: List[str]
        :rtype: int
        """
        if len(chars) == 1:
            return 1
        res = ""
        anchor = 0
        moving = 0
        cnt = 0
        while moving < len(chars):
            if chars[anchor] == chars[moving]:
                if res == "":
                    res += chars[moving]
                cnt += 1
                moving += 1
            else:
                if cnt != 1:
                    res += str(cnt)
                anchor = moving
                res += chars[moving]
                cnt = 1
                moving += 1
        if cnt != 1:
            res += str(cnt)
        chars[:] = [s for s in res]
        return len(res)
```
