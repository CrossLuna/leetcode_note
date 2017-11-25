# 280. Wiggle Sort

[Description](https://leetcode.com/problems/wiggle-sort/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    void wiggleSort(vector<int>& nums) {
        if(nums.size() <= 1) return;
        bool up = true;
        for(int i=0; i<nums.size()-1; ++i) {
            if(up) {
                if(nums[i] > nums[i+1]) {
                    swap(nums[i], nums[i+1]);
                }
            }
            else { // down
                if(nums[i] < nums[i+1]) {
                    swap(nums[i], nums[i+1]);
                }
            }
            up = !up;
        }
    }
};
```

## 思路
一次遍歷，交換順序

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度