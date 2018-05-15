# 198. House Robber

[Description](https://leetcode.com/problems/house-robber/description/)

## 解法一
```C++
class Solution {
public:
    int rob(vector<int>& nums) {
        int ans = 0;
        int N = nums.size();
        if(N == 0) return ans;
        vector<int> dp(N+1, 0);
        dp[1] = nums[0];
        ans = dp[1];
        if(N == 1) return ans;
        dp[2] = nums[1];
        ans = max(dp[2], ans);
        if(N == 2) return ans;
        for(int i=3; i<=N; ++i) {
            dp[i] = nums[i-1] + max(dp[i-2], dp[i-3]) ;
            ans = max(ans, dp[i]);
        }
        return ans;
    }
};
```

## 思路
動態規劃，如果每次搶了當下房子，前一個就不能搶了，只能搶前兩個或三個，每次搶完更新答案

## 複雜度
時間 O(n)
空間 O(n)

## 解法二
```C++
class Solution {
public:
    int rob(vector<int>& nums) {
        int N = nums.size();
        int a = 0; // Even Position
        int b = 0; // Odd Position
        for(int i=0; i<N; ++i) {
            if(i % 2 == 0) {
                a = max(nums[i] + a, b);
            }
            else {
                b = max(nums[i] + b, a);
            }
        }
        return max(a, b);
    }
};
```
## 思路
兩點不同
1. 紀錄到當前位置為止所有可能的搶法中最大值
2. 分成兩個位置，只紀錄有效的範圍(到前兩格為止)，每次`max`的參數中，第一項為搶，第二項為不搶

## 複雜度
時間 O(n)
空間 O(1)