# 216. Combination Sum III 

[Description](https://leetcode.com/problems/combination-sum-iii/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    void recur(vector<vector<int>>& ans, vector<int>& cur , int num, int sum, int k, int n) {
        if(cur.size() == k && sum == n) {
            ans.push_back(cur);
            return;
        }
        if(sum > n || cur.size() >= k) return;
        for(int i = num ; i <= 9; ++i) {
            cur.push_back(i);
            sum += i;
            recur(ans, cur, i+1, sum, k, n);
            sum -= i;
            cur.pop_back();
        }
    }
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<vector<int>> ans;
        vector<int> cur;
        recur(ans, cur, 1, 0, k, n);
        return ans;
    }
};
```

## 思路
經典back trace，小心各種邊界條件

## 複雜度
O(C n 取 k)

## 解法二
```C++
class Solution {
public:
    void combination(vector<vector<int>>& result, vector<int> sol, int k, int n) {
        if (sol.size() == k && n == 0) { 
            result.push_back(sol); 
            return ;   
        }
        if (sol.size() < k) {
            for (int i = sol.empty() ? 1 : sol.back() + 1; i <= 9; ++i) {
                if (n - i < 0) break;
                sol.push_back(i);
                combination(result, sol, k, n - i);
                sol.pop_back();
            }
        }
    }

    vector<vector<int>> combinationSum3(int k, int n) {
        vector<vector<int>> result;
        vector<int> sol;
        combination(result, sol, k, n);
        return result;
    }
};
```
## 思路

## 複雜度