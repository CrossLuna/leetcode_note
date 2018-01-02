# 296. Best Meeting Point

[Description](https://leetcode.com/problems/best-meeting-point/description/)

## 解法一
```C++
class Solution {
public:
    int minTotalDistance(vector<vector<int>>& grid) {
        int ans = 0;
        if(grid.empty() || grid[0].empty()) return ans;
        vector<pair<int, int>> points;
        for(int i=0; i<grid.size(); ++i) {
            for(int j=0; j<grid[0].size(); ++j) {
                if(grid[i][j] == 1) {
                    points.push_back(make_pair(i, j));
                }
            }
        }
        sort(points.begin(), points.end(), [](pair<int, int>& a, pair<int, int>& b){
            return a.first < b.first;
        });
        int N = points.size();
        for(int i=0; i<N/2; ++i) {
            ans += points[N-i-1].first - points[i].first;
        }
        sort(points.begin(), points.end(), [](pair<int, int>& a, pair<int, int>& b){
            return a.second < b.second;
        });
        for(int i=0; i<N/2; ++i) {
            ans += points[N-i-1].second - points[i].second;
        }
        return ans;
    }
};
```

## 思路
首先遇到 Manhattan Distance 一定先想到每個方向分開處理。
思考一維，排序後從外側開始每次加上兩個端點的距離(0, n-1), (1, n-2) ,....

## 複雜度
O(m*n + klogk)  
k = number of '1'

## 解法二
```C++
```
## 思路

## 複雜度