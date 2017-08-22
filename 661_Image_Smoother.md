#

[Description]()

## First Attemp = 解法一
```C++
class Solution {
public:
    vector<vector<int>> imageSmoother(vector<vector<int>>& M) {
        if(M.size() == 0 || M[0].size() == 0) 
            return vector<vector<int>>{};
        int row = M.size();
        int col = M[0].size();
        vector<vector<int>> ans(row, vector<int> (col, 0));
        
        for(int i=0; i<row; ++i){
            for(int j=0; j<col;++j) {
                int cnt = 0;
                int sum = 0;
                
                for(int x=max(0, i-1); x<min(row, i+2); ++x) {
                    for(int y=max(0, j-1); y<min(col, j+2); ++y) {
                        ++cnt;
                        sum += M[x][y];
                    }
                }
                ans[i][j] = sum/cnt;
            }
        }
        

        return ans;
        
    }
};
```

## 思路
1. 多層迴圈注意變數名稱
2. check邊界用的routine要正確搞熟
3. vector的初始化方法，除了指定元素用{}，其餘都用()，以免掉到坑裡


## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度