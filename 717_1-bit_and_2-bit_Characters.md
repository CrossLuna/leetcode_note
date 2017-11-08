# 717. 1-bit and 2-bit Characters 

[Description](https://leetcode.com/problems/1-bit-and-2-bit-characters/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool isOneBitCharacter(vector<int>& bits) {
        int i = 0;
        int N = bits.size();
        while(i < N-1) {
            if(bits[i] == 1) i += 2;
            else  ++i;
        }
        if(i == N-1 && bits[i] == 0) return true;
        return false;
    }
};
```

## 思路
O(n)
## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度