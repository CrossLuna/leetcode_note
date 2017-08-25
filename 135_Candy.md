# 135. Candy 

[Description](https://leetcode.com/problems/candy/description/)

## 解法一
```C++
class Solution {
public:
    int candy(vector<int>& ratings) {
        int N = ratings.size();
        vector<int> from_left(N, 1);
        for(int i=1; i<N; ++i) {
            if(ratings[i-1] < ratings[i]) {
                from_left[i] = from_left[i-1] + 1;
            }else {
                from_left[i] = 1;
            }
        }

        vector<int> from_right(N, 1);
        for(int i=N-2; i>=0; --i) {
            if(ratings[i] > ratings[i+1]) {
                from_right[i] = from_right[i+1] + 1;
            }
            else {
                from_right[i] = 1;
            }
        }
        int ans = 0;
        for(int i=0; i<N; ++i) {
            ans += max(from_left[i], from_right[i]);
        }
        return ans;
    }
};
```

## 思路
若上升就+1，其他就回到基本面，兩邊各掃一次，額外空間可以只用一個

## 複雜度
O(n)

## 解法二
```C++
```
## 思路

## 複雜度