# 377. Combination Sum IV 

[Description](https://leetcode.com/problems/combination-sum-iv/description/)

## First Attemp
```C++
class Solution {
public:
    void recur(vector<int>& nums, int target, int& cur_sum, int& ans) {
        if(cur_sum == target) { 
            ++ans;
            return;
        }
        int N = nums.size();
        for(int i=0; i<N; ++i) {
            if(cur_sum + nums[i] > target) break;
            cur_sum += nums[i];
            recur(nums, target, cur_arr, cur_sum, ans);
            cur_sum -= nums[i];
        }
    }

    int combinationSum4(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        int ans = 0;
        int cur_sum = 0;
        recur(nums, target, arr, cur_sum, ans);
        return ans;
    }
};
```
LTE

## 思路

## 複雜度

## 解法一
```C++
class Solution {
public:
    int combinationSum4(vector<int>& nums, int target) {
        vector<int> dp(target + 1, 0);
        dp[0] = 1;
        for(int t=1; t<=target; ++t) {
            for(auto n: nums) {
                if(t - n >= 0) dp[t] += dp[t-n];
            }
        }
        return dp[target];
    }
};
```
## 思路
經典DP，要稍微想一下為什麼可以用這個DP

## 複雜度
O(target * N)
