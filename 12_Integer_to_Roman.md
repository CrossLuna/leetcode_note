# 12. Integer to Roman 

[Description](https://leetcode.com/problems/integer-to-roman/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    string intToRoman(int num) {
        string ans;
        vector<pair<int,string>> vec{
            {1000, "M"},
            {900, "CM"},
            {500, "D"},
            {400, "CD"},
            {100, "C"},
            {90, "XC"},
            {50, "L"},
            {40, "XL"},
            {10, "X"},
            {9, "IX"},
            {5, "V"},
            {4, "IV"},
            {1, "I"}
        };
        for(auto& p: vec) {
            if(num / p.first > 0) {
                for(int i=0; i<num/p.first; ++i) {
                    ans += p.second;
                }
            }
            num -= num / p.first * p.first;
        }
        return ans;
    }
};
```

## 思路
貪心算法，關鍵是列出4和9的行為

## 複雜度
Almost constant

## 解法二
```C++
class Solution {
public:
    string intToRoman(int num) {
        vector<string> M {"", "M", "MM", "MMM"};
        vector<string> C {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};
        vector<string> X {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};
        vector<string> I {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};
        return M[num/1000] + C[(num%1000)/100] + X[(num%100)/10] + I[num%10];
    }
};
```
## 思路
簡單粗暴

## 複雜度