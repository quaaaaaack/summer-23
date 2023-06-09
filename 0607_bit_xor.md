# 0607
> Bit - XOR

## 136. Single Number
```py
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        res = 0

        for num in nums:
            res ^= num
        
        return res
        
        # time: O(n)
        # space: O(1)   
```

## 268. Missing Number
```py
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        res = len(nums)
        for i, num in enumerate(nums):
            res ^= i ^ num
        
        return res
        
        # time: O(n)
        # space: O(1)   
```
