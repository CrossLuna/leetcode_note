# 240. Search a 2D Matrix II
[Description](https://leetcode.com/problems/search-a-2d-matrix-ii/description/)

## 解法一
```C++
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if(matrix.empty() || matrix[0].empty()) return false;
        int n_row = matrix.size();
        int n_col = matrix[0].size();
        int r = 0;
        int c = n_col - 1;
        while(r < n_row && 0 <= c) {
            if(matrix[r][c] == target) return true;
            else if(matrix[r][c] < target) ++r;
            else --c;
        }
        return false;
    }
};
```

## 思路
Young Tableau的查找操作，關鍵是從右上角開始

## 複雜度
O(n+m)

## 解法二
```C++
```
## 思路

## 複雜度