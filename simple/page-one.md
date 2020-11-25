### 1. 两数之和

#### 题目

```txt
给定一个整数数组nums和一个目标值target，请你在该数组中找出和为目标值的那两个整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。
```

####  示例

```py
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

#### 代码

```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for ni in range(len(nums)):
            if target - nums[ni] in nums[ni+1:]:
                nj = nums[ni+1:].index(target - nums[ni])
                return [ni, ni+nj+1]
```

### 7.整数反转

#### 题目

```txt
给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。
```

#### 示例

```py
# 示例1

输入: 123
输出: 321
 
# 示例2

输入: -123
输出: -321

# 示例3

输入: 120
输出: 21
```

#### 注意

```txt
假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−231,  231 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。
```

#### 代码

```py
class Solution:
    def reverse(self, x: int) -> int:
        flag = 1
        if x < 0:
            flag = -1
        res = str(abs(x))[::-1]
        value = int(res) * flag
        if value < -pow(2, 31) or value > pow(2, 31) - 1:
            return 0
        return value
```

### 9.回文数

#### 题目

```txt
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。
```

#### 示例

```py
# 示例1

输入: 121
输出: true

# 示例2

输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。

# 示例3

输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。
```

#### 进阶

```txt
你能不将整数转为字符串来解决这个问题吗？
```

#### 代码

```py
class Solution:
    def isPalindrome(self, x: int) -> bool:
        return str(x) == str(x)[::-1]
```

```py
from collections import deque

class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False
        current = deque()
        while x:
            current.append(x % 10)
            x //= 10
        while len(current) > 1:
            front, rear = current.popleft(), current.pop()
            if front != rear:
                return False
        return True
```
