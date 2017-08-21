# 376. Wiggle Subsequence 

[Description](https://leetcode.com/problems/wiggle-subsequence/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        if(nums.size() <= 1) return nums.size();
        int i = 1;
        int ans = 1;
        int cur = nums[0];
        int status = 0; // 1: up , 2: down
        while(i < nums.size()) {
            if(status == 0) {
                if(cur < nums[i]) {
                    status = 1;
                    ans++;
                }
                else if(cur > nums[i]) {
                    status = 2;
                    ans++;
                }
            }
            if(status == 1) { // UP
                if(cur > nums[i]) {
                    status = 2;
                    ans++;
                }
            }
            else if(status == 2) { // DOWN
                if(cur < nums[i]) {
                    status = 1;
                    ans++;
                }
            }
            cur = nums[i];
            i++;
        }
        return ans;
    }
};
```
## 思路
貪心策略，沿路檢查

## 解法二
```C++
```
## 思路