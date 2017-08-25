# 598. Range Addition II 

[Description](https://leetcode.com/problems/range-addition-ii/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int maxCount(int m, int n, vector<vector<int>>& ops) {
        if(ops.size() == 0 || ops[0].size() == 0)
            return m * n;
        int row = m;
        int col = n;
        for(auto& op: ops) {
            row = min(row, op[0]);
            col = min(col, op[1]);
        }
        return row * col;
    }
};
```

## 思路
每次取的範圍一定是交集，trivial
## 複雜度
O(n)