# 71. Simplify Path

[Description](https://leetcode.com/problems/simplify-path/description/)

## 解法一
```C++
class Solution {
public:
    string simplifyPath(string path) {
        if(path.size() == 0) return path;
        size_t start = 0;
        stack<string> st_dir;
        while(start < path.size()) {
            while(path[start] == '/' && start < path.size()) ++start;
            size_t end = path.find('/', start);
            if(start < end) {
                string dir = path.substr(start, end-start); 
                if(dir == "..") {
                    if(!st_dir.empty())
                        st_dir.pop();
                }
                else if(!dir.empty() && dir != ".") {
                    st_dir.push(dir);
                }
            }
            
            start = end;
        }
        string ans;
        stack<string> st_dir_rev;
        while(!st_dir.empty()) {
            st_dir_rev.push(st_dir.top());
            st_dir.pop();
        }
        while(!st_dir_rev.empty()) {
            ans += '/';
            ans += st_dir_rev.top();
            st_dir_rev.pop();
        }
        if(ans.size() == 0) ans += "/";
        return ans;
    }
};
```

## 思路
注意各種邊界條件，string的index應當是size_t，注意npos的用法，雖然給定-1的值但是轉成無符號整數就會變成最大值
注意find跟substr的用法

## 複雜度

## 解法二
```C++
string simplifyPath(string path) {
    string res, tmp;
    vector<string> stk;
    stringstream ss(path);
    while(getline(ss,tmp,'/')) {
        if (tmp == "" or tmp == ".") continue;
        if (tmp == ".." and !stk.empty()) stk.pop_back();
        else if (tmp != "..") stk.push_back(tmp);
    }
    for(auto str : stk) res += "/"+str;
    return res.empty() ? "/" : res;
}
```
## 思路
學習stringstream以及getline的用法

## 複雜度