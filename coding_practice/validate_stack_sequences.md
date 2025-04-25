Location: https://leetcode.com/problems/validate-stack-sequences/description/?envType=problem-list-v2&envId=stack&
# Question
Given two integer arrays pushed and popped each with distinct values, return true if this could have been the result of a sequence of push and pop operations on an initially empty stack, or false otherwise.

 
# Example

## Example 1:

Input: pushed = [1,2,3,4,5], popped = [4,5,3,2,1]

Output: true

Explanation: We might do the following sequence:\
push(1), push(2), push(3), push(4),\
pop() -> 4,\
push(5),\
pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1

## Example 2:

Input: pushed = [1,2,3,4,5], popped = [4,3,5,1,2]

Output: false

Explanation: 1 cannot be popped before 2.

## Constraints:

1 <= pushed.length <= 1000\
0 <= pushed[i] <= 1000\
All the elements of pushed are unique.\
popped.length == pushed.length\
popped is a permutation of pushed.
 

# My solution 
```python
class Solution(object):
    def validateStackSequences(self, pushed, popped):
        """
        :type pushed: List[int]
        :type popped: List[int]
        :rtype: bool
        """
        stack = []
        while pushed:
            # print(pushed)
            if popped[0] == pushed[0]:
                # print('here')
                popped.pop(0)
                pushed.pop(0)
            elif stack and popped[0] == stack[-1]:
                # print('there')
                popped.pop(0)
                stack.pop(-1)
            else:
                # print('this')
                stack.append(pushed.pop(0))
            # print(stack)
        while popped:
            if popped[0] == stack[-1]:
                popped.pop(0)
                stack.pop(-1)
            else:
                return False
        if not stack and not popped:
            return True
        else:
            return False
```
