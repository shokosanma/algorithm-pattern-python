# 双指针



## 接雨水问题



[盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/)

```
class Solution:
    def maxArea(self, height: List[int]) -> int:
        left = 0
        right = len(height)-1
        res = 0
        while left < right:
            res = max(res, min(height[left], height[right])*(right-left))
            if height[left] < height[right]:
                left += 1
            else:
                right -= 1
        return res
```



[接雨水](https://leetcode-cn.com/problems/trapping-rain-water/)

```
class Solution:
    def trap(self, height: List[int]) -> int:
        if len(height) <= 2:
            return 0
        left = 1
        right = len(height)-2
        res = 0
        ml = height[0]
        mr = height[len(height)-1]
        while left <= right:
            if ml < mr:
                res += max(ml-height[left], 0)
                ml = max(ml, height[left])
                left += 1
            else:
                res += max(mr-height[right], 0)
                mr = max(mr, height[right])
                right -= 1
        return res
```

