# 405. Convert a Number to Hexadecimal 

[Description](https://leetcode.com/problems/convert-a-number-to-hexadecimal/description/)

## 解法一
```C++
class Solution {
public:
    string toHex(int num) {
        if(num == 0) return "0";
        long long n = num;

        vector<char> mm {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a', 'b', 'c', 'd', 'e', 'f'};
        
        bool is_neg = false;
        if(num < 0) {
            is_neg = true;
            n = -num - 1;
        }

        stack<char> s;
        while(n > 0) {
            if(is_neg) {
                s.push(mm[15 - n % 16]);
            }
            else {
                s.push(mm[n % 16]);
            }
            n >>= 4;
        }

        while(is_neg && s.size() != 8) {
            s.push('f');
        }

        string ans;
        while(!s.empty()) {
            ans += s.top();
            s.pop();
        }
        return ans;

    }
};
```

## 思路
基本進制轉換

## 複雜度
O(log n)

## 檢討
1. 注意各種邊界條件
2. 二的補數規則 (負數轉正 = -n-1)

## 解法二
```C++
const string HEX = "0123456789abcdef";
class Solution {
public:
    string toHex(int num) {
        if (num == 0) return "0";
        string result;
        int count = 0;
        while (num && count++ < 8) {
            result = HEX[(num & 0xf)] + result;
            num >>= 4;
        }
        return result;
    }
};

```
## 思路
轉2、8、16進制不需要負數轉換，僅須直接對應轉換bit即可