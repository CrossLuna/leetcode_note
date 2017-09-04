#

[Description]()

## 解法一
```C++
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        if(matrix.size() == 0 || matrix[0].size() == 0) return;
        int row = matrix.size();
        int col = matrix[0].size();
        bool fc_zero = false;
        bool fr_zero = false;
        for(int c=0; c<col; ++c)
            if(matrix[0][c] == 0)
                fr_zero = true;
        for(int r=0; r<row; ++r)
            if(matrix[r][0] == 0)
                fc_zero = true;
        
        for(int r=1; r<row; ++r) {
            for(int c=1; c<col; ++c) {
                if(matrix[r][c] == 0) {
                    matrix[r][0] = 0;
                    matrix[0][c] = 0;
                }
            }
        }

        for(int r=1; r<row; ++r) {
            for(int c=1; c<col; ++c) {
                if(matrix[r][0] == 0 || matrix[0][c] == 0)
                    matrix[r][c] = 0;
            }
        }

        if(fc_zero) {
            for(int r=0; r<row; ++r) matrix[r][0] = 0;
        }
        if(fr_zero) {
            for(int c=0; c<col; ++c) matrix[0][c] = 0;
        }
    }
};
```

## 思路
利用首行首列來標記是不是清零

## 複雜度
O(mn)，空間複雜度O(1)

## 反思
矩陣或是陣列要用到空間複雜度O(1)，都必須想想怎麼使用現有位置儲存資訊

## 解法二
```C++
```
## 思路
空間複雜度O(mn)，O(m+n)，比較trivial

## 複雜度