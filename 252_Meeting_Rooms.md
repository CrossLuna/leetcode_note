# 252. Meeting Rooms 

[Description](https://leetcode.com/problems/meeting-rooms/description/)

## 解法一
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
    bool canAttendMeetings(vector<Interval>& intervals) {
        sort(intervals.begin(), intervals.end(), [](Interval& a, Interval& b){
            return a.start < b.start;
        });
        for(int i=1; i<intervals.size(); ++i) {
            if(intervals[i-1].end > intervals[i].start)
                return false;
        }
        return true;
    }
};
```

## 思路
排序，查重疊

## 複雜度
O(nlogn)

## 解法二
```C++
```
## 思路

## 複雜度