# 537. Complex Number Multiplication 

[Description](https://leetcode.com/problems/complex-number-multiplication/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    pair<int, int> parse_comp(const string& s) {
        int n = s.find("+");
        int real = stoi(s.substr(0, n));
        int img = stoi(s.substr(n+1, s.size()));
        return make_pair(real, img);
    }
    string complexNumberMultiply(string a, string b) {
        auto p_a = parse_comp(a);
        auto p_b = parse_comp(b);
        int real = p_a.first * p_b.first - p_a.second * p_b.second;
        int img  = p_a.first * p_b.second + p_a.second * p_b.first;
        string ans = to_string(real) + "+" + to_string(img) + "i";
        return ans;
    }
};
```

## 思路
熟記 `basic_string::find` 以及 `basic_string::substr` 的用法