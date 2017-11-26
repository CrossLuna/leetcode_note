#  253. Meeting Rooms II

[Description](https://leetcode.com/problems/meeting-rooms-ii/description/)

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
    int minMeetingRooms(vector<Interval>& intervals) {
        sort(intervals.begin(), intervals.end(), [](Interval& a, Interval& b) {
            return a.start < b.start;
        });
        priority_queue<int, vector<int>, greater<int>> heap;
        for(auto& intv: intervals) {
            if(!heap.empty() && heap.top() <= intv.start) {
                heap.pop();
            }   
            heap.push(intv.end);
        }
        return heap.size();
    }
};
```

## 思路
用一個mininum heap儲存結束時間，如果新活動的開始時間早於當前最小的結束時間，表示現有房間都不夠了，需要新開房間，此時將新房間的結束時間存入heap。

詳細證明參照CLRS Exercise 16.1-4

## 複雜度
O(nlogn)

## 解法二
```C++
```
## 思路

## 複雜度