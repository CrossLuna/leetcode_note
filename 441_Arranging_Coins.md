# 441. Arranging Coins 

[Description](https://leetcode.com/problems/arranging-coins/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int arrangeCoins(int n) {
        int orig_n = n;
        int i = 1;
        for(; i<=orig_n; ++i) {
            n -= i;
            if(n < 0) return i-1;
            else if(n == 0) return i;
        }
        return 0;
    }
};
```

## 思路
逐次相減，注意邊界

## 複雜度

## 解法二
```C++
class Solution {
public:
    int arrangeCoins(int n) {
        return floor(-0.5 + sqrt(2.0*n+0.25));
    }
};
```
## 思路

## 複雜度