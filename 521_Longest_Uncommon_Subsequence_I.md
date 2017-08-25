# 521. Longest Uncommon Subsequence I 

[Description](https://leetcode.com/problems/longest-uncommon-subsequence-i/description/)

## First Attemp
```C++
class Solution {
public:
    int findLUSlength(string a, string b) {
        if(a == b) return -1;
        else return max(a.size(), b.size());
    }
};

```

## 思路
注意審題，要看出題目真義