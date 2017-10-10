# 91. Decode Ways 

[Description](https://leetcode.com/problems/decode-ways/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int numDecodings(string s) {
        if(s.empty()) return 0;
        int N = s.size();
        vector<int> dp(N+1, 0);
        dp[0] = 1;
        if(s[0] != '0')
            dp[1] = 1;
        for(int i=1; i<N; ++i) {
            int nc = stoi(s.substr(i-1, 2));
            if(10 <= nc && nc <= 26) {
                dp[i+1] += dp[i-1];
            }
            if(s[i] != '0') {
                dp[i+1] += dp[i];
            }
        }
        return dp.back();
    }
};
```

## 思路
動態規劃，如果連續二字符符合條件記得加上前面可能的組合，注意邊界條件

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度