# 746. Min Cost Climbing Stairs

[Description](https://leetcode.com/problems/min-cost-climbing-stairs/description/)

## 解法一
```C++
class Solution {
public:
    int minCostClimbingStairs(vector<int>& cost) {
        int N = cost.size();
        vector<int> dp(N+1, 0);
        dp[0] = 0;
        dp[1] = 0;
        for(int i=2; i<=N; ++i) {
            dp[i] = min(dp[i-1] + cost[i-1],dp[i-2] + cost[i-2]);
        }
        return dp[N];
    }
};
```

## 思路
動態規劃，每次回頭看一格或兩格，看哪個成本低

## 複雜度
時間複雜度O(n)
空間複雜度O(n)
