#130. Surrounded Regions  

[Description](https://leetcode.com/problems/surrounded-regions/description/)

## First Attemp
```C++
class Solution {
public:
    typedef array<int, 2> pos2d;
    bool isvalid(int x, int y, int height, int weight) {
        return 0 <= x && x < height && 0 <= y && y < weight;
    }


    bool isvalid(pos2d & pos, int height, int weight) {
        int x = get<0>(pos);
        int y = get<1>(pos);
        return 0 <= x && x < height && 0 <= y && y < weight;
    }

    void Edge_DFS(vector<vector<char>>& board, int x, int y, set<pos2d>& ss) {
        int x = get<0>(pos);
        int y = get<1>(pos);
        int h = board.size();
        int w = board[0].size();
        ss.emplace({get<0>(pos), get<1>(pos)});
        if(isvalid(x+1, y, h, w)) Edge_DFS(board, x+1, y, ss);
        if(isvalid(x-1, y, h, w)) Edge_DFS(board, x-1, y, ss);
        if(isvalid(x, y+1, h, w)) Edge_DFS(board, x, y+1, ss);
        if(isvalid(x, y-1, h, w)) Edge_DFS(board, x, y-1, ss);
    }

    void solve(vector<vector<char>>& board) {
        set<pos2d> ss;
        int h = board.size();
        int w = board[0].size();
        // Along the edge
        for(int i = 0; i<h; ++i) {
            if(board[i][0] == 'O') Edge_DFS(i, 0, ss);
            if(board[i][w-1] == 'O') Edge_DFS(i, w-1, ss);
        }
        for(int j = 0; j < w; ++j) {
            if(board[0][j] == 'O') Edge_DFS(0, j, ss);
            if(board[h-1][j] == 'O') Edge_DFS(h-1, j, ss);
        }

        for(int i=1; i<h-1; ++i) {
            for(int j=1; j<w-1; ++j) {
                pos2d pos {i, j};
                if(board[i][j] == 'O' && ss.find(pos) == ss.end()) board[i][j] = 'X';
            }
        }
    }
};
```

## 解法一
```C++
class Solution {
public:
    typedef array<int, 2> pos2d;
    bool isvalid(int x, int y, int row, int col) {
        return 0 <= x && x < row && 0 <= y && y < col;
    }

    void DFS(vector<vector<char>>& board, int x, int y, set<pos2d>& ss) {
        if(board[x][y] == 'X') return;
        stack<int> s_x;
        stack<int> s_y;
        s_x.push(x);
        s_y.push(y);
        int h = board.size();
        int w = board[0].size();

        while(!s_x.empty()) {
            int xx = s_x.top();
            int yy = s_y.top();
            s_x.pop();
            s_y.pop();
            pos2d pos{xx, yy};
            if(board[xx][yy] == 'O' && ss.find(pos) == ss.end()) {
                ss.insert(pos);
                if(isvalid(xx+1, yy, h, w)) {s_x.push(xx+1); s_y.push(yy);}
                if(isvalid(xx-1, yy, h, w)) {s_x.push(xx-1); s_y.push(yy);}
                if(isvalid(xx, yy+1, h, w)) {s_x.push(xx); s_y.push(yy+1);}
                if(isvalid(xx, yy-1, h, w)) {s_x.push(xx); s_y.push(yy-1);}
            }


        }
    }
    
    void solve(vector<vector<char>>& board) {
        if(board.size() == 0 || board[0].size() == 0) return;
        set<pos2d> ss;
        int h = board.size();
        int w = board[0].size();

        for(int i=0; i<h; ++i) {
            DFS(board, i, 0, ss);
            DFS(board, i, w-1, ss);
        }

        for(int j=0; j<w; ++j) {
            DFS(board, 0, j, ss);
            DFS(board, h-1, j, ss);
        }

        for(int i=1; i<h-1; ++i) {
            for(int j=1; j<w-1; ++j) {
                pos2d pos{i, j};
                if(board[i][j] && ss.find(pos) == ss.end()) board[i][j] = 'X';
            }
        }
    }
};
```

## 思路
DFS

## 檢討
1. DFS遞迴容易溢出，記得迭代
2. routine要寫熟，注意邊界

## 解法二 (參考) TODO
```C++
```

## 思路