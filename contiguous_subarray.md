# Contiguous Subarray
#### Two pointers: left start --> right end

### 209. Minimum Size Subarray Sum 

[problem description](https://leetcode.com/problems/minimum-size-subarray-sum/#/description)
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
 

