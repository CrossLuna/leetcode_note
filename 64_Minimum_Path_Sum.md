#

[Description]()

## First Attemp = 解法一
```C++
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        if(grid.size() == 0 || grid[0].size() == 0) return 0;
        int h = grid.size();
        int w = grid[0].size();
        for(int j=1; j<w; ++j) grid[0][j] += grid[0][j-1];
        for(int i=1; i<h; ++i) grid[i][0] += grid[i-1][0];
        for(int i=1; i<h; ++i) {
            for(int j=1; j<w; ++j) {
                grid[i][j] += min(grid[i-1][j], grid[i][j-1]);
            }
        }
        return grid[h-1][w-1];
    }
};
```

## 思路
動態規劃

## 複雜度
O(mn)

## 解法二
```C++
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        vector<int> cur(m, grid[0][0]);
        for (int i = 1; i < m; i++)
            cur[i] = cur[i - 1] + grid[i][0]; 
        for (int j = 1; j < n; j++) {
            cur[0] += grid[0][j]; 
            for (int i = 1; i < m; i++)
                cur[i] = min(cur[i - 1], cur[i]) + grid[i][j];
        }
        return cur[m - 1];
    }
};
```
## 思路
不更改原陣列，用一個vector儲存狀態