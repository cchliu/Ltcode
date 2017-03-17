# Contiguous Subarray
#### Two pointers: left start --> right end

### 209. Minimum Size Subarray Sum 

[problem description](https://leetcode.com/problems/minimum-size-subarray-sum/#/description)

The solution below is O(n) time complexity.
```
class Solution(object):
    def minSubArrayLen(self, s, nums):
        """
        :type s: int
        :type nums: List[int]
        :rtype: int
        """
        tsum, left = 0, 0
        lenth = len(nums)
        minSub = lenth + 1
        if lenth == 0:
            return 0
        for right,n in enumerate(nums):
            tsum += n
            while tsum >= s:
                minSub = min(right-left+1, minSub)
                tsum -= nums[left]
                left += 1
        if minSub > lenth:
            return 0
        else:
            return minSub
 ```
 ### 325. Maximum Size Subarray Sum Equals k
 
 [problem description](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/#/description)
 
 Ideas:
 - Sum of any contiguous subarray is equal to x<sub>2</sub> - x<sub>1</sub>, as shown in this figure ![figure](https://github.com/cchliu/Ltcode/blob/master/ltcode_p325.png)
 - We are looking for subarray whose sum is equal to k, so we have x<sub>2</sub> - x<sub>1</sub> = k
 - Save all the "sum from left" sums into an dictionary, for each x<sub>2</sub>, looking up in the dictionary if key x<sub>1</sub> exists.
 ```
 class Solution(object):
    def maxSubArrayLen(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        lenth = len(nums)
        if lenth == 0:
            return 0
        sumDict = {}
        # Don't forget key-value pair: {0:-1}
        sumDict[0] = -1
        acc, maxSub = 0, 0
        for idx in range(lenth):
            acc += nums[idx]
            if not acc in sumDict:
                sumDict[acc] = idx
            if acc-k in sumDict:
                maxSub = max(maxSub, idx-sumDict[acc-k])
        return maxSub
 ```

