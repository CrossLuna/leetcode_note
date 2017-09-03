# 300. Longest Increasing Subsequence 

[Description](https://leetcode.com/problems/longest-increasing-subsequence/description/)

## 解法一
```C++
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        if(nums.empty()) return 0;
        vector<int> dp(nums.size(), 1);
        for(int i=0; i<nums.size(); ++i) {
            for(int j=0; j<i; ++j) {
                if(nums[j] < nums[i]) {
                    dp[i] = max(dp[i], 1+dp[j]);
                }
            }
        }
        int max_LIS = dp[0];
        for(int i=1; i<dp.size(); ++i) max_LIS = max(max_LIS, dp[i]);
        return max_LIS;
    }
};
```

## 思路
經典動態規劃

## 複雜度
O(n^2)

## 解法二
```C++
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        vector<int> arr;
        for(int n: nums) {
            if(arr.empty() || n > arr.back()) arr.push_back(n);
            else {
                auto it = lower_bound(arr.begin(), arr.end(), n);
                *it = n;
            }
        }
        return arr.size();
    }
};
```
## 思路
使用二分搜尋輔助加快，為什麼要替換？因為可以找出同樣長度的LIS但允許後續更多增長的空間

## 複雜度
O(nlogn)