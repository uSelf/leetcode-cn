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

