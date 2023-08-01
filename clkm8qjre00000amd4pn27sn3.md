---
title: "Leet code 217 Contains Duplicate"
datePublished: Fri Jul 28 2023 07:07:04 GMT+0000 (Coordinated Universal Time)
cuid: clkm8qjre00000amd4pn27sn3
slug: leet-code-217-contains-duplicate
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/f77Bh3inUpE/upload/19ee25fb32ad81e2ba9e4e2d1de71512.jpeg
tags: data-structures, arrays, python-dictionaries

---

**217\. Contains Duplicate**

**Easy**

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

```plaintext
Input: nums = [1,2,3,1]
Output: true
```

**Example 2:**

```plaintext
Input: nums = [1,2,3,4]
Output: false
```

**Example 3:**

```plaintext
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

**Constraints:**

* `1 <= nums.length <= 10<sup>5</sup>`
    
* `-10<sup>9</sup> <= nums[i] <= 10<sup>9</sup>`
    

Input: nums = \[1,2,3,1\]

Output: true

**Example 2:**

Input: nums = \[1,2,3,4\]

Output: false

**Example 3:**

Input: nums = \[1,1,1,3,3,4,3,2,4,2\]

Output: true

**Constraints:**

1 &lt;= nums.length &lt;= 105 -109 &lt;= nums\[i\] &lt;= 109

### Intuition

My first thought to solving this problem was a brute force approach, which is to just iterate over the entire list, and compare each element of the array to the next. Although this worked, it didn't take into account a List with a vast number of elements, it also didn't take into account an unsorted list.

### First Approach

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[i] == num[j]:
                    return True
        return False
```

The first approach has a time complexity of O(n^2) because it utilizes two for loops to compare two elements, which is very inefficient. After all, as the array grows larger, the run time also increases. Hence, I had to refactor the code to be more efficient.

---

### Second Approach

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        nums.sort()
        for i in range(len(nums) - 1):
                if nums[i] == nums[i + 1]:
                    return True
        return False
```

The second approach was more efficient than the first because the dominant operation was sorting the list and the approach utilized a single for loop. The sort method in Python uses the Timsort algorithm which has a time complexity of O(n log n) which is more time efficient than the first approach.

Complexity

Time complexity: O(n log n)

Space complexity: O(1) - This is because the sorting operation was performed in place, meaning no new space was allocated for the list in memory.

Although this approach passed all test cases, a more efficient method to solve this problem is by utilizing a dictionary, or a hash map. The time complexity of this approach is O(n) and the space complexity is O(n).

### Optimised Approach

```python
class Solution:
def containsDuplicate(self, nums: List[int]) -> bool:
    dict = {}
    for element in nums:
        if element in dict:
            return True
        dict[element] = True
    return False
```

You can find the source code [here](https://github.com/IamLam163/Data-Structures-and-Algorithm-Leetcode-Challenge/tree/main/Leetcode/Arrays). The next problem will be Leetcode 242 Valid Anagram.