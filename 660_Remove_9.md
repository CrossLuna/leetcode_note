# 660. Remove 9

[Description](https://leetcode.com/problems/remove-9/description/)

## 解法一
```C++
class Solution {
public:
    int newInteger(int n) {
        string ans;
        while(n > 0) {
            int r = n%9;
            ans += static_cast<char>(r + '0');
            n = n/9;
        }
        reverse(ans.begin(), ans.end());
        return stoi(ans);
    }
};
```

## 思路
遇到9跳過，相當於9進位的操作，因此把n轉成9進制即可
注意進制轉換的套路

## 複雜度
O(log n)


## 解法二
```C++
class Solution {
public:
    int newInteger(int n) {
        int ans = 0;
        int base = 1;
        while(n>0) {
            ans += n%9 * base;
            n /= 9;
            base *= 10;
        }
        return ans;
    }
};
```
## 思路

## 複雜度