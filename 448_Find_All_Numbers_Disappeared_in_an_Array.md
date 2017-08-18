# 448. Find All Numbers Disappeared in an Array 

[Description](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)

## First attemp = 解法一
``` C++
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        int N = nums.size();
        vector<int> mm(N+1);
        for(auto n: nums) {
            mm[n]++;
        }
        vector<int> ans;
        for(int i=1; i<mm.size(); ++i) {
            if(mm[i] == 0)
                ans.push_back(i);
        }
        return ans;
    }
};
```

## 思路
Hashmap

## 複雜度
空間複雜度達到O(n)
時間複雜度O(n)

## TODO
## 解法二 (參考)
``` C++
```

## 思路