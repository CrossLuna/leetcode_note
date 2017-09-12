# 560. Subarray Sum Equals K 

[Description](https://leetcode.com/problems/subarray-sum-equals-k/description/)

## First Attemp = 解法一
```C++
```

## 思路
暴力解

## 複雜度

## 解法二
```C++
class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        unordered_map<int, int> m;
        m[0] = 1;
        int sum = 0;
        int ans = 0;
        for(int i=0; i<nums.size(); ++i) {
            sum += nums[i];
            ans += m[sum-k];
            ++m[sum];
        }
        return ans;
    }
};
```
## 思路
用hashmap儲存前方已經有的值，記得連續子序列的話，不是指針就是hashmap

## 複雜度