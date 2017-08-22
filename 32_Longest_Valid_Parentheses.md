# 32. Longest Valid Parentheses 

[Description](https://leetcode.com/problems/longest-valid-parentheses/description/)

## 解法一
```C++
class Solution {
public:
    int longestValidParentheses(string s) {
        stack<int> st;
        size_t idx = 0;
        int max_len = 0;
        int cur_len = 0;
        for(int i=0; i<s.size(); ++i) {
            if(s[i] == '(') {
                st.push(i);
            }
            else if(s[i] == ')') {
                if(!st.empty() && s[st.top()] == '(') {
                    st.pop();
                    if(st.empty()) {
                        cur_len = i + 1;
                    }
                    else {
                        cur_len = i - st.top();
                    }
                    max_len = max(max_len, cur_len);
                }
                else {
                    st.push(i);
                }
            }
        }
        return max_len;
    }
};
```

## 思路
使用棧，如果遇到死的)，將之push入棧，如此可以當作目前已經有效的標兵
記得放一個-1在最底下，或是處理邊界條件

## 複雜度

## DP TODO
## 解法二
```C++
```
## 思路

## 複雜度