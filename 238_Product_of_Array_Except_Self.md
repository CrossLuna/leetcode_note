# 238. Product of Array Except Self 

[Description](https://leetcode.com/problems/product-of-array-except-self/description/)

## 解法一
```C++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int N = nums.size();
        vector<int> slow(N, 1);
        for(int i=1; i<N; ++i) {
            slow[i] = slow[i-1] * nums[i-1];
        }
        vector<int> fast(N, 1);
        for(int i=N-2; i>=0; --i) {
            fast[i] = fast[i+1] * nums[i+1];
        }
        vector<int> ans;
        for(int i=0; i<N; ++i) {
            ans.push_back(slow[i] * fast[i]);
        }
        return ans;
    }
};
```

## 思路
維護兩個array，一個從前算，一個從後算

## 複雜度
O(n)

## 解法二
```C++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int N = nums.size();
        int fromBegin = 1;
        int fromLast = 1;
        vector<int> res(N,1);
        
        for(int i=0; i<N; i++){
            res[i] *= fromBegin;
            fromBegin *= nums[i];
            res[n-1-i] *= fromLast;
            fromLast *= nums[n-1-i];
        }
        return res;
    }
};
```
## 思路
改成使用兩個變數紀錄

## 複雜度
O(n)