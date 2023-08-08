---
title: "Leet Code 49 Group Anagrams"
datePublished: Tue Aug 08 2023 07:40:59 GMT+0000 (Coordinated Universal Time)
cuid: cll1zsjt0000509kz7ola32ae
slug: leet-code-49-group-anagrams
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/npxXWgQ33ZQ/upload/3699823b6e668279b7d5b0f1174ce45c.jpeg
tags: data-structures, leetcode, problem-solving-skills

---

**49\. Group Anagrams**

**Medium**

`Given an array of strings strs, group the anagrams together. You can return the answer in any order.`

`An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.`

`Example 1:`

`Input: strs = ["eat", "tea", "tan", "ate", "nat", "bat"] Output: [["bat"],["nat", "tan"],["ate", "eat", "tea"]] Example 2:`

`Input: strs = [""] Output: [[""]] Example 3:`

`Input: strs = ["a"] Output: [["a"]]`

`Constraints:`

`1 <= strs.length <= 104 0 <= strs[i].length <= 100 strs[i] consists of lowercase English letters.`

### Intuition

My first thought for solving this problem was to use my previous knowledge of the Leet code valid anagram problem, which opened my eyes to the two ways I could solve the problem, the first method is to sort the word and use it as key in a hashmap while the second method is to count the frequency of a character and store the frequency in a hashmap. That knowledge helped me visualise how to solve this problem.

### First Approach

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        anagrams = {}
        for astr in strs:
            sorted_strs = ''.join(sorted(astr))
            if sorted_strs in anagrams:
                anagrams[sorted_strs].append(astr)
            else:
                anagrams[sorted_strs] = [astr]
        return list(anagrams.values())
```

This approach utilizes a hash map. In this approach, the hash map's keys consist of sorted strings, and the corresponding values are the original words. For instance, for the word "eat," its sorted key would be 'aet,' and the associated value would include all anagrams of the word, such as 'eat,' 'tea,' and 'ate.' This way, words with the same sorted key, like 'tea' and 'ate,' will be mapped together as anagrams. If the sorted strings are not in the map, then we create a new key and find the anagrams. Since we return a list, the hash map is converted to a list and its values are returned.

**Time Complexity:** O(N *M* log M) The loop takes O(n) time when n is the number of words in the strs List, whilst the sorting of the string of size **m** (maximum length of any string) takes O(M *log* M).

**Space Complexity:** O(N + M). Where N is the size of the dictionary and M is the size allocated to the sorted strings.

### Alternative Approach

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        def get_char_count(word: str) -> tuple:
            char_count = [0] * 26
            for char in word:
                char_count[ord(char) - ord('a')] += 1
            return tuple(char_count)

        anagrams_dict = {}
        for astr in strs:
            char_count_key = get_char_count(astr)
            if char_count_key not in anagrams_dict:
                anagrams_dict[char_count_key] = []
            anagrams_dict[char_count_key].append(astr)

        return list(anagrams_dict.values())
```

This approach relies on counting the occurrences of each character in the string and using that count as a key to group anagrams. It avoids the need to sort the characters and use sorted strings as keys, making it slightly more efficient in terms of time complexity. The solution has a time complexity of O(N \* K) where N is the time it takes to loop through the strs list and K is the maximum length of each string. The space complexity is O(N).

The source code as well as tests can be found [here](https://github.com/IamLam163/Data-Structures-and-Algorithm-Leetcode-Challenge/tree/main/Leetcode/Arrays). Our next problem is Leet code 347 Top K Frequent Elements.