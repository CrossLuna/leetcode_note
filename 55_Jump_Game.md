# 55. Jump Game

[Description](https://leetcode.com/problems/jump-game/description/)

## First Attemp
```C++
class Solution {
public:
    bool canJump(vector<int>& nums) {
        if(nums.size() == 0) return true;
        int N = nums.size();
        int max_dist = nums[0];
        while(i < N && i <= max_dist) {
            max_dist = max(max_dist, i + nums[i]);
        }
        if(max_dist >= N-1) return true;
        return false;
    }
};
```
## 反省
1. 注意變數是否宣告
2. 注意變數是否遞增

## 解法一
```C++
class Solution {
public:
    bool canJump(vector<int>& nums) {
        if(nums.size() == 0) return true;
        int N = nums.size();
        int max_dist = nums[0];
        int i = 0;
        while(i < N && i <= max_dist) {
            max_dist = max(max_dist, i + nums[i]);
            i++;
        }
        if(max_dist >= N-1) return true;
        return false;
    }
};
```

## 思路
用貪心算法，還沒到max_dist的每一格都往下算最遠能到之處

## 複雜度
O(n)

## 解法二
```C++
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int n = nums.size();
        int i = 0;
        for (int reach = 0; i < n && i <= reach; ++i)
            reach = max(i + nums[i], reach);
        return i == n;
    }
};
```
## 思路
隨時思考如何精簡代碼