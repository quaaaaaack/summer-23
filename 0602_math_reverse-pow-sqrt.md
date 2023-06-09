# 0602
> Math
> - Reverse
> - Pow & Sqrt

## 7. Reverse Integer
```py
class Solution:
    def reverse(self, x: int) -> int:
        mark = 1 if x >= 0 else -1

        x = abs(x)
        res = 0
        while x:
            res = res * 10 + x % 10
            x //= 10
            if res > 2 ** 31 - 1:
                return 0
        
        return mark * res
        
        # time: O(logn)
        # space: O(1)
```

## 9. Palindrome Number
- Reverse all
```py
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0 or (x != 0 and x % 10 == 0):
            return False
        
        origin = x
        reverse = 0

        while x:
            reverse = reverse * 10 + x % 10
            x //= 10
        
        return reverse == origin
        
        # time: O(logn)
        # space: O(1)
```
- Reverse half
```py
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0 or (x > 0 and x % 10 == 0):
            return False
        
        reverse = 0
        while x > reverse:
            reverse = reverse * 10 + x % 10
            x //= 10
            
        # If the length of x is odd, we need to remove the middle digit from reverse 
        # to ensure it has the same number of digits as x
        return x == reverse or x == reverse // 10
        
        # time: O(logn)
        # space: O(1)
```

## 50. Pow(x, n)
```py
class Solution:
    def myPow(self, x: float, n: int) -> float:
        if n < 0:
            x = 1 / x
            n = -n
        
        res = 1
        while n > 0:
            if n % 2 == 1:
                res *= x
            x *= x
            n //= 2

        return res
        
        # time: O(logn)
        # space: O(1)
```

## 69. Sqrt(x)
- Binary search
```py
class Solution:
    def mySqrt(self, x: int) -> int:
        left = 0
        right = x

        while left <= right:
            mid = left + (right - left) // 2
            sqr = mid * mid
            if sqr == x:
                return mid
            if sqr < x:
                left = mid + 1
            else:
                right = mid - 1
            
        return right
        
        # time: O(nlogn)
        # space: O(1)
```

## 633. Sum of Square Numbers
- Two pointers
```py
class Solution:
    def judgeSquareSum(self, c: int) -> bool:
        left = 0
        right = int(sqrt(c))

        while left <= right:
            sum_of_sqr = left ** 2 + right ** 2
            if sum_of_sqr == c:
                return True
            if sum_of_sqr < c:
                left += 1 
            else:
                right -= 1
        
        return False
        
        # time: O(sqrt(c))
        # space: O(1)
```
