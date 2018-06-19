# 118. Pascal's Triangle

[Description](https://leetcode.com/problems/pascals-triangle/description/)

## 解法一
```C++
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> ans;
        if(numRows < 1) return ans;
        ans.push_back({1});
        if(numRows < 2) return ans;
        ans.push_back({1, 1});
        for(int n=2; n<numRows; ++n) {
            ans.push_back({1});
            for(int i=0; i<ans[n-1].size()-1; ++i) {
                ans[n].push_back(ans[n-1][i] + ans[n-1][i+1]);
            }
            ans[n].push_back(1);
        }
        return ans;
    }
};
```

## 思路
按照題目，小心實作

## 複雜度
O(n^2)，相當於三角形的項數

## 解法二
```C++
```
## 思路

## 複雜度