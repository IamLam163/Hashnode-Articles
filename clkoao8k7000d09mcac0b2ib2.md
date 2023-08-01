---
title: "Leet Code 242 Valid Anagram"
datePublished: Sat Jul 29 2023 17:36:47 GMT+0000 (Coordinated Universal Time)
cuid: clkoao8k7000d09mcac0b2ib2
slug: leet-code-242-valid-anagram
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/uPXs5Vx5bIg/upload/24f74cedd732893e84912bd2c9cdc9f7.jpeg
tags: data-structures

---

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

`Example 1:`

`Input: s = "anagram", t = "nagaram"`

`Output: true`

`Example 2:`

`Input: s = "rat", t = "car"`

`Output: false`

`Constraints:`

`1 <= s.length, t.length <= 5 * 104 s and t consist of lowercase English letters.`

### Intuition

Solving the valid Anagram problem was quite easy, I mean there's the really easy way to solve it, and there's a much more technical approach to solving this problem. My first thought was the easy way which involved checking the lengths of both strings and returning False if it didn't match, and sorting the strings using the inbuilt Sorted() in python and return True if the sorted values match

##### **First Approach**

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        sortS = sorted(s)
        sortT = sorted(t)
        return sortS == sortT
```

The time complexity of this approach is O(n log n) using the inbuilt Sorted() method. The space complexity is O(n) which means as the size of the strings grow so does the size of space allocated.

---

##### **Second Approach**

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        def getCharFreq(word):
            freq = {}
            for char in word:
                freq[char] = 1 + freq.get(char, 0)
            return freq

        frequencyS = getCharFreq(s)
        frequencyT = getCharFreq(t)
        return frequencyS == frequencyT
```

This approach is much more technical and does not abstract the Solution. A hash map is used to calculate the frequency of a character in a string or word, the value of the character is incremented on every iteration and stored in the map. For scalability, a function handles this operation. Finally, both strings are compared and returns True if they are anagrams

**Complexity**

* Time complexity: O(n) This is because as the size of input s and t grows, the time required to execute the function will also grow.
    
* Space complexity: O(n)
    

You can find the source code as well as test cases [here](https://github.com/IamLam163/Data-Structures-and-Algorithm-Leetcode-Challenge/tree/main/Leetcode/Arrays). The next problem will be Leet code Two Sum.