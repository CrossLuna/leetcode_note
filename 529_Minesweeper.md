# 529. Minesweeper

[Description](https://leetcode.com/problems/minesweeper/description/)

## First Attemp
```C++
class Solution {
public:
    static vector<vector<int>> dis_vec {
        {-1, -1},
        {-1, 0},
        {-1, 1},
        {0, -1},
        {0, 1},
        {1, -1},
        {1, 0},
        {1, 1}
    };

    vector<vector<char>> updateBoard(vector<vector<char>>& board, vector<int>& click) {
        int h = board.size();
        int w = board[0].size();
        if(board[click[0]][click[1]] == 'M') {
            board[click[0]][click[1]] = 'X';
            return board;
        }
        queue<vector<int>> q;
        visit(board, click, q, h, w);
        while(!q.empty()) {
            auto pos = q.front();
            if(board[pos[0]][pos[1]] == 'E') {
                visit(board, pos, q, h, w);
            }
            q.pop();
        }
        return board;
    }

    bool isvalid(vector<int>&pos, int height, int weight) {
        return 0 <= pos[0] && pos[0] < height && 0 <= pos[1] && pos[1] < weight;
    }

    void visit(vector<vector<char>>& board, vector<int>& pos, queue<vector<int>& q, int h, int w) {
        queue<vector<int>> temp_q;
        int cnt_mine = 0;
        for(auto dis : dis_vec) {
            int x = pos[0] + dis[0];
            int y = pos[1] + dis[1];
            if(isvalid({x, y}, h, w)) {
                if(board[x][y] == 'M') {
                    ++cnt_mine;
                }
                else if(board[x][y] == 'E') {
                    temp_q.push({x, y});
                }
            }
        }

        if(cnt_mine > 0) {
            board[x][y] = '0' + cnt_mine;
        }
        else {
            while(!temp_q.empty()) {
                q.push(temp_q.front());
                temp_q.pop();
            }
            board[x][y] = 'B';
        }

    }
}; 
```

## 思路
圖的遍歷 BFS，照著做即可

## 解法一
```C++
class Solution {
public:
    vector<vector<char>> updateBoard(vector<vector<char>>& board, vector<int>& click) {
        vector<vector<int>> dis_vec {
            {-1, -1},
            {-1, 0},
            {-1, 1},
            {0, -1},
            {0, 1},
            {1, -1},
            {1, 0},
            {1, 1}
        };
        int h = board.size();
        int w = board[0].size();
        if(board[click[0]][click[1]] == 'M') {
            board[click[0]][click[1]] = 'X';
            return board;
        }
        queue<vector<int>> q;
        visit(board, click, q, h, w, dis_vec);
        while(!q.empty()) {
            auto pos = q.front();
            if(board[pos[0]][pos[1]] == 'E') {
                visit(board, pos, q, h, w, dis_vec);
            }
            q.pop();
        }
        return board;
    }

    bool isvalid(const vector<int>&pos, int height, int weight) {
        return 0 <= pos[0] && pos[0] < height && 0 <= pos[1] && pos[1] < weight;
    }

    void visit(vector<vector<char>>& board, vector<int>& pos, queue<vector<int>>& q, int h, int w,  vector<vector<int>>& dis_vec) {
        queue<vector<int>> temp_q;
        int cnt_mine = 0;
        for(auto dis : dis_vec) {
            int x = pos[0] + dis[0];
            int y = pos[1] + dis[1];
            if(isvalid({x, y}, h, w)) {
                if(board[x][y] == 'M') {
                    ++cnt_mine;
                }
                else if(board[x][y] == 'E') {
                    temp_q.push({x, y});
                }
            }
        }

        if(cnt_mine > 0) {
            board[pos[0]][pos[1]] = '0' + cnt_mine;
        }
        else {
            while(!temp_q.empty()) {
                q.push(temp_q.front());
                temp_q.pop();
            }
            board[pos[0]][pos[1]] = 'B';
        }

    }
}; 
```

## 複雜度
o(格子數量)

## 檢討
1. static 變數的用法要複習
2. 各項常用資料結構的初始化方法要熟記
3. 注意各項變數名稱
4. 記得return東西

# TODO: 參考別人解法
