# 435. Non-overlapping Intervals 

[Description](https://leetcode.com/problems/non-overlapping-intervals/description/)

## First Attemp = 解法一
```C++
/**
 * Definition for an interval.
 * struct Interval {
 *     int start;
 *     int end;
 *     Interval() : start(0), end(0) {}
 *     Interval(int s, int e) : start(s), end(e) {}
 * };
 */
class Solution {
public:
    int eraseOverlapIntervals(vector<Interval>& intervals) {
        if(intervals.empty()) return 0;
        sort(intervals.begin(), intervals.end(), [](Interval& a, Interval& b){
            if(a.end < b.end) return true;
            if(a.end > b.end) return false;
            return a.start > b.start;
        });

        int end = intervals[0].end;
        int cnt = 1;
        for(int i=1; i<intervals.size(); ++i) {
            if(end <= intervals[i].start) {
                end = intervals[i].end;
                ++cnt;
            }
        }
        return intervals.size() - cnt;
    }
};
```

## 思路
貪心算法，按結束時間排序，可以參考Algorithm Design Manual Chap.1.2 Page 9

## 複雜度
O(nlogn)

## 解法二
```C++
```
## 思路

## 複雜度