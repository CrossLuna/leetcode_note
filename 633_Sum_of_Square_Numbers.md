# 633. Sum of Square Numbers 

[Description](https://leetcode.com/problems/sum-of-square-numbers/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool judgeSquareSum(int c) {
        for(int n=0; n*n <= c/2; ++n) {
            int b_2 = c - n*n;
            int b = sqrt(b_2);
            if(b * b == b_2) return true;
        }
        return false;
    }
};
```

## 思路
窮舉，注意條件，沒必要的別舉

## 複雜度

## 解法二
```C++
class Solution {
public:
    bool judgeSquareSum(int c) {
        int right = sqrt(c);
        int left = 0;
        while(left <= right) {
            int sum = left*left + right*right;
            if(sum == c) return true;
            else if(sum < c) ++left;
            else --right;
        }
        return false;
    }
};
```
## 思路
左右指針法，兩方向夾擠

## 複雜度