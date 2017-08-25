# 357. Count Numbers with Unique Digits 

[Description](https://leetcode.com/problems/count-numbers-with-unique-digits/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int countNumbersWithUniqueDigits(int n) {
        vector<long long> arr(11, 0);
        arr[0] = 1;
        arr[1] = 9;
        for(int i=2; i<11; ++i) {
            arr[i] = arr[i-1] * (11 - i);
        }
        long long ans = 0;
        for(int i=0; i<=n && i<arr.size(); ++i) ans += arr[i];
        return ans;
    }
};
```

## 思路
簡易排列組合，注意邊界

## 複雜度
O(n), up to 11