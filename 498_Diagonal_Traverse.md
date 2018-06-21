# 498. Diagonal Traverse

[Description](https://leetcode.com/problems/diagonal-traverse/description/)

## 解法一
```C++
class Solution {
public:
    vector<int> findDiagonalOrder(vector<vector<int>>& matrix) {
        vector<int> ans;
        if(matrix.size() == 0 || matrix[0].size() == 0) return ans;
        int rows = matrix.size();
        int cols = matrix[0].size();
        ans.reserve(rows * cols);
        bool up = true;
        for(int sum = 0; sum < cols+rows-1; ++sum) {
            if(up) {
                int i = sum < rows? sum: rows-1;
                int j = sum - i;
                while(i >= 0 && j < cols) {
                    ans.push_back(matrix[i--][j++]);
                }
                up = false;
            }
            else {
                int i = sum < cols? 0: sum-cols+1;
                int j = sum - i;
                while(i < rows && j >= 0){
                    ans.push_back(matrix[i++][j--]);
                }
                up = true;
            }
        }
        
        return ans;
    }
};
```

## 思路
仔細觀察x起始值，用sum來控制y值

## 複雜度
O(m*n)

## 解法二
```C++
```
## 思路

## 複雜度