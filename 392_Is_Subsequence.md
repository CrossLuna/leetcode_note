# 392. Is Subsequence 

[Description](https://leetcode.com/problems/is-subsequence/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool isSubsequence(string s, string t) {
        vector<int> dp_curr (t.size()+1);
        vector<int> dp_next (t.size()+1);
        for(int i=1; i<=s.size(); ++i) {
            for(int j=1; j<=t.size(); ++j) {
                if(s[i-1] == t[j-1]) {
                    dp_next[j] = dp_curr[j-1] + 1;
                }
                else {
                    dp_next[j] = max(dp_next[j-1], dp_curr[i-1]);
                }
            }
            swap(dp_next, dp_curr);
        }
        return dp_curr.back() == s.size();
    }
};
```

## 思路
如果LCS長度等於s長度

## 複雜度
時間複雜度O(n*m)
空間複雜度O(m)

## 解法二
```C++
class Solution {
public:
    bool isSubsequence(string s, string t) {
        int idxs = 0;
        int idxt = 0;
        for(;idxt < t.size(); ++idxt) {
            if(s[idxs] == t[idxt])
                ++idxs;
        }
        return idxs == s.size();
    }
};
```
## 思路
逐個比對，每次字符相同 s 的 index 就往前一格，最後檢查是否全部遍歷。

## 複雜度
O(m or n)