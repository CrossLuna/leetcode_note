# 539. Minimum Time Difference 

[Description](https://leetcode.com/problems/minimum-time-difference/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int to_min(const string & time) {
        int min = 0;
        int i = time.find(':');
        min += 60 * stoi(time.substr(0, i));
        min += stoi(time.substr(i+1));
        return min;
    }
    int findMinDifference(vector<string>& timePoints) {
        sort(timePoints.begin(), timePoints.end(), [&](string& a, string &b){
            return to_min(a) < to_min(b);
        });
        int min_diff = 1440;
        for(int i=0; i<timePoints.size()-1; ++i) {
            int diff = to_min(timePoints[i+1]) - to_min(timePoints[i]);
            min_diff = min(min_diff, diff);
        }
        min_diff = min(min_diff, 1440-to_min(timePoints.back())+to_min(timePoints[0]));
        return min_diff;
    }
};
```

## 思路
把時間字符轉換成分鐘數後再排序，記得前後排序

## 複雜度
O(nlogn)

## 解法二
```C++
class Solution {
public:
    int findMinDifference(vector<string>& times) {
        int n = times.size();
        sort(times.begin(), times.end());
        int mindiff = INT_MAX;
        for (int i = 0; i < times.size(); i++) {
            int diff = abs(timeDiff(times[(i - 1 + n) % n], times[i]));
            diff = min(diff, 1440 - diff);
            mindiff = min(mindiff, diff);
        }
        return mindiff;
    }

private:
    int timeDiff(string t1, string t2) {
        int h1 = stoi(t1.substr(0, 2));
        int m1 = stoi(t1.substr(3, 2));
        int h2 = stoi(t2.substr(0, 2));
        int m2 = stoi(t2.substr(3, 2));
        return (h2 - h1) * 60 + (m2 - m1);
    }
};
```
## 思路
簡潔代碼
## 複雜度