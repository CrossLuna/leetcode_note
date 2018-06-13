# 845. Longest Mountain in Array

[Description](https://leetcode.com/problems/longest-mountain-in-array/description/)

## 解法一
```C++
class Solution {
public:
    int longestMountain(vector<int>& A) {
        if(A.size() == 0) return 0;
        int max_len = 1;
        int cur_len = 1;
        bool is_up = false;
        bool is_down = false;
        int cur_val = A[0];
        int N = A.size();
        for(int i=1; i<N; ++i) {
            if(cur_val < A[i]) {
                if(is_up) ++cur_len;
                if(is_down) {
                    max_len = max(max_len, cur_len);
                }
                cur_len = 2;
                is_up = true;
            }
            else if (cur_val == A[i]) {
                is_up = false;
                is_down = false;
                max_len = max(max_len, cur_len);
                cur_len = 1;
            }
            else { // cur_val > A[i]
                if(is_up) {
                    is_down = true;
                    cur_len += 1;
                }
                else if(is_down) {
                    cur_len += 1;
                    max_len = max(max_len, cur_len);
                }
            }
            cur_val = A[i];
        }
        if (max_len < 3) return 0;
        return max_len;
    }
};
```

## 思路
各種邊界條件，思路複雜

## 複雜度
時間複雜度O(n)
空間複雜度O(1)

## 解法二
```C++
class Solution {
public:
    int longestMountain(vector<int>& A) {
        int ans = 0, up = 0, down = 0;
        for(int i=1 ;i<A.size(); ++i) {
            if((down > 0 && A[i-1] < A[i]) || A[i-1] == A[i]) {
                up = 0;
                down = 0;
            }
            if(A[i-1] < A[i]) ++up;
            if(A[i-1] > A[i]) ++down;
            if(up > 0 && down > 0) {
                ans = max(ans, up+down+1);
            }
        }
        return ans;
    }
};
```
## 思路
簡化，分成uphill跟downhill來處理
注意：如果同時需要數數量和表示狀態，可以合併
比如這邊的`is_up`和`is_down`可以改成`up`和`down`處理

## 複雜度
時間複雜度O(n)
空間複雜度O(1)