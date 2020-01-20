# Leetcode
Repo used for recording my daily Python practice @ Leetcode



1. [Two Sum](https://leetcode.com/problems/two-sum/)   <br>
Given an array of integers, return indices of the two numbers such that they add up to a specific target. <br>
Example: Given nums = [2, 7, 11, 15], target = 9, Because nums[0] + nums[1] = 2 + 7 = 9, return [0, 1].

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dict = {} # Define a dictionary
        for i in range(len(nums)): 
            x = nums[i]
            if target-x in dict:
                return (dict[target-x], i)          
            dict[x] = i
```
