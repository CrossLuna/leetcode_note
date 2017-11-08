# 67. Add Binary

[Description](https://leetcode.com/problems/add-binary/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    string addBinary(string a, string b) {
        if(a.size() < b.size()) swap(a, b);
        // a is always longer
        reverse(a.begin(), a.end());
        reverse(b.begin(), b.end());
        int carry = 0;
        int sum = 0;
        for(int i = 0; i<a.size(); ++i) {
            sum = carry;
            sum += a[i] - '0';
            if(i < b.size())
                sum += b[i] - '0';
            carry = sum / 2;
            sum = sum % 2;
            a[i] = sum + '0';
        }
        if(carry != 0) a += static_cast<char>(carry + '0');
        reverse(a.begin(), a.end());
        return a;
    }
};
```

## 思路
先反過來

## 複雜度
O(n)

## 解法二
```C++
class Solution
{
public:
    string addBinary(string a, string b)
    {
        string s = "";
        
        int c = 0, i = a.size() - 1, j = b.size() - 1;
        while(i >= 0 || j >= 0 || c == 1)
        {
            c += i >= 0 ? a[i --] - '0' : 0;
            c += j >= 0 ? b[j --] - '0' : 0;
            s = char(c % 2 + '0') + s;
            c /= 2;
        }
        
        return s;
    }
};
```
## 思路

## 複雜度