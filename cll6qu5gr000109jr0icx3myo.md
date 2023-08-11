---
title: "Leet Code 347 Top K Frequent Elements"
datePublished: Fri Aug 11 2023 15:29:08 GMT+0000 (Coordinated Universal Time)
cuid: cll6qu5gr000109jr0icx3myo
slug: leet-code-347-top-k-frequent-elements
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/5fNmWej4tAA/upload/5f9cec15e1d89c4c220efa261b10ae7d.jpeg
tags: data-structures, problem-solving, leetcode

---

`Top K Frequent Elements`

`Medium`

`Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.`

`Example 1:`

`Input: nums = [1,1,1,2,2,3], k = 2 Output: [1,2] Example 2:`

`Input: nums = [1], k = 1 Output: [1]`

`Constraints:`

`1 <= nums.length <= 105 -104 <= nums[i] <= 104 k is in the range [1, the number of unique elements in the array]. It is guaranteed that the answer is unique.`

`Follow up: Your algorithm's time complexity must be better than O(n log n), where n is the array's size.`

### Intuition

My first approach to this problem was to use my previous knowledge of Leet code 217 Contains duplicate problem. I know using a dictionary will be optimal, the only twist to this problem is returning the top two most recurring elements.

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        mydict = {}
        for num in nums:
            if num not in mydict:
                mydict[num] = 0
            mydict[num] += 1
        return sorted(mydict, key=lambda value: mydict[value], reverse=True)[:k]
```

This approach initialises a dictionary, then iterates through the nums list, if there is no item in the dictionary, initialise it to 0, if there is increment by 1. Then return the sorted items in the dictionary by first using the lambda function to store the items and their frequency count, reverse is set to True which means the higher frequencies comes first. We then slice the top :k elements.

**Time Complexity:** O(n + k) because the time take to iterate through the list is O(n), sorting is determined by the size of nums(n) and slicing also takes O(k) time.

**Space Complexity:** O(n + k), because where created a dictionary and also returned a list. N is the length of the input nums list, and k is the value provided as an argument to the function.

### **Optimized Approach**

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        mydict = Counter(nums)
        return [item[0] for item in mydict.most_common(k)]
```

Solving this problem in just two lines is quite amazing, Using the Counter from the collections library and the most\_common() and List comprehension, the top K elements were easily found.

**Time Complexity:** O(n log n) because of the most\_common method uses a heap to sort the list.

**Space Complexity:** O(n + k) where n is the size of the dict and k represents the size of the top k elements.

If you want to check out more methods to solve this problem, check [here](https://github.com/IamLam163/Data-Structures-and-Algorithm-Leetcode-Challenge/tree/main/Leetcode/Arrays). Our next problem is Leet Code 238 Product of Array Except Self.