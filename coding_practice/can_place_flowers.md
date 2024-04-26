Location: https://leetcode.com/problems/can-place-flowers/description/?envType=study-plan-v2&envId=leetcode-75

# Question
You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, return true if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule and false otherwise.

# Example

## Example 1:

Input: flowerbed = [1,0,0,0,1], n = 1\
Output: true
## Example 2:

Input: flowerbed = [1,0,0,0,1], n = 2\
Output: false

# My solution
```python
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        starting = 0
        fl = n
        if len(flowerbed) == 1:
            return flowerbed.count(0) >= n
        while starting < len(flowerbed) and fl>0:
            if flowerbed[starting] == 0:
                if starting == 0:
                    if flowerbed[starting+1] == 0:
                        flowerbed[starting]=1
                        fl -= 1
                    else:
                        starting += 1
                elif starting == len(flowerbed)-1:
                    if flowerbed[starting-1] == 0:
                        fl -= 1
                    return fl == 0
                else:
                    if flowerbed[starting+1] == 0 and flowerbed[starting-1] == 0:
                        flowerbed[starting] = 1
                        fl -= 1
                    else:
                        starting += 1
            else:
                starting += 1
        return fl == 0

```

# Fastest solution
```python
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        if n == 0:
            return True
        for i in range(len(flowerbed)):
            if flowerbed[i] == 0 and (i == 0 or flowerbed[i-1] == 0) and (i == len(flowerbed)-1 or flowerbed[i+1] == 0):
                flowerbed[i] = 1
                n -= 1
                if n == 0:
                    return True
        return False
```
