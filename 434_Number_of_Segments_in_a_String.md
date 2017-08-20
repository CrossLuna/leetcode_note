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



## 解法二
```C++
```
## 思路