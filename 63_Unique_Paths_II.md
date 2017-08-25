# 63. Unique Paths II 

[Description](https://leetcode.com/problems/unique-paths-ii/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        if (obstacleGrid.size() == 0 or obstacleGrid[0].size() == 0) return 0;
        int row = obstacleGrid.size();
        int col = obstacleGrid[0].size();
        vector<vector<int>> m (row, vector<int>(col, 0));
        bool obstacled = false;
        for(int j=0; j<col; ++j) {
            if(obstacleGrid[0][j] == 1)  {
                obstacled = true;
            }
            if(obstacled) {
                m[0][j] = 0;
            }
            else {
                m[0][j] = 1;
            }
        }
        obstacled = false;
        for(int i=0; i<row; ++i) {
            if(obstacleGrid[i][0] == 1)  {
                obstacled = true;
            }
            if(obstacled) {
                m[i][0] = 0;
            }
            else {
                m[i][0] = 1;
            }
        }
        for(int i=1; i<row; ++i) {
            for(int j=1; j<col; ++j) {
                if(obstacleGrid[i][j] == 1) {
                    m[i][j] = 0;
                }
                else {
                    m[i][j] = m[i-1][j] + m[i][j-1];
                }
            }
        }
        return m[row-1][col-1];
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
    int uniquePathsWithObstacles(vector<vector<int> > &obstacleGrid) {
        int m = obstacleGrid.size() , n = obstacleGrid[0].size();
        vector<vector<int>> dp(m+1,vector<int>(n+1,0));
        dp[0][1] = 1;
        for(int i = 1 ; i <= m ; ++i)
            for(int j = 1 ; j <= n ; ++j)
                if(!obstacleGrid[i-1][j-1])
                    dp[i][j] = dp[i-1][j]+dp[i][j-1];
        return dp[m][n];
    }
};
```
## 思路
向量加一列可以拯救人生，創造簡潔的代碼

## 複雜度