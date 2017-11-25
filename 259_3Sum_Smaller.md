# 259. 3Sum Smaller 

[Description](https://leetcode.com/problems/3sum-smaller/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int threeSumSmaller(vector<int>& nums, int target) {
        int ans = 0;
        if(nums.size() < 3) return ans;
        sort(nums.begin(), nums.end());
        for(int i=0; i<nums.size()-2; ++i) {
            int left = i+1;
            int right = nums.size()-1;
            int sum = nums[i] + nums[left] + nums[right];
            while(true) {
                if(sum < target) {
                    //[left, right) all feasible
                    ans += right - left;
                    sum -= nums[left++];
                    if(left >= right) break;
                    sum += nums[left];
                }
                else { // sum >= target
                    sum -= nums[right--];
                    if(left >= right) break;
                    sum += nums[right];
                }
            }
        }
        return ans;
    }
};
```

## 思路
雙指針

## 複雜度
O(N^2)

## 解法二
```C++
class Solution {
public:
    int threeSumSmaller(vector<int>& nums, int target) {
        int ans = 0;
        if(nums.size() < 3) return ans;
        sort(nums.begin(), nums.end());
        for(int i=0; i<nums.size()-2; ++i) {
            int left = i+1;
            int right = nums.size()-1;
            while(left < right) {
                if(nums[i] + nums[left] + nums[right] < target) {
                    ans += (right - left);
                    ++left;
                }
                else { // sum >= target
                    --right;
                }
            }
        }
        return ans;
    }
};
```
## 思路
寫法改進

## 複雜度