---
layout: post
title: Neetcode Roadmap - Solution to Arrays & Hashing problem in C++
categories: Neetcode C++
---

## Contains Duplicate

link: [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

Solution:

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        map<int, int> counts;
        for(int i: nums) counts[i]++;

        for(auto it : counts){
            if(it.second > 1) return true;
        }
        return false; 
    }
};
```


## Valid Anagram

link: [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

Solution:

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.length() != t.length()) return false;
        unordered_map<char, int> m1, m2;
        for(char c : s) m1[c]++;
        for(char c : t) m2[c]++;

        if(m1.size() != m2.size()) return false;
        for(auto it : m1){
            if(it.second != m2[it.first]) return false; 
        }
        return true; 
    }
};
```

Follow up: What if the inputs contain Unicode characters? How would you adapt your solution to such a case?

`std::unordered_map<std::wstring>` instead of `std::unordered_map<char>`

## Two Sum

link: [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

Solution:

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> index; 
        for(int i=0; i < nums.size(); i++){
            index[nums[i]] = i; 
            
        }
        for(int i=0; i< nums.size(); i++){
            int otherNumber = target - nums[i];
            if(index.find(otherNumber) != index.end() && index[otherNumber] != i){
                return vector<int> {i, index[otherNumber]};
            }
        }

        return vector<int> {-1,-1}; 
    }

    
};
```

## Group Anagrams

link: [https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)

Solution:

```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<vector<string>>  groups; 
        unordered_map<string, vector<string>> m;

        for(string s: strs){
            string key = s;
            sort(key.begin(), key.end());
            m[key].push_back(s);
        }

        for(auto x : m) groups.push_back(x.second);
        return groups; 
    }
};
```

## Top K Frequent Elements


