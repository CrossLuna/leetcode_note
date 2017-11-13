# 139. Word Break 

[Description](https://leetcode.com/problems/word-break/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        if(s.empty()) return true;
        if(wordDict.empty()) return false;
        unordered_set<string> dictset;
        for(auto& w: wordDict) {
            dictset.insert(w);
        }
        int N = s.size();
        vector<bool> dp(N+1, false);
        dp[0] = true;
        for(int i=1; i<=N; ++i) {
            for(int j=0; j<i; ++j) {
                if(dp[j]) {
                    auto str = s.substr(j, i-j);
                    if(dictset.find(str) != dictset.end()) {
                        dp[i] = true;
                        break;
                    }
                }
            }
        }
        return dp[N];
    }
};
```

## 思路
動態規劃，DP內存的是str[0,...,i]是否可拆，邊界條件很tricky

## 複雜度
時間複雜度O(N^2)
空間複雜度O(N)

## 解法二
```C++
```
## 思路

## 複雜度