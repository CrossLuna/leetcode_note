# 283. Move Zeroes 

[Description](https://leetcode.com/problems/move-zeroes/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int i = 0; // zero
        int j = 0; // non-zero
        int N = nums.size();
        while(i < N && j < N) {
            while(nums[i] != 0 && i < N) ++i;
            while(nums[j] == 0 && j < N) ++j;
            if(i >= N || j >= N) return;
            else if(j < i) ++j;
            else swap(nums[i], nums[j]);
        }
    }
};
```

## 思路
雙指針，注意邊界

## 複雜度
O(n)

## 解法二
```C++
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int j = 0;
        // move all the nonzero elements advance
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != 0) {
                nums[j++] = nums[i];
            }
        }
        for (;j < nums.size(); j++) {
            nums[j] = 0;
        }
    }
};
```
## 思路
先前移，再歸零

## 複雜度