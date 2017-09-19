# 89. Gray Code 

[Description](https://leetcode.com/problems/gray-code/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    vector<int> grayCode(int n) {
        vector<int> ans(1, 0);
        recur_add(ans, n);
        return ans;
    }
    void recur_add(vector<int>& arr, int n) {
        if(n == 0) return;
        recur_add(arr, n-1);
        int filter = 1 << (n-1);
        for(int i = arr.size() - 1; i >= 0; --i)
            arr.push_back(filter ^ arr[i]);
    }
};
```
## 思路
遞迴，反覆從底部跟變換一位

## 複雜度
O(2^n)

## 解法二
```C++
```
## 思路

## 複雜度