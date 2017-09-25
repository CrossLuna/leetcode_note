# 593. Valid Square 

[Description](https://leetcode.com/problems/valid-square/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool is_perpen_and_equal (vector<int>& p1, vector<int>& p2, vector<int>& p3) {
        vector<int> v1 {p2[0]-p1[0], p2[1]-p1[1]};
        vector<int> v2 {p3[0]-p1[0], p3[1]-p1[1]};
        int dist1 = v1[0]*v1[0]+v1[1]*v1[1];
        int dist2 = v2[0]*v2[0]+v2[1]*v2[1];
        return v1[0]*v2[0]+v1[1]*v2[1] == 0 && dist1 != 0 && dist2 != 0 && dist1 == dist2;
    }
    bool validSquare(vector<int>& p1, vector<int>& p2, vector<int>& p3, vector<int>& p4) {
        return 
        is_perpen_and_equal(p1, p2, p3) && is_perpen_and_equal(p4, p2, p3) ||
        is_perpen_and_equal(p1, p3, p4) && is_perpen_and_equal(p2, p3, p4) ||
        is_perpen_and_equal(p1, p2, p4) && is_perpen_and_equal(p3, p2, p4);
    }
};
```
## 思路
內積，距離

## 複雜度

## 解法二
```C++
int d(vector<int>& p1, vector<int>& p2) {
    return (p1[0] - p2[0]) * (p1[0] - p2[0]) + (p1[1] - p2[1]) * (p1[1] - p2[1]);
}
bool validSquare(vector<int>& p1, vector<int>& p2, vector<int>& p3, vector<int>& p4) {
    unordered_set<int> s({ d(p1, p2), d(p1, p3), d(p1, p4), d(p2, p3), d(p2, p4), d(p3, p4) });
    return s.count(0) == 0 && s.size() == 2;
}
```
## 思路

## 複雜度