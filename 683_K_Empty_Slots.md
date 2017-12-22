# 683. K Empty Slots

[Description](https://leetcode.com/problems/k-empty-slots/description/)

## 解法一
```C++
class Solution {
public:
    int kEmptySlots(vector<int>& flowers, int k) {
        set<int> pset;
        for(int i = 0; i<flowers.size(); ++i) {
            auto n = flowers[i];
            auto p = pset.insert(n).first;
            auto r = p;
            ++r;
            if(r != pset.end() && *r == n+k+1) return i+1;
            if(p != pset.begin() && *(--p) == n-k-1) return i+1;
        }
        return -1;
    }
};
```

## 思路
使用set (binary search tree)，直接搜尋上下元素

## 複雜度
O(nlogn)

## 解法二
```C++
class Solution {
public:
    int kEmptySlots(vector<int>& flowers, int k) {
        int num_b = (flowers.size() / (k+1))+1;
        vector<int> bucket_min (num_b, INT_MAX);
        vector<int> bucket_max (num_b, INT_MIN);
        for(int i=0; i<flowers.size(); ++i) {
            int n = flowers[i];
            int idx_b = n/(k+1);
            if(n < bucket_min[idx_b]) {
                bucket_min[idx_b] = n;
            }
            if(n > bucket_max[idx_b]) {
                bucket_max[idx_b] = n;
            }

            if(n == bucket_min[idx_b]) {
                if(idx_b > 0 && bucket_max[idx_b-1] == n-k-1) return i+1;
            }
            if(n == bucket_max[idx_b]) {
                if(idx_b < num_b-1 && bucket_min[idx_b+1] == n+k+1) return i+1;
            }
        }
        return -1;
    }
};
```
## 思路
利用bucket存最大與最小值，直接把最小值與前一桶或是最大值與後一桶比較(因為如果在中間就不用比了，一定不到k+1個空格)，再確認空格是否正確。

## 複雜度
時間複雜度O(nk)
空間複雜度O(n/(k+1))