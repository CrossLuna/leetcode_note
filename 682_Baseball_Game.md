# 682. Baseball Game

[Description](https://leetcode.com/contest/leetcode-weekly-contest-51/problems/baseball-game/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int calPoints(vector<string>& ops) {
        vector<int> scores;
        for(auto & op: ops) {
            if(op == "C") {
                scores.pop_back();
            }
            else if(op == "D") {
                scores.push_back(scores.back() * 2);
            }
            else if(op == "+") {
                int N = scores.size();
                scores.push_back(scores[N-1] + scores[N-2]);
            }
            else {
                scores.push_back(stoi(op));
            }
        }
        return accumulate(scores.begin(), scores.end(), 0);
    }
};
```

## 思路
Implementation, O(n)

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度