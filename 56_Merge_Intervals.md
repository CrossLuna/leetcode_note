# 56. Merge Intervals 

[Description](https://leetcode.com/problems/merge-intervals/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    vector<Interval> merge(vector<Interval>& intervals) {
        vector<pair<int, int>> points;
        for(auto& itv: intervals) {
            // 1: start , 2: end
            points.push_back(make_pair(itv.start, 1));
            points.push_back(make_pair(itv.end, 2));
        }
        sort(points.begin(), points.end());
        int level = 0;
        int start = 0;
        int end = 0;
        vector<Interval> ans;
        for(int i=0; i<points.size(); ++i) {
            if(points[i].second == 1) {
                if(level == 0)
                    start = points[i].first;
                ++level;
            }
            else if(points[i].second == 2) {
                --level;
                if(level == 0) {
                    end = points[i].first;
                    ans.push_back(Interval(start, end));
                }
            }
        }
        return ans;
    }
};
```

## 思路
O(nlogn)，排序，利用計數器判定區間

## 複雜度

## 解法二
```C++
class Solution {
public:
    vector<Interval> merge(vector<Interval>& intervals) {
        sort(intervals.begin(), intervals.end(), [](Interval& a, Interval& b){
            return a.start < b.start;
        });
        vector<Interval> ans;
        if(intervals.empty()) return ans;
        ans.push_back(intervals[0]);
        for(int i=1; i<intervals.size(); ++i) {
            if(ans.back().end >= intervals[i].start){
                ans.back().end = max(ans.back().end, intervals[i].end);
            } 
            else {
                ans.push_back(intervals[i]);
            }
        }
        return ans;
    }
};
```
## 思路
思路雷同，但是更精簡

## 複雜度