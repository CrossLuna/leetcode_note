# 567. Permutation in String 

[Description](https://leetcode.com/problems/permutation-in-string/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool all_zeros(vector<int>& v) {
        for(auto n: v) 
            if(n != 0) return false;
        return true;
    }
    bool checkInclusion(string s1, string s2) {
        if(s1.size() > s2.size()) return false;
        vector<int> m(256, 0);
        for(auto ch: s1) ++m[ch];
        int N = s1.size();
        int i=0;
        for(; i<N; ++i) {
            --m[s2[i]];
        }
        if(all_zeros(m)) return true;
        for(; i<s2.size(); ++i) {
            --m[s2[i]];
            ++m[s2[i-N]];
            if(all_zeros(m)) return true;
        }
        return false;
    }
};
```

## 思路
Sliding window

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度