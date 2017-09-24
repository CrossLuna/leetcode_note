# 200. Number of Islands 

[Description](https://leetcode.com/problems/number-of-islands/discuss/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool is_valid(vector<vector<char>>& grid, int x, int y) {
        int row = grid.size();
        int col = grid[0].size();
        return 0 <= x && x < row && 0 <= y && y < col;
    }
    bool is_ocean(vector<vector<char>>& grid, int x, int y) {
        return !is_valid(grid, x, y) || grid[x][y] == '0';
    }
    bool visited(vector<vector<char>>& grid, int x, int y) {
        return grid[x][y] == '2';
    }
    void dfs(vector<vector<char>>& grid, int x, int y) {
        grid[x][y] = '2';
        if(!is_ocean(grid, x+1, y) && !visited(grid, x+1, y)) dfs(grid, x+1, y);
        if(!is_ocean(grid, x-1, y) && !visited(grid, x-1, y)) dfs(grid, x-1, y);
        if(!is_ocean(grid, x, y+1) && !visited(grid, x, y+1)) dfs(grid, x, y+1);
        if(!is_ocean(grid, x, y-1) && !visited(grid, x, y-1)) dfs(grid, x, y-1);
    }
    int numIslands(vector<vector<char>>& grid) {
        if(grid.empty() || grid[0].empty()) return 0;
        int cnt = 0;
        for(int i=0; i<grid.size(); ++i) {
            for(int j=0; j<grid[0].size(); ++j) {
                if(!is_ocean(grid, i, j) && !visited(grid, i, j)) {
                    dfs(grid, i, j);
                    ++cnt;
                }
            }
        }
        return cnt;
    }
};
```

## 思路
DFS

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度