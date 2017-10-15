# 665. Non-decreasing Array

[Description](https://leetcode.com/problems/non-decreasing-array/description/)

## First Attemp = 解法一
```C++class Solution {
public:
    bool checkPossibility(vector<int>& nums) {
        int ans = 0;
        for(int i=0; i<nums.size()-1; ++i) {
            if(nums[i] > nums[i+1]) {
                if(i == 0) {
                    nums[i] = nums[i+1];
                }
                else if(i == nums.size()-2) {
                    nums[i+1] = nums[i];
                }
                else if(nums[i-1] < nums[i+1]) {
                    nums[i] = nums[i-1];
                }
                else {
                    nums[i+1] = nums[i];
                }
                ++ans;
            }
        }
        return ans <= 1;
    }
};
```

## 思路
用貪心法盡量更新數值，注意邊界條件

## 複雜度
O(n)

## 解法二
```C++
public:
    bool checkPossibility(vector<int>& nums) {
        int cnt = 0;                                                                    //the number of changes
        for(int i = 1; i < nums.size() && cnt<=1 ; i++){
            if(nums[i-1] > nums[i]){
                cnt++;
                if(i-2<0 || nums[i-2] <= nums[i])nums[i-1] = nums[i];                    //modify nums[i-1] of a priority
                else nums[i] = nums[i-1];                                                //have to modify nums[i]
            }
        }
        return cnt<=1;
    }
};
```
## 思路

## 複雜度