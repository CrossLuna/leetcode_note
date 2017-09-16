# 137. Single Number II 

[Description](https://leetcode.com/problems/single-number-ii/description/)

## 解法一
```C++
class Solution {
public:
    int count_ones(vector<int>& nums, int filter) {
        int ans = 0;
        for(auto n: nums) {
            if(n & filter) ++ans;
        }
        return ans;
    }
    int singleNumber(vector<int>& nums) {
        int ans = 0;
        int filter = 1;
        while(filter) {
            int count = count_ones(nums, filter);
            if(count % 3 == 1) ans ^= filter;
            filter <<= 1;
        }
        return ans;
    }
};
```

## 思路
既然沒有單一operation可以直接操作，就分各個位數來數

## 複雜度
O(n*32)

## 解法二
```C++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int ones = 0, twos = 0;
        for(int i=0; i<nums.size(); ++i) {
            ones = (ones ^ nums[i]) & ~twos;
            twos = (twos ^ nums[i]) & ~ones;
        }
        return ones;
    }
};
```
## 思路
考慮每個bit，使用兩個bit來儲存，依序為 00->10->01->00 (ones, twos)，
https://discuss.leetcode.com/topic/2031/challenge-me-thx/11
## 複雜度