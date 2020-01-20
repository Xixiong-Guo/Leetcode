# Leetcode
Repo used for recording my daily Python practice @ Leetcode

# Easy

## 1. [Two Sum](https://leetcode.com/problems/two-sum/)   <br>
Given an array of integers, return indices of the two numbers such that they add up to a specific target. <br>
Example: Given nums = [2, 7, 11, 15], target = 9, Because nums[0] + nums[1] = 2 + 7 = 9, return [0, 1].

Notes: define a dictionary, and use target-i to determine its pair number and related index

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


## 118. [Pascal Triangle](https://leetcode.com/problems/pascals-triangle/) <br>
Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.

Notes: list.append() , build a list row[] to help record nums in each row.

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        
        answer = []
        for i in range(numRows):
            row = [1] * (i+1)
            for j in range(1,i):
                row[j] = answer[i-1][j] + answer[i-1][j-1]
            answer.append(row)
        return answer
                
```


# Medium



# Hard
