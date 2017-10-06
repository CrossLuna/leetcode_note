# 150. Evaluate Reverse Polish Notation 

[Description](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool is_operator(string& s) {
        return s == "+" || s == "-" || s == "*" || s == "/";
    }
    int evalRPN(vector<string>& tokens) {
        vector<int> nums;
        for(auto & t: tokens) {
            if(is_operator(t)) {
                int a = nums[nums.size()-2];
                int b = nums[nums.size()-1];
                nums.pop_back();
                nums.pop_back();
                if(t == "+") {
                    nums.push_back(a+b);
                }
                else if(t == "-") {
                    nums.push_back(a-b);
                }
                else if(t == "*") {
                    nums.push_back(a*b);
                }
                else if(t == "/") {
                    nums.push_back(a/b);
                }
            }
            else {
                nums.push_back(stoi(t));
            }
        }
        return nums.back();
    }
};
```

## 思路
逆波蘭表達式，標準使用stack解決

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度