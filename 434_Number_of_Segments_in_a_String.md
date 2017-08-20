#434. Number of Segments in a String 

[Description](https://leetcode.com/problems/number-of-segments-in-a-string/description/)

## First Attemp
```C++
class Solution {
public:
    int countSegments(string s) {
        int cnt = 0;
        bool in_seg = false;
        for(int i=0; i<s.size(); ++i) {
            if(s[i] == ' ') {
                if(in_seg) {
                    in_seg = false;
                }
            }
            else {
                if(!in_seg) {
                    in_seg = true;
                    cnt++
                }
            }
        }
        return cnt;
    }
};
```

## 解法一
```C++
class Solution {
public:
    int countSegments(string s) {
        int cnt = 0;
        bool in_seg = false;
        for(int i=0; i<s.size(); ++i) {
            if(s[i] == ' ') {
                if(in_seg) {
                    in_seg = false;
                }
            }
            else {
                if(!in_seg) {
                    in_seg = true;
                    cnt++;
                }
            }
        }
        return cnt;
    }
};
```

## 思路
直接implement

## 複雜度
O(n)

## 檢討
1. 分號！！！

## 解法二
```C++
class Solution {
public:
    int countSegments(string s) {
        int res = 0;
        for (int i = 0; i < s.size(); i++) 
            res += s[i] != ' ' && (i + 1 == s.size() || s[i + 1] == ' ');
        return res;
    }
};
```
## 思路
相同，比較精簡