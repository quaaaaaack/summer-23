# 0606
> Math - String, Greedy
## 179. Largest Number
```py
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        def compare(x, y): 
            return int(y+x) - int(x+y)
        nums = sorted(map(str, nums), key=cmp_to_key(compare))
        return "0" if nums[0]=="0" else "".join(nums)
```

## 2384. Largest Palindromic Number
```py
class Solution:
    def largestPalindromic(self, num: str) -> str:
        freqs = collections.Counter(num)
        # edge cases
        if freqs['0'] == len(num):
            return "0"

        # left side
        left = ""
        for i in "987654321":
            left += i * (freqs[i] // 2)
        if left:
            left += '0' * (freqs['0'] // 2)

        right = left[::-1]

        center = ""

        for i in "9876543210":
            if freqs[i] % 2 == 1:
                center = i
                break
        
        return left + center + right
```
