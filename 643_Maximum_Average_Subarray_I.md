# 643. Maximum Average Subarray I 

[Description](https://leetcode.com/problems/maximum-average-subarray-i/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        long long sum = 0;
        for(int i=0; i<k; ++i)
            sum += nums[i];
        double ans = static_cast<double>(sum)/k;
        for(int i=k; i<nums.size(); ++i) {
            sum -= nums[i-k];
            sum += nums[i];
            ans = max(ans, static_cast<double>(sum)/k);
        }
        return ans;
    }
};
```

## 思路
Sliding window

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度