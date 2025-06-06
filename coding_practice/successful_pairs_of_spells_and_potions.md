Location: https://leetcode.com/problems/successful-pairs-of-spells-and-potions/description/?envType=study-plan-v2&envId=leetcode-75
# Question
You are given two positive integer arrays spells and potions, of length n and m respectively, where spells[i] represents the strength of the ith spell and potions[j] represents the strength of the jth potion.

You are also given an integer success. A spell and potion pair is considered successful if the product of their strengths is at least success.

Return an integer array pairs of length n where pairs[i] is the number of potions that will form a successful pair with the ith spell.

# Example
## Example 1:

Input: spells = [5,1,3], potions = [1,2,3,4,5], success = 7

Output: [4,0,3]

Explanation: 
</br>- 0th spell: 5 * [1,2,3,4,5] = [5,10,15,20,25]. 4 pairs are successful.
</br>- 1st spell: 1 * [1,2,3,4,5] = [1,2,3,4,5]. 0 pairs are successful.
</br>- 2nd spell: 3 * [1,2,3,4,5] = [3,6,9,12,15]. 3 pairs are successful.
</br>Thus, [4,0,3] is returned.
## Example 2:

Input: spells = [3,1,2], potions = [8,5,8], success = 16

Output: [2,0,2]

Explanation: 
</br>- 0th spell: 3 * [8,5,8] = [24,15,24]. 2 pairs are successful.
</br>- 1st spell: 1 * [8,5,8] = [8,5,8]. 0 pairs are successful. 
</br>- 2nd spell: 2 * [8,5,8] = [16,10,16]. 2 pairs are successful. 
</br>Thus, [2,0,2] is returned.

Constraints:

- n == spells.length
- m == potions.length
- 1 <= n, m <= 105
- 1 <= spells[i], potions[i] <= 105
- 1 <= success <= 1010
  
# My solution (exceeds time limit, follows instructions)
```python
class Solution(object):
import numpy as np
class Solution(object):
    def successfulPairs(self, spells, potions, success):
        """
        :type spells: List[int]
        :type potions: List[int]
        :type success: int
        :rtype: List[int]
        """
        n = len(spells)
        m = len(potions)
        ans = [0] * n
        potions.sort()
        for i in range(n):
            spell = spells[i]
            left = 0
            right = m - 1
            while left <= right:
                mid = left + (right-left)//2
                pro = spell * potions[mid]
                if pro >= success:
                    right = mid - 1
                else:
                    left = mid + 1
            ans[i] = m-left
        return ans
```
