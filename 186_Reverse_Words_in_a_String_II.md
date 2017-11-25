# 186. Reverse Words in a String II 

[Description](https://leetcode.com/problems/reverse-words-in-a-string-ii/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    void reverseWords(vector<char>& str) {
        int pos = 0;
        int br = 0;
        while(pos < str.size()) {
            br = pos;
            while(str[br] != ' ' && br < str.size()) ++br;
            if(br >= 0) {
                reverse(str.begin() + pos, str.begin() + br);
            }
            pos = br + 1;
        }
        reverse(str.begin(), str.end());
    }
};
```

## 思路
找空格，先反轉每一個字，再反轉整個句子

## 複雜度
時間複雜度O(n)
空間複雜度O(1)

## 解法二
```C++
```
## 思路

## 複雜度