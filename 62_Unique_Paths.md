# 62. Unique Paths 

[Description](https://leetcode.com/problems/unique-paths/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int uniquePaths(int m, int n) {
        vector<int> curr(n+1);
        vector<int> next(n+1);
        curr[1] = 1;
        for(int i=1; i<=m; ++i) {
            for(int j=1; j<=n; ++j) {
                next[j] = next[j-1] + curr[j];
            }
            swap(curr, next);
        }
        return curr.back();
    }
};
```

## 思路
動態規劃

## 複雜度
時間複雜度O(m*n)
空間複雜度O(n)

## 解法二
```C++
```
## 思路

## 複雜度