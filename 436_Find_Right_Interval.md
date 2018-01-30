# 436. Find Right Interval

[Description](https://leetcode.com/problems/find-right-interval/description/)

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
    vector<int> findRightInterval(vector<Interval>& intervals) {
        vector<int> ans;
        map<int, int> mymap;
        for(int i=0; i<intervals.size(); ++i) {
            mymap[intervals[i].start] = i;
        }
        for(auto& interval: intervals) {
            auto it = mymap.lower_bound(interval.end);
            if(it != mymap.end()) {
                ans.push_back(it->second);
            }
            else {
                ans.push_back(-1);
            }
        }
        return ans;
    }
};
```

## 思路
mymap有提供lower_bound接口，重點是只需要關心interval的end

## 複雜度
O(nlogn)

## 解法二
```C++
```
## 思路

## 複雜度