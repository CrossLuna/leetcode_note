# 274. H-Index

[Description](https://leetcode.com/problems/h-index/description/)

## 解法一
```C++
class Solution {
public:
    int hIndex(vector<int>& citations) {
        if(citations.empty()) return 0;
        sort(citations.begin(), citations.end());
        int N = citations.size();
        for(int i=0; i<N; ++i) {
            if(citations[i] >= N-i) return N-i;
        }
        return 0;
    }
};
```
## 思路

## 複雜度
O(nlogn)

## 解法二
```C++
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int N = citations.size();
        vector<int> count(N+1);
        for(int c: citations)
            if(c>N)
                ++count[N];
            else
                ++count[c];
        
        int total = 0;
        for(int i=N; i>=0; --i) {
            total += count[i];
            if(total >= i)
                return i;
        }
        return 0;
    }
};
```
## 思路
動態規劃
## 複雜度
O(n)