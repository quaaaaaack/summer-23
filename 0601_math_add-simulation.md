# 0601
> Math - Add Simulation
 ## 67. Add Binary
 - Bit-by-bit Computation
 ```py
 class Solution:
    def addBinary(self, a: str, b: str) -> str:
        res = []
        carry = 0
        
        i = len(a) - 1
        j = len(b) - 1

        while i >= 0 or j >= 0 or carry:
            bit_a = int(a[i]) if i >= 0 else 0
            bit_b = int(b[j]) if j >= 0 else 0
            bit_sum = bit_a + bit_b + carry

            cur_bit = bit_sum % 2
            carry = bit_sum // 2

            res.append(str(cur_bit))

            i -= 1
            j -= 1

        return "".join(res[::-1])

        # time: O(n)
        # space: O(n)
 ```
 
- Bit: bitwise
 ```py
 class Solution:
    def addBinary(self, a: str, b: str) -> str:
        x = int(a, 2)
        y = int(b, 2)
        
        return bin(x + y)[2:]
        # time: O(n)
        # space: O(1)
 ```
## 415. Add Strings *
```py
class Solution:
    def addStrings(self, num1: str, num2: str) -> str:
        res = []
        carry = 0

        i = len(num1) - 1
        j = len(num2) - 1

        while i >= 0 or j >= 0 or carry:
            x = int(num1[i]) if i >= 0 else 0
            y = int(num2[j]) if j >= 0 else 0
            cur_sum = x + y + carry

            cur_char = cur_sum % 10
            carry = cur_sum // 10

            res.append(str(cur_char))

            i -= 1
            j -= 1
        
        return "".join(res[::-1])
        
        # time: O(n)
        # space: O(n)
```
## 2. Add Two Numbers
 ```py
 # Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:

        dummy = ListNode(0)
        cur = dummy
        carry = 0

        while l1 or l2 or carry:
            v1 = l1.val if l1 else 0
            v2 = l2.val if l2 else 0
            temp_sum = v1 + v2 + carry
            carry = temp_sum // 10
            cur.next = ListNode(temp_sum % 10)
            
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
            cur = cur.next
            
        return dummy.next
 ```

## 66. Plus One *
- Digit by Digit
```py
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        carry = 1  # Start with a carry of 1
        res = []
        i = len(digits) - 1

        while i >= 0 or carry:
            cur_sum = digits[i] + carry if i >= 0 else carry

            digit = cur_sum % 10
            carry = cur_sum // 10
            
            res.append(digit)

            i -= 1

        return res[::-1]

        # time: O(n)
        # space: O(n)
```
- Save space
```py
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        for i in range(len(digits) - 1, -1, -1):
            if digits[i] == 9:
                digits[i] = 0
            else:
                digits[i] += 1
                return digits
            
        return [1] + digits
        
        # time: O(n)
        # space: O(1)
```

## 43. Multiply Strings *
```py
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        if num1 == "0" or num2 == "0":
            return "0"

        n1 = len(num1)
        n2 = len(num2)
        res = [0] * (n1 + n2)

        for i in range(n1 - 1, -1, -1):
            for j in range(n2 - 1, -1, -1):
                product = int(num1[i]) * int(num2[j])
                cur_sum = product + res[i + j + 1]
                
                digit = cur_sum % 10
                carry = cur_sum // 10

                res[i + j + 1] = digit
                res[i + j] += carry
        
        while res[0] == 0:
            res.pop(0)

        return ''.join(str(digit) for digit in res)

        # time: O(n1 * n2 + n1 * (n1 + n2) + n1 + n2)
        # space: O(n1 + n2)
```
