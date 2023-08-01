---
title: "Leet Code 1 Two Sum"
datePublished: Tue Aug 01 2023 11:30:14 GMT+0000 (Coordinated Universal Time)
cuid: clks7webn000v0ajr22qkfh3n
slug: leet-code-1-two-sum
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/BVr3XaBiWLU/upload/bf5a0fb6caee52156baba10eec1b50af.jpeg
tags: data-structures, leetcode, problem-solving-skills

---

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

`Example 1:`

`Input: nums = [2,7,11,15], target = 9`

`Output: [0,1]`

`Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].`

`Example 2:`

`Input: nums = [3,2,4], target = 6`

`Output: [1,2]`

`Example 3:`

`Input: nums = [3,3], target = 6 Output: [0,1]`

`Constraints:`

`2 <= nums.length <= 104 -109 <= nums[i] <= 109 -109 <= target <= 109 Only one valid answer exists.`

### Intuition

The Two sum problem is quite tricky because you are required to return the index and not the value. To do this my first thought was to initialise a dictionary to store the elements encountered, then use python enumerate() which returns the value and index. The next step is to get a match that adds up to the target, this is done by first subtracting the target from each element in the nums array. If a match is found the dictionary, the matching element, and its index are returned, else the index is updated with a value in the dictionary for another iteration. If no match is found, an empty array is returned

**Approach**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        mydict = {}

        for idx, val in enumerate(nums):
            match = target - val

            if match in mydict:
                return [mydict[match], idx]

            mydict[val] = idx
        return []
```

---

### Complexity

* Time complexity: O(n) the time taken grows linearly as the size of input nums
    
* Space complexity: O(n) the size of the dictionary is size n i.e. the size of the array nums
    

### Alternative Approach

In an attempt to discover a more efficient approach, I opted to utilize a set. However, this alternative method turned out to be less efficient compared to the initial one, as it resulted in a time complexity of O(n^2) because I had to search the entire nums array for the match. Although both approaches shared the same space complexity of O(n) when I submitted the code on Leet Code, the set-based approach consumed more memory. Nevertheless, I will still share it for reference :-)

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = set()

        for idx, val in enumerate(nums):
            match = target - val

            if match in seen:
                return [nums.index(match), idx]
            seen.add(val)

        return []
```

Overall, this problem helps strengthen your ability to breakdown problems, and further deepen your ability to think critically whilst considering the efficiency of the algorithm you develop. You can check [here](https://github.com/IamLam163/Data-Structures-and-Algorithm-Leetcode-Challenge/tree/main/Leetcode/Arrays) for source code and unit tests. The next problem will be Leet Code 49. Group Anagrams.