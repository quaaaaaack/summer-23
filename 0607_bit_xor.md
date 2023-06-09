# 0607
> Bit - XOR

- **Finding the single/duplicate number**: XOR can be used to find the single or duplicate number in an array. By XORing all the elements of the array, the numbers that appear twice will cancel out each other, leaving only the single or duplicate number in the result.

- **Finding missing numbers**: XOR can be used to find the missing number(s) in a given range. By XORing all the numbers in the range with the elements in the array, the missing number(s) will be left in the result.

- **Swapping values**: XOR can be used to swap the values of two variables without using an extra variable. By XORing the two variables, their values are flipped.
```py
def swapValues(a, b):
    a ^= b
    b ^= a
    a ^= b
    return a, b
```

- **Detecting the odd occurrence**: XOR can be used to find the element that appears an odd number of times in an array. By XORing all the elements of the array, the elements that appear twice will cancel out each other, leaving only the element that appears an odd number of times.

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
`res ^= i ^ num`: XORs the current value of res with the current index i and the current element num. XOR is a bitwise operator that returns 1 if the corresponding bits of the operands differ; otherwise, it returns 0.

- The first XOR operation `res ^= i` effectively cancels out the numbers from `0` to `n` present in `res` because XORing a number with itself results in `0`.
- The second XOR operation `res ^= num` XORs `res` with the current element `num`. This cancels out the numbers that are present in both `res` and `num`.  

After completing the loop, res will be left with the missing number from the array.
