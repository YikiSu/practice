Location: https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/
# Question
You are given an array of characters letters that is sorted in non-decreasing order, and a character target. There are at least two different characters in letters.

Return the smallest character in letters that is lexicographically greater than target. If such a character does not exist, return the first character in letters.
# Example

## Example 1:

Input: letters = ["c","f","j"], target = "a"

Output: "c"

Explanation: The smallest character that is lexicographically greater than 'a' in letters is 'c'.

## Example 2:

Input: letters = ["c","f","j"], target = "c"

Output: "f"

Explanation: The smallest character that is lexicographically greater than 'c' in letters is 'f'.

## Example 3:

Input: letters = ["x","x","y","y"], target = "z"

Output: "x"

Explanation: There are no characters in letters that is lexicographically greater than 'z' so we return letters[0].
## Constraints:

2 <= letters.length <= 104\
letters[i] is a lowercase English letter.\
letters is sorted in non-decreasing order.\
letters contains at least two different characters.\
target is a lowercase English letter.

# My solution (follow instructions)
```python
class Solution(object):
    def nextGreatestLetter(self, letters, target):
        """
        :type letters: List[str]
        :type target: str
        :rtype: str
        """
        # stack = set(letters)
        # stack.add(target)
        # stack = sorted(stack)
        # print(stack)
        # for ind, l in enumerate(stack):
        #     if l == target:
        #         if ind == len(stack)-1:
        #             return letters[0]
        #         else:
        #             return stack[ind+1]
        l, r = 0, len(letters)-1
        while l <= r:
            mid = l + (r-l)//2
            if letters[mid] <= target:
                l = mid + 1
            else:
                r = mid-1
        return letters[l] if l < len(letters) else letters[0]
      
```
