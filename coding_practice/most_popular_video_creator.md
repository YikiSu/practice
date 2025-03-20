Location: https://leetcode.com/problems/most-popular-video-creator/description/
# Question
You are given two string arrays creators and ids, and an integer array views, all of length n. The ith video on a platform was created by creators[i], has an id of ids[i], and has views[i] views.

The popularity of a creator is the sum of the number of views on all of the creator's videos. Find the creator with the highest popularity and the id of their most viewed video.

- If multiple creators have the highest popularity, find all of them.
_ If multiple videos have the highest view count for a creator, find the lexicographically smallest id.

Note: It is possible for different videos to have the same id, meaning that ids do not uniquely identify a video. For example, two videos with the same ID are considered as distinct videos with their own viewcount.

Return a 2D array of strings answer where answer[i] = [creatorsi, idi] means that creatorsi has the highest popularity and idi is the id of their most popular video. The answer can be returned in any order.
 
# Example

## Example 1:

Input: creators = ["alice","bob","alice","chris"], ids = ["one","two","three","four"], views = [5,10,5,4]

Output: [["alice","one"],["bob","two"]]

Explanation:

The popularity of alice is 5 + 5 = 10.\
The popularity of bob is 10.\
The popularity of chris is 4.\
alice and bob are the most popular creators.\
For bob, the video with the highest view count is "two".\
For alice, the videos with the highest view count are "one" and "three". Since "one" is lexicographically smaller than "three", it is included in the answer.

## Example 2:

Input: creators = ["alice","alice","alice"], ids = ["a","b","c"], views = [1,2,2]

Output: [["alice","b"]]

Explanation:

The videos with id "b" and "c" have the highest view count.\
Since "b" is lexicographically smaller than "c", it is included in the answer.

## Constraints:

n == creators.length == ids.length == views.length\
1 <= n <= 105\
1 <= creators[i].length, ids[i].length <= 5\
creators[i] and ids[i] consist only of lowercase English letters.\
0 <= views[i] <= 105
 

# My solution (follows instructions on solutions)
```python
import collections
class Solution(object):
    def mostPopularCreator(self, creators, ids, views):
        """
        :type creators: List[str]
        :type ids: List[str]
        :type views: List[int]
        :rtype: List[List[str]]
        """
        memo = {}
		#tracking the max popular video count
        overall_max_popular_video_count = -1
        #looping over the creators
        for i in range(len(creators)):
            if creators[i] in memo:
                #Step 1: update number of views for the creator
                memo[creators[i]][0] += views[i]
                #Step 2: update current_popular_video_view and id_of_most_popular_video_so_far
                if memo[creators[i]][2] < views[i]:
                    memo[creators[i]][1] = ids[i]
                    memo[creators[i]][2] = views[i]
                #Step 2a: finding the lexicographically smallest id as we hit the current_popularity_video_view again!
                elif memo[creators[i]][2] == views[i]:
                    memo[creators[i]][1] = min(memo[creators[i]][1],ids[i])
            else:
			#adding new entry to our memo
			#new entry is of the format memo[creator[i]] = [total number current views for the creator, store the lexicographic id of the popular video, current popular view of the creator]
                memo[creators[i]] = [views[i],ids[i],views[i]]
			#track the max popular video count
            overall_max_popular_video_count = max(memo[creators[i]][0],overall_max_popular_video_count)
        
        result = []
        for i in memo:
            if memo[i][0] == overall_max_popular_video_count:
                result.append([i,memo[i][1]])
        return result

        # n = len(creators)
        # mapping = {}
        # for ind in range(n):
        #     if creators[ind] not in mapping.keys():
        #         mapping[creators[ind]] = {}
        #         mapping[creators[ind]]['pop'] = views[ind]
        #         dp = []
        #         heapq.heappush(dp, [-views[ind], ids[ind]])
        #         mapping[creators[ind]]['video'] = dp
        #     else:
        #         mapping[creators[ind]]['pop'] += views[ind]
        #         heapq.heappush(mapping[creators[ind]]['video'], [-views[ind], ids[ind]])
                
        # max_pop = max([mapping[key]['pop'] for key in mapping.keys()])
        # ans = []
        # for creator, value in mapping.items():
        #     if value['pop'] == max_pop:
        #         # print(video)
        #         video = heapq.heappop(value['video'])
        #         ans.append([creator, video[1]])
        # return ans
```
