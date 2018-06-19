# 344. Reverse String

[Description](https://leetcode.com/problems/reverse-string/description/)

## 解法一
```C++
class Solution {
public:
    string reverseString(string s) {
        for(int i=0; i<s.size()/2; ++i) {
            swap(s[i], s[s.size()-i-1]);
        }
        return s;
    }
};
```

## 思路
標準解法

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度