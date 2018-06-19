# 66. Plus One

[Description](https://leetcode.com/problems/plus-one/description/)

## 解法一
```C++
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int sum = 0;
        int car = 1;
        for(int i=digits.size()-1; i>=0; --i) {
            sum = car + digits[i];
            car = sum / 10;
            digits[i] = sum % 10;
        }
        if(car > 0) {
            digits.insert(digits.begin(), car);
        }
        return digits;
    }
};
```

## 思路
注意進位

## 複雜度
O(n)，最後一次進位可能成本高達O(n)