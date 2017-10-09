# 33. Search in Rotated Sorted Array 

[Description](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int is_low(vector<int>& nums, int i) {
        int N = nums.size();
        if( (i == 0 && nums[i] < nums[i+1]) ||
        (i == N-1 && nums[i-1] > nums[i]) ||
        (nums[i-1] > nums[i] && nums[i] < nums[i+1]) ) return 0;
        else if(nums[0] > nums[i]) {
            return -1;
        }
        else { // if(nums[0] < nums[i]) {
            return +1;
        }
    }
    int find_low(vector<int>& nums) {
        int lo = 0, hi = nums.size();
        while(lo < hi) {
            int mid = lo + (hi-lo)/2;
            int status = is_low(nums, mid);
            if(status == 0) return mid;
            else if(status < 0) {
                hi = mid;
            }
            else {
                lo = mid + 1;
            }
        }
        return 0;
    }
    int bisearch(vector<int>& nums, int lo, int hi, int target) {
        while(lo <= hi) {
            int mid = lo + (hi-lo)/2;
            if(nums[mid] == target) return mid;
            else if(nums[mid] > target) hi = mid-1;
            else  lo = mid + 1;
        }
        return -1;
    }
    int search(vector<int>& nums, int target) {
        int idx = find_low(nums);
        int ans = bisearch(nums, 0, idx-1, target);
        if(ans >= 0) return ans;
        ans = bisearch(nums, idx, nums.size()-1, target);
        if(ans >= 0) return ans;
        return -1;
    }
};
```

## 思路
找到最低點後，對兩側做binary search

## 複雜度
O(logn)

## 解法二
```C++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int N = nums.size();
        int lo = 0, hi = N-1;
        // Find lowest element
        while(lo < hi) {
            int mid = lo + (hi - lo)/2;
            if(nums[mid] > nums[hi]) lo = mid + 1;
            else hi = mid;
        }
        // lo == hi, the smallest element
        int rot = lo;
        lo = 0;
        hi = N-1;
        while(lo <= hi) {
            int mid = lo + (hi - lo)/2;
            int realmid = (mid + rot) % N;
            if(nums[realmid] == target) return realmid;
            else if(nums[realmid] < target) lo = mid + 1;
            else hi = mid - 1;
        }
        return -1;
    }
};
```
## 思路

## 複雜度

## 解法三
```C++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int N = nums.size();
        int lo = 0, hi = N-1;
        while(lo <= hi) {
            int mid = lo + (hi-lo)/2;
            if(nums[mid] == target) return mid;
            if(nums[mid] >= nums[lo]) {
                if(nums[lo] <= target && target < nums[mid])
                    hi = mid-1;
                else
                    lo = mid+1;
            }
            else {
                if(nums[mid] < target && target <= nums[hi])
                    lo = mid+1;
                else 
                    hi = mid-1;
            }
        }
        return -1;
    }
};
```