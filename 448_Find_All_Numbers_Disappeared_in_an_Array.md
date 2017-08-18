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
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        vector<int> ans;
        for(int i=0; i<nums.size(); ++i) {
            int idx = abs(nums[i]) - 1;
            if(nums[idx] > 0) nums[idx] *= -1;
        }

        for(int i=0; i<nums.size(); ++i) {
            if(nums[i] > 0) ans.push_back(i + 1);
        }
        return ans;
    }
};
```

## 思路
將出現過的置為負號
當明顯時間複雜度為O(n)的題要求使用O(1)的複雜度時，基本上就是用相加、相乘、XOR等處理
若無法處理，將信息存入原輸入陣列也是一法