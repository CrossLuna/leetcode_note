# 836. Rectangle Overlap

[Description](https://leetcode.com/problems/rectangle-overlap/description/)

## 解法一
```C++
class Solution {
public:
    bool isRectangleOverlap(vector<int>& rec1, vector<int>& rec2) {
        bool x_overlap = not ((rec1[2] <= rec2[0]) || (rec2[2] <= rec1[0]));
        bool y_overlap = not ((rec1[3] <= rec2[1]) || (rec2[3] <= rec1[1]));
        return x_overlap and y_overlap;
    }
};
```

## 思路
有overlap必定兩軸都有overlap，邊界條件考慮上找非overlap的情況比較簡單

## 複雜度
O(1)

## 解法二
```C++
```
## 思路

## 複雜度