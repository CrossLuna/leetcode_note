# 74. Search a 2D Matrix
[Description](https://leetcode.com/problems/search-a-2d-matrix/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if(matrix.size() == 0 || matrix[0].size() == 0) return false;
        vector<int> first_col;
        for(auto& row: matrix) first_col.push_back(row[0]);
        auto target_row = upper_bound(first_col.begin(), first_col.end(), target);
        if(target_row == first_col.begin()) return false;
        --target_row;
        int idx = target_row - first_col.begin();
        return binary_search(matrix[idx].begin(), matrix[idx].end(), target);
    }
};
```

## 思路
先比第一column，再比同一row

## 複雜度
O(log sqrt(n))
空間複雜度O(sqrt(n))

## 解法二
```C++
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if(matrix.empty() || matrix[0].empty()) return false;
        int start = 0;
        int n_row = matrix.size();
        int n_col = matrix[0].size();
        int end = n_row * n_col;
        while(start < end) {
            int mid = start + (end - start)/2;
            int mid_val = matrix[mid / n_col][mid % n_col];
            if(mid_val == target) return true;
            else if(mid_val < target) {
                start = mid + 1;
            }
            else {
                end  = mid;
            }
        }
        return false;
    }
};
```
## 思路
把整個2D矩陣當成已排序陣列

## 複雜度
O(logn)