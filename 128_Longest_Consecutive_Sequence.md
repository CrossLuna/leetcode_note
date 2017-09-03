# 128. Longest Consecutive Sequence 

[Description](https://leetcode.com/problems/longest-consecutive-sequence/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        unordered_set<int> s;
        for(auto n: nums) s.insert(n);
        int ans = 0;
        while(!s.empty()) {
            int cnt = 1;
            int n = *s.begin();
            int dist = 1;
            while(s.find(n+dist) != s.end()) {
                s.erase(n+dist);
                ++dist;
                ++cnt;
            }
            dist = -1;
            while(s.find(n+dist) != s.end()) {
                s.erase(n+dist);
                --dist;
                ++cnt;
            }
            ans = max(ans, cnt);
            s.erase(n);
        }
        return ans;
    }
};
```

## 思路
hashmap，每個數字往上下找，記得erase

## 複雜度
O(n)

## 解法二
```C++
class Solution {
public:
    int longestConsecutive(vector<int> &num) {
        unordered_set<int> record(num.begin(),num.end());
        int res = 1;
        for(int n : num){
            if(record.find(n)==record.end()) continue;
            record.erase(n);
            int prev = n-1,next = n+1;
            while(record.find(prev)!=record.end()) record.erase(prev--);
            while(record.find(next)!=record.end()) record.erase(next++);
            res = max(res,next-prev-1);
        }
        return res;
    }
};
```
## 思路
代碼簡潔

## 複雜度