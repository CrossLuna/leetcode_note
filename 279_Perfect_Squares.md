# 279. Perfect Squares 

[Description](https://leetcode.com/problems/perfect-squares/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int numSquares(int n) {
        vector<int> squares;
        for(int i=1; i*i <=n; ++i) {
            squares.push_back(i*i);
        }
        vector<int> dp(n+1);
        for(int i=1; i<=n; ++i) {
            dp[i] = i;
            for(int sq: squares) {
                if(i-sq >= 0)
                    dp[i] = min(dp[i], dp[i-sq]+1);
            }
        }
        return dp[n];
    }
};
```

## 思路
動態規劃

## 複雜度
O(n sqrt(n))

## 解法二
```C++
class Solution {
public:
    int numSquares(int n) {
        vector<int> dp(n+1);
        for(int i=1; i<=n; ++i) {
            dp[i] = i;
            for(int j=1; j*j <= i; ++j) {
                dp[i] = min(dp[i], dp[i-j*j] + 1);
            }
        }
        return dp.back();
    }
};
```
## 思路
不需要存平方數

## 複雜度
O(n sqrt(n))

## 解法三
## 思路
Lagrange's Four Square theorem，省略