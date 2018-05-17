# 338. Counting Bits

[Description](https://leetcode.com/problems/counting-bits/description/)

## 解法一
```C++
class Solution {
public:
    vector<int> countBits(int num) {
        vector<int> ans = {0};
        if(num == 0) return ans;
        ans.push_back(1);
        if(num == 1) return ans;
        int base = 1;
        for(int i=2; i<=num; ++i) {
            if(i >= (base << 1)) {
                base <<= 1;
            }
            ans.push_back(ans[i-base]+1);
        }
        return ans;
    }
};
```

## 思路
注意有重複的pattern，用一個`base`變數來紀錄要往前看到第幾個(1001->001, `base`=8)，找到對應的數字後加一，注意更新`base`的邊界條件(每隔1, 2, 4, 8...次循環)

## 複雜度
時間複雜度O(n)
空間複雜度O(n)

## 解法二
```C++
```
## 思路

## 複雜度