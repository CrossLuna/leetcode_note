# 161. One Edit Distance 

[Description](https://leetcode.com/problems/one-edit-distance/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool isOneEditDistance(string s, string t) {
        // s is shorter
        if(s.size() > t.size()) swap(s, t);
        if(t.size() > s.size() + 1) return false;
        int i = 0, j = 0;
        for(; i<s.size(); ++i, ++j) {
            if(s[i] != t[j]) {
                return i+1 == s.size() && j+1 == t.size() ||
                       s.substr(i) == t.substr(i+1) ||
                       s.substr(i+1) == t.substr(i+1);
            }
        }
        if(s.size() + 1 == t.size()) return true;
        return false;
    }
};
```

## 思路
小心檢查邊界條件，分成三種討論

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度