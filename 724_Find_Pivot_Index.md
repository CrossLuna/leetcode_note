# 724. Find Pivot Index

[Description](https://leetcode.com/problems/find-pivot-index/description/)

## 解法一
```C++
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int right_sum = accumulate(nums.begin(), nums.end(), 0);
        int left_sum = 0;
        for(int i=0; i<nums.size(); ++i) {
            right_sum -= nums[i];
            if(left_sum == right_sum) return i;
            left_sum += nums[i];
        }
        return -1;
    }
};
```

## 思路
先取總和，再比較左右和，每次循環左加右扣，注意右邊比較前需要先扣。

## 複雜度
時間複雜度O(n)，two pass  
空間複雜度O(1)
