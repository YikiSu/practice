Location: https://leetcode.com/problems/fruit-into-baskets/description/
# Question
You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

- You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
- Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
- Once you reach a tree with fruit that cannot fit in your baskets, you must stop.

Given the integer array fruits, return the maximum number of fruits you can pick.
# Example

## Example 1:

Input: fruits = [1,2,1]

Output: 3

Explanation: We can pick from all 3 trees.

## Example 2:

Input: fruits = [0,1,2,2]

Output: 3

Explanation: We can pick from trees [1,2,2].\
If we had started at the first tree, we would only pick from trees [0,1].

## Example 3:

Input: fruits = [1,2,3,2,2]

Output: 4

Explanation: We can pick from trees [2,3,2,2].\
If we had started at the first tree, we would only pick from trees [1,2].
 

## Constraints:

1 <= fruits.length <= 105\
0 <= fruits[i] < fruits.length
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def totalFruit(self, fruits):
        """
        :type fruits: List[int]
        :rtype: int
        """
        ans = 0
        left, right = 0, 0
        seen = {}
        while left < len(fruits) and right < len(fruits):
            print(seen)
            if fruits[right] not in seen.keys():
                if len(seen) < 2:
                    seen[fruits[right]] = 1
                    right += 1
                else:
                    ans = max(ans, right-1-left+1)
                    seen[fruits[right]] = 1
                    while len(seen) > 2:
                        seen[fruits[left]] -= 1
                        if seen[fruits[left]] == 0:
                            seen.pop(fruits[left])
                        left += 1
                    right += 1
                        # cnt = seen[fruits[left]]
                        # left += cnt
                        # if right > left:
                        #     seen = collections.Counter(fruits[left:right+1])
                        #     right += 1
                        # else:
                        #     seen = {}
                        #     right = left
            else:
                seen[fruits[right]] += 1
                right += 1
        return max(ans, right-1-left+1)
        
```
