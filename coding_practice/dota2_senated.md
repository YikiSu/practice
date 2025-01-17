Location: https://leetcode.com/problems/dota2-senate/description/?envType=study-plan-v2&envId=leetcode-75
# Question
In the world of Dota2, there are two parties: the Radiant and the Dire.

The Dota2 senate consists of senators coming from two parties. Now the Senate wants to decide on a change in the Dota2 game. The voting for this change is a round-based procedure. In each round, each senator can exercise one of the two rights:

- Ban one senator's right: A senator can make another senator lose all his rights in this and all the following rounds.
- Announce the victory: If this senator found the senators who still have rights to vote are all from the same party, he can announce the victory and decide on the change in the game.
Given a string senate representing each senator's party belonging. The character 'R' and 'D' represent the Radiant party and the Dire party. Then if there are n senators, the size of the given string will be n.

The round-based procedure starts from the first senator to the last senator in the given order. This procedure will last until the end of voting. All the senators who have lost their rights will be skipped during the procedure.

Suppose every senator is smart enough and will play the best strategy for his own party. Predict which party will finally announce the victory and change the Dota2 game. The output should be "Radiant" or "Dire".

# Example
## Example 1:

senate = "RD"

Output: "Radiant"

Explanation: 
</br>The first senator comes from Radiant and he can just ban the next senator's right in round 1. 
</br>And the second senator can't exercise any rights anymore since his right has been banned. 
</br>And in round 2, the first senator can just announce the victory since he is the only guy in the senate who can vote.
## Example 2:

Input: senate = "RDD"

Output: "Dire"

Explanation: 
</br>The first senator comes from Radiant and he can just ban the next senator's right in round 1. 
</br>And the second senator can't exercise any rights anymore since his right has been banned. 
</br>And the third senator comes from Dire and he can ban the first senator's right in round 1. 
</br>And in round 2, the third senator can just announce the victory since he is the only guy in the senate who can vote.

# My solution (follows instructions)
```python
class Solution(object):
    def predictPartyVictory(self, senate):
        """
        :type senate: str
        :rtype: str
        """
        r_ban = 0
        d_ban = 0
        s_ = set()
        banned = [False]*len(senate)
        while len(s_) != 1:
            s_ = set()
            for ind, s in enumerate(senate):
                if banned[ind]:
                    continue
                if s == "R":
                    if r_ban > 0:
                        r_ban -= 1
                        banned[ind] = True
                    else:
                        d_ban += 1
                        s_.add("R")
                else:
                    if d_ban > 0:
                        d_ban -= 1
                        banned[ind] = True
                    else:
                        r_ban += 1
                        s_.add("D")
        return "Radiant" if s_.pop() == "R" else "Dire"
```
