# 495. Teemo Attacking 

[Description](https://leetcode.com/problems/teemo-attacking/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        if(timeSeries.size() == 0) return 0;
        sort(timeSeries.begin(), timeSeries.end());
        int ans = 0;
        int start = timeSeries[0];
        int end = start + duration;
        for(int i=1; i<timeSeries.size(); ++i) {
            if(timeSeries[i] <= end) {
                end = timeSeries[i] + duration;
            }
            else {
                ans += (end - start);
                start = timeSeries[i];
                end = start + duration;
            }
        }
        ans += (end - start);
        return ans;
    }
};
```

## 思路

## 複雜度

## 解法二
```C++
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int ans = duration * timeSeries.size();
        for(int i=1; i<timeSeries.size(); ++i) {
            ans -= max(0, duration- (timeSeries[i]-timeSeries[i-1]));
        }
        return ans;
    }
};
```
## 思路

## 複雜度