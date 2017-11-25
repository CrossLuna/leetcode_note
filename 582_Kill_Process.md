# 582. Kill Process 

[Description](https://leetcode.com/problems/kill-process/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    vector<int> killProcess(vector<int>& pid, vector<int>& ppid, int kill) {
        unordered_map<int, vector<int>> tree_map;
        int root = 0;
        for(int i=0; i<pid.size(); ++i) {
            if(ppid[i] == 0) {
                root = pid[i];
            }
            tree_map[ppid[i]].push_back(pid[i]);
        }
        vector<int> ans;
        queue<int> q;
        q.push(kill);
        while(!q.empty()) {
            auto n = q.front();
            for(auto ch: tree_map[n]) {
                q.push(ch);
            }
            ans.push_back(n);
            q.pop();
        }
        return ans;
    }
};
```

## 思路
Hashmap(key: 節點, value: children) + BFS(樹的層次遍歷)
也可以用DFS

## 複雜度
時間複雜度O(n)
空間複雜度O(n)

## 解法二
```C++
```
## 思路

## 複雜度