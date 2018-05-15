# 70. Climbing Stairs

[Description](https://leetcode.com/problems/climbing-stairs/description/)

## 解法一
```C++
class Solution {
public:
    int climbStairs(int n) {
        vector<int> dp(n+1, 0);
        dp[0] = 1;
        dp[1] = 1;
        for(int i=2; i<=n; ++i) {
            dp[i] = dp[i-1] + dp[i-2];
        }
        return dp[n];
    }
};
```

## 思路
動態規劃，走到當前格子的方法，可以前兩格或是前一格走過來

## 複雜度
時間O(n)
空間O(n)

