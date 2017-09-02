# 438. Find All Anagrams in a String 

[Description](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool all_zero(vector<int>& m) {
        for(auto n: m) {
            if(n != 0) return false;
        }
        return true;
    }
    vector<int> findAnagrams(string s, string p) {
        vector<int> ans;
        if(s.size() < p.size()) return ans;
        vector<int> m(256, 0);
        for(auto ch: p) ++m[ch];
        for(int i=0; i<p.size(); ++i) {
            --m[s[i]];
        }
        if(all_zero(m)) ans.push_back(0);
        for(int j=1; j<s.size()-p.size()+1; ++j) {
            ++m[s[j-1]];
            --m[s[j+p.size()-1]];
            if(all_zero(m)) ans.push_back(j);
        }
        return ans;
    }
};
```
## 思路
Sliding Window，每次檢查，一進一出

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度