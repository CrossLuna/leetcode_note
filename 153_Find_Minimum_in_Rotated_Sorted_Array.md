#153. Find Minimum in Rotated Sorted Array 

[Description](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int findMin(vector<int>& nums) {
        int min_idx = 0;
        for(int i=0; i<nums.size()-1; ++i) {
            if(nums[i] > nums[i+1]) {
                min_idx = i+1;
                break;
            }
        }
        return nums[min_idx];
    }
};
```

## 思路
線性搜索，複雜度O(n)

## 解法二
```C++
class Solution {
public:
    int findMin(vector<int>& nums) {
        int lo = 0;
        int hi = nums.size() - 1;
        while(lo < hi) {
            int mi = lo + (hi - lo)/2;
            if(nums[mi] > nums[mi + 1]) {
                return nums[mi + 1];
            }
            else if(nums[lo] < nums[mi]) { // fall on right
                lo = mi + 1;
                
            }
            else { // nums[lo] > nums[mi], fall on left
                hi = mi;
            }
        }
        return nums[0];
    }
};
```

## 思路
二分搜索，O(logn)，注意邊界條件