# 0608
> Bit - LSB, MSB

- **The least significant bit (LSB)** is the rightmost bit or the bit with the lowest positional value within a binary number. It is also referred to as the rightmost bit or the bit at position 0.
```py
def calculate_lsb(number):
    lsb = number & 1
    return lsb
```
- **The most significant bit (MSB)** is the leftmost bit or the highest-order bit in a binary representation of a number.
```py
def calculate_msb(number):
    msb = 0
    while number != 0:
        number = number >> 1    # Right-shift the number by 1 bit
        msb = number & 1        # Perform bitwise AND operation with 1
    return msb
```

## 191. Number of 1 Bits
```py
class Solution:
    def hammingWeight(self, n: int) -> int:
        count = 0
        while n:
            count += n & 1
            n >>= 1
        
        return count
        
        # time: O(logn)
        # space: O(1)
```

## 338. Counting Bits
- LSB
```py
class Solution:
    def countBits(self, n: int) -> List[int]:
        res = [0] * (n + 1)
        for i in range(n + 1):
            res[i] = self.getBinaryOne(i)
        
        return res
    
    def getBinaryOne(self, num):
        count = 0
        while num:
            count += num & 1
            num >>= 1
        return count
        
    # time: O(n * logn)
    # space: O(1)
```
- DP + LSB
```py
class Solution:
    def countBits(self, n: int) -> List[int]:
        res = [0] * (n + 1)
        for i in range(n + 1):
            res[i] = res[i >> 1] + (i & 1)
        
        return res
        
        # time: O(n)
        # space: O(1)
```
