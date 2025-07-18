Location: https://leetcode.com/problems/divide-players-into-teams-of-equal-skill/description/
# Question
You are given a positive integer array skill of even length n where skill[i] denotes the skill of the ith player. Divide the players into n / 2 teams of size 2 such that the total skill of each team is equal.

The chemistry of a team is equal to the product of the skills of the players on that team.

Return the sum of the chemistry of all the teams, or return -1 if there is no way to divide the players into teams such that the total skill of each team is equal.

 
# Example

## Example 1:

Input: skill = [3,2,5,1,3,4]

Output: 22

Explanation: \
Divide the players into the following teams: (1, 5), (2, 4), (3, 3), where each team has a total skill of 6.\
The sum of the chemistry of all the teams is: 1 * 5 + 2 * 4 + 3 * 3 = 5 + 8 + 9 = 22.

## Example 2:

Input: skill = [3,4]

Output: 12

Explanation: \
The two players form a team with a total skill of 7.\
The chemistry of the team is 3 * 4 = 12.

## Example 3:

Input: skill = [1,1,2,3]

Output: -1

Explanation: \
There is no way to divide the players into teams such that the total skill of each team is equal.
 

## Constraints:

2 <= skill.length <= 105\
skill.length is even.\
1 <= skill[i] <= 1000
 

# My solution 
```python
class Solution(object):
    def dividePlayers(self, skill):
        """
        :type skill: List[int]
        :rtype: int
        """
        skill = sorted(skill)
        curr = skill[0]+skill[-1]
        ans = skill[0]*skill[-1]
        l,r = 1, len(skill)-2
        while l<r:
            if skill[l]+skill[r] != curr:
                return -1
            else:
                ans += skill[l]*skill[r]
            l += 1
            r -= 1
        return ans
```
