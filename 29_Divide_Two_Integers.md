# 29. Divide Two Integers

[Description](https://leetcode.com/problems/divide-two-integers/description/)

## 解法一
```C++
class Solution {
public:
    int divide(int dividend, int divisor) {
        bool isneg = false;
        if(dividend < 0 && divisor > 0 || dividend > 0 && divisor < 0) {
            isneg = true;
        }
        unsigned long long dvd = abs(static_cast<long long>(dividend));
        unsigned long long dvs = abs(static_cast<long long>(divisor));
        unsigned base = 1;
        unsigned ans = 0;
        cout << dvd << endl;
        cout << dvs << endl;
        if(dvd < dvs) return 0;
        while(dvs <= dvd) {
            if(dvs << 1 > dvd) {
                break;
            }
            dvs <<= 1;
            base <<= 1;
        }

        cout << dvs << endl;

        while(dvd > 0) {
            while(dvd < dvs) {
                dvs >>= 1;
                base >>= 1;
            }
            dvd -= dvs;
            ans += base;
        }
        if(ans > INT_MAX && !isneg) return INT_MAX;
        int ret = static_cast<int>(ans);
        if(isneg) ret = -ret;
        return ret;
    }
};
```

## 思路
用移位代替乘法，從最高位開始
注意各種邊界條件

## 複雜度
O(log N)，N是dividend或是divisor的值

## 解法二
```C++
```
## 思路

## 複雜度