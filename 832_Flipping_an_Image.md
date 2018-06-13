# 832. Flipping an Image

[Description](https://leetcode.com/problems/flipping-an-image/description/)

## 解法一
```C++
class Solution {
public:
    vector<vector<int>> flipAndInvertImage(vector<vector<int>>& A) {
        for(auto& r: A) {
            int N = r.size();
            for(int i=0; i<N/2; ++i) {
                swap(r[i], r[N-i-1]);
            }
            for(auto& e: r) {
                if(e == 1) e = 0;
                else e = 1;
            }
        }
        return A;
    }
};
```

## 思路
直接實作

## 複雜度
O(width * height)

## 解法二
```C++
```
## 思路

## 複雜度