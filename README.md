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

## 7 [Reverse integer](https://leetcode.com/problems/reverse-integer/)  <br>
Given a 32-bit signed integer, reverse digits of an integer. <br>
Example: Input 123, output 321 ; Input -120, output -21
```python
class Solution:
    def reverse(self, x):
        result = 0
        a = abs(x)
            
        while (a != 0):
            temp = a%10
            result = result * 10 + temp
            a = int(a/10)
            
        if x > 0 and x < 2**31-1:
            return result
        elif x < 0 and x > -(2**31):
            return -result
        else:
            return 0
```

## 13 [Roman to integer](https://leetcode.com/problems/roman-to-integer/)
Input a Roman str, and output its representing integer

Notes: a) 4,40,9,90 ... are IV, XL, IX, XC ....  if to determine the aggregation
b) Use dictionary to represent keys and values

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        
        map_value = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        result = 0
        
        for i in range(len(s)):
            if (i > 0) and (map_value[s[i]]>map_value[s[i-1]]):
                result = result - 2 * map_value[s[i-1]] + map_value[s[i]]
            else:
                result = result + map_value[s[i]]
                
        return result
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

## 46. [Permutations](https://leetcode.com/problems/permutations/)  <br>
Given a collection of distinct integers, return all possible permutations. <br>
Example:
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        if len(nums)==1:
            return [nums]
        
        result=[]
        for index,num in enumerate(nums):
            n = nums[:index]+nums[index+1:]
            for y in self.permute(n):
                result.append([nums[index]]+y)
        return result
```


## 973. [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)

Notes: Pythagoras theorem (Euclidean distance)  

a. sorted, and pick up the top k element (in this way, other elements are all sorted, which is not required, so the computing time is wasted)
```python
class Solution(object):
    def kClosest(self, points, K):
        """
        :type points: List[List[int]]
        :type K: int
        :rtype: List[List[int]]
        """
        return sorted(points, key=lambda p: p[0]**2 + p[1]**2)[:K]
```
b. Heapq (heapq.nsmallest) 堆排序

# Hard
