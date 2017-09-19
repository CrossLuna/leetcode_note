# 22. Generate Parentheses 

[Description](https://leetcode.com/problems/generate-parentheses/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> ans;
        string curr = "";
        dfs(curr, 0, n, ans);
        return ans;
    }
    void dfs(string& curr, int num_left_in_stack, int num_to_push, vector<string>& ans) {
        if(num_left_in_stack == 0 && num_to_push == 0) {
            ans.push_back(curr);
            return;
        }
        if(num_to_push == 0) {
            curr += ')';
            dfs(curr, num_left_in_stack-1, 0, ans);
            curr.pop_back();
        }
        else if(num_left_in_stack == 0) {
            curr += '(';
            dfs(curr, 1, num_to_push-1, ans);
            curr.pop_back();
        }
        else {
            curr += ')';
            dfs(curr, num_left_in_stack-1, num_to_push, ans);
            curr.pop_back();
            curr += '(';
            dfs(curr, num_left_in_stack+1, num_to_push-1, ans);
            curr.pop_back();
        }
    }
};
```

## 思路

## 複雜度
Catalan(n)

## 解法二
```C++
```
## 思路

## 複雜度