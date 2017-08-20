#289. Game of Life 

[Description](https://leetcode.com/problems/game-of-life/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool isvalid(vector<vector<int>>& board, int x, int y) {
        int row = board.size();
        int col = board[0].size();
        return 0 <= x && x < row && 0 <= y && y < col;
    }
    bool is_live_before(int n) {
        return n == 1 || n == 4 || n == 5;
    }
    bool is_live_after(int n) {
        return n == 3 || n == 5;
    }

    int count_live_neighbor(vector<vector<int>>& board, int x, int y) {
        int cnt = 0;
        if(isvalid(board, x-1, y-1) && is_live_before(board[x-1][y-1])) cnt++;
        if(isvalid(board, x-1, y  ) && is_live_before(board[x-1][y  ])) cnt++;
        if(isvalid(board, x-1, y+1) && is_live_before(board[x-1][y+1])) cnt++;
        if(isvalid(board, x  , y-1) && is_live_before(board[x  ][y-1])) cnt++;
        if(isvalid(board, x  , y+1) && is_live_before(board[x  ][y+1])) cnt++;
        if(isvalid(board, x+1, y-1) && is_live_before(board[x+1][y-1])) cnt++;
        if(isvalid(board, x+1, y  ) && is_live_before(board[x+1][y  ])) cnt++;
        if(isvalid(board, x+1, y+1) && is_live_before(board[x+1][y+1])) cnt++;
        return cnt;
    }

    void update(vector<vector<int>>& board, int x, int y) {
        int cnt = count_live_neighbor(board, x, y);
        if(is_live_before(board[x][y])) {
            if(cnt < 2)                   board[x][y] = 4;
            else if(cnt == 2 || cnt == 3) board[x][y] = 5;
            else if(cnt > 3)              board[x][y] = 4;
        }
        else {
            if(cnt == 3)                  board[x][y] = 3;
            else                          board[x][y] = 2;
        }
        
    }
    
    void gameOfLife(vector<vector<int>>& board) {
        if(board.size() == 0 || board[0].size() == 0) return;
        for(int i=0; i<board.size(); ++i) {
            for(int j=0; j<board[0].size(); ++j) {
                update(board, i, j);
            }
        }
        for(int i=0; i<board.size(); ++i) {
            for(int j=0; j<board[0].size(); ++j) {
                if(is_live_after(board[i][j])) board[i][j] = 1;
                else                           board[i][j] = 0;
            }
        }
    }
};

```
## 思路
用別的數字狀態來存

## 檢討
1. 變數名記得不要打錯
2. Typo要注意

## 解法二
```C++
void gameOfLife(vector<vector<int>>& board) {
    int m = board.size(), n = m ? board[0].size() : 0;
    for (int i=0; i<m; ++i) {
        for (int j=0; j<n; ++j) {
            int count = 0;
            for (int I=max(i-1, 0); I<min(i+2, m); ++I)
                for (int J=max(j-1, 0); J<min(j+2, n); ++J)
                    count += board[I][J] & 1;
            if (count == 3 || count - board[i][j] == 3)
                board[i][j] |= 2;
        }
    }
    for (int i=0; i<m; ++i)
        for (int j=0; j<n; ++j)
            board[i][j] >>= 1;
}

```
## 思路
可以學習的邊界routine
```C++
// position: (i, j)
for(int I = max(i-1, 0); I < min(i+2, m); ++I) {
    for(int J = max(j-1, 0); J < min(j+2, n); ++J) {
        // 沒有排除自己那一格，需要注意
    }
}
```