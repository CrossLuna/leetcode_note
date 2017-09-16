# 477. Total Hamming Distance 
[Description](https://leetcode.com/problems/total-hamming-distance/description/)

## First Attemp
```C++
class Solution {
public:
    int count_one(int n) {
        int ans = 0;
        while(n) {
            n &= (n-1);
            ++ans;
        }
        return ans;
    }
    int hamming_dist(int a, int b) {
        return count_one(a ^ b);
    }
    int totalHammingDistance(vector<int>& nums) {
        int ans = 0;
        for(int i=0; i<nums.size(); ++i) {
            for(int j=i+1; j<nums.size(); ++j) {
                ans += hamming_dist(nums[i], nums[j]);
            }
        }
        return ans;
    }
};
```
TLE

## 思路

## 複雜度
O(n^2)

## 解法二
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
    int totalHammingDistance(vector<int>& nums) {
        int N = nums.size();
        int filter = 1;
        int ans = 0;
        while(filter) {
            int ones = count_ones(nums, filter);
            ans += ones * (N - ones);
            filter <<= 1;
        }
        return ans;
    }
};
```
## 思路
觀察Hamming距離如何造成，對於每一位統計0數和1數相乘即是可以產生的Hamming距離

## 複雜度
O(nlogn)