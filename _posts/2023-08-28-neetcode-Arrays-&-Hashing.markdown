---
layout: post
title: Neetcode Roadmap - Solution to Arrays & Hashing problem in C++
categories: Neetcode C++
---

This post contains C++ solution to the problems in the Arrays & Hashing section of the Neetcode Roadmap. I mostly saved it for myself. 
Please let me know if you find any mistakes or have any suggestions. 

![Stock Image](/assets/stockimage.jpeg)

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

Ans: `std::unordered_map<std::wstring>` instead of `std::unordered_map<char>`

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

link: [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)

Solution:

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        vector<int> kFreqElements; 
        unordered_map<int, int> valCount;
        for(int i : nums) valCount[i]++;
         
        vector<pair<int, int>> vec;

        for(auto it : valCount)vec.push_back(pair<int,int>(it.first, it.second));


        sort(vec.begin(), vec.end(), [](const auto &a, const auto &b){ return a.second < b.second;});
        reverse(vec.begin(), vec.end());

        for(int i=0; i<k; i++) kFreqElements.push_back(vec[i].first);

        return kFreqElements;
    }    
};
```

Follow up: Your algorithm's time complexity must be better than O(n log n), where n is the array's size. (TODO)

## Product of Array Except Self

link: [https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)

Solution:

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> prefixProduct(nums.size(), 1), suffixProduct(nums.size(), 1), ans(nums.size(), 1);

        for(int i=1; i< nums.size() ; i++) prefixProduct[i] = prefixProduct[i-1] * nums[i-1];

        for(int i=nums.size()-2; i>= 0; i--) suffixProduct[i] = suffixProduct[i+1] * nums[i+1];

        for(int i=0; i< nums.size(); i++) ans[i] = suffixProduct[i] * prefixProduct[i];

        return ans;
        
    }
};
```

Follow up: Can you solve the problem in O(1) extra space complexity? (The output array does not count as extra space for space complexity analysis.)

Ans: Use the ans as prefixProduct array and the original array as suffixProduct array.

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int>  ans(nums.size(), 1);

        for(int i=1; i< nums.size() ; i++) ans[i] = ans[i-1] * nums[i-1];

        // now ans has the prefix array

        int a = nums.back(), b;
        nums[nums.size()-1] = 1; 

        for(int i=nums.size()-2; i>= 0; i--){
            b = nums[i]; 
            nums[i] = nums[i+1] * a;
            a = b; 
        } 

        for(int i=0; i< nums.size(); i++) ans[i] = ans[i] * nums[i];

        return ans;
        
    }
};
``` 

## Valid Sudoku

link: [https://leetcode.com/problems/valid-sudoku/](https://leetcode.com/problems/valid-sudoku/)

Solution:

```cpp
class Solution {
public:
    bool isValidRow(vector<vector<char>>& board, int rowNum){
        unordered_map<char, int> m;
        for(int j=0; j< 9; j++){
            if(board[rowNum][j] != '.')m[board[rowNum][j]]++;
        }
        for(auto it: m){
            if(it.second > 1) return false;
        }
        return true; 
    }
    bool isValidColumn(vector<vector<char>>& board, int colNum){
        unordered_map<char, int> m;
        for(int i=0; i<9; i++){
            if(board[i][colNum] != '.')m[board[i][colNum]]++;
        }
        for(auto it: m){
            if(it.second > 1) return false;
        }
        return true; 
    }

    bool isValidBox(vector<vector<char>>& board, int rowNum, int colNum){
        unordered_map<char, int> m;
        for(int i= rowNum; i < rowNum+3; i++){
            for(int j = colNum; j< colNum+3; j++){
                if(board[i][j] != '.')m[board[i][j]]++;
            }
        }
        for(auto it: m){
            if(it.second > 1) return false;
        }
        return true;
    }

    bool isValidSudoku(vector<vector<char>>& board) {
        for(int i=0; i<9; i++){
            if(isValidRow(board, i) == false) return false;
        }
        for(int i=0; i<9; i++){
            if(isValidColumn(board, i) == false) return false;
        }
        for(int i=0; i<9 ; i+=3){
            for(int j=0; j<9; j+=3){
                if(isValidBox(board, i, j) == false) return false; 
            }
        }
        return true; 
    }
};
```

## Longest Consecutive Sequence

link: [https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)

Solution:

```cpp

class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_map<int, bool> map; 

        for(int num : nums)map[num] = true; 

        int longestSeqLen = 0, currentSeqLen = 0, i; 

        for(int num : nums){
            if(!map[num-1]){
                // num is first item
                currentSeqLen = 1;
                i = num+1;
                while(map[i]){
                    currentSeqLen += 1;
                    i++;
                }
                longestSeqLen = max ( longestSeqLen, currentSeqLen);
            }
        }

        
        return longestSeqLen; 
    }
};

```







