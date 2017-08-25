# 482. License Key Formatting 

[Description](https://leetcode.com/problems/license-key-formatting/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    string licenseKeyFormatting(string S, int K) {
        int N = 0;
        for(auto ch: S) {
            if(ch != '-') ++N;
        }
        int first = N % K == 0 ? K: N % K;
        int i = 0;
        int num = 0;
        string ans;
        while(first-->0) {
            while(S[i] == '-') ++i;
            ans += toupper(S[i++]);
            ++num;
        }
        ans += '-';
        
        while(num < N) {
            int cnt = 0;
            while(cnt++ < K) {
                while(S[i] == '-') ++i;
                ans += toupper(S[i++]);
                ++num;
            }
            ans += '-';
        }
        ans.pop_back();
        
        return ans;
    }
};
```

## 思路
Implement，注意邊界條件

## 複雜度

## 解法二
```C++
string licenseKeyFormatting(string S, int K) {
    string res;
    for (auto i = S.rbegin(); i < S.rend(); i++)
        if (*i != '-') { 
            // ignore '-' in original string
            if (res.size()%(K+1) == K) res += '-'; // every (K+1)th char is '-' from tail
            res += toupper(*i);
        }
        
    reverse(res.begin(), res.end());
    return res;
}

```
## 思路

## 複雜度