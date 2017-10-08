# 72. Edit Distance 

[Description](https://leetcode.com/problems/edit-distance/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int minDistance(string word1, string word2) {
        vector<vector<int>> dp (word1.size()+1, vector<int>(word2.size()+1, 0));
        for(int i=1; i<=word1.size(); ++i) {
            dp[i][0] = i;
        }
        for(int j=1; j<=word2.size(); ++j) {
            dp[0][j] = j;
        }
        for(int i=1; i<=word1.size(); ++i) {
            for(int j=1; j<=word2.size(); ++j) {
                if(word1[i-1] != word2[j-1]) {
                    int n = dp[i-1][j];
                    n = min(n, dp[i][j-1]);
                    n = min(n, dp[i-1][j-1]);
                    dp[i][j] = n + 1;
                }
                else {
                    int n = dp[i-1][j] + 1;
                    n = min(n, dp[i][j-1] + 1);
                    n = min(n, dp[i-1][j-1]);
                    dp[i][j] = n;
                }
            }
        }
        return dp.back().back();
    }
};
```

## 思路
Dynamic Programming，用一個dp矩陣存取距離，當前兩個字元一樣時，可以取左上角，不一樣時，左上角、上、左中取小的再加一格，注意邊界條件。

## 複雜度
時間複雜度O(nm)
空間複雜度O(nm)

## 解法二
```C++
class Solution { 
public:
    int minDistance(string word1, string word2) {
        int m = word1.length(), n = word2.length();
        vector<int> cur(m + 1, 0);
        for (int i = 1; i <= m; i++)
            cur[i] = i;
        for (int j = 1; j <= n; j++) {
            int pre = cur[0];
            cur[0] = j;
            for (int i = 1; i <= m; i++) {
                int temp = cur[i];
                if (word1[i - 1] == word2[j - 1])
                    cur[i] = pre;
                else cur[i] = min(pre + 1, min(cur[i] + 1, cur[i - 1] + 1));
                pre = temp;
            }
        }
        return cur[m]; 
    }
}; 

```
## 思路
注意每一個row，到下兩層之後就不會再用，因此空間複雜度可以依此優化。

## 複雜度
時間複雜度O(nm)
空間複雜度O(n)