# 266. Palindrome Permutation 

[Description](https://leetcode.com/problems/palindrome-permutation/description/)

## 解法一
```C++
class Solution {
public:
    bool canPermutePalindrome(string s) {
        vector<int> hashmap(256, 0);
        for(auto ch: s) {
            ++hashmap[ch];
        }
        bool one = false;
        for(auto n: hashmap) {
            if(n % 2 != 0) {
                if(!one) one = true;
                else return false;
            }
        }
        return true;
    }
};
```

## 思路
Hashmap

## 複雜度
時間複雜度O(n)
空間複雜度O(256)

## 解法二
```C++
```
## 思路

## 複雜度