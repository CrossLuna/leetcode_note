# 278. First Bad Version 

[Description](https://leetcode.com/problems/first-bad-version/description/)

## First Attemp = 解法一
```C++
// Forward declaration of isBadVersion API.
bool isBadVersion(int version);

class Solution {
public:
    int firstBadVersion(int n) {
        if(n == 1) return 1;
        int low = 1, high = n;
        while(low <= high) {
            int mid = low + (high-low)/2;
            if(isBadVersion(mid)) {
                if(mid == low) return low;
                else if(!isBadVersion(mid-1)) return mid;
                else high = mid;
            }
            else {
                low = mid + 1;
            }
        }
        return low;
    }
};
```

## 思路
Binary Search

## 複雜度
O(log n)

## 解法二
```Java
public int firstBadVersion(int n) {
    int start = 1, end = n;
    while (start < end) {
        int mid = start + (end-start) / 2;
        if (!isBadVersion(mid)) start = mid + 1;
        else end = mid;            
    }        
    return start;
}
```
## 思路

## 複雜度