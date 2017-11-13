# 621. Task Scheduler 

[Description](https://leetcode.com/problems/task-scheduler/description/)

## 解法一
```C++
class Solution {
public:
    int leastInterval(vector<char>& tasks, int n) {
        vector<int> cnt (26, 0);
        for(auto ch: tasks) {
            ++cnt[ch-'A'];
        }
        sort(cnt.begin(), cnt.end());
        int i = 25;
        while(cnt[i] == cnt[25]) --i;
        int mx = cnt[25];
        int len = tasks.size();
        return max(len, (mx-1) * (n+1) + 25-i);
    }
};
```

## 思路
http://www.cnblogs.com/grandyang/p/7098764.html
非常神...

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度