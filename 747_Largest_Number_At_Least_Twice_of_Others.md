# 747. Largest Number At Least Twice of Others

[Description](https://leetcode.com/problems/largest-number-at-least-twice-of-others/description/)

## 解法一
```C++
class Solution {
public:
    int dominantIndex(vector<int>& nums) {
        if(nums.size() == 0) return -1;
        if(nums.size() == 1) return 0;
        int ans = 0;
        int first = nums[0];
        int second = nums[1];
        if(first < second) {
            ans = 1;
            swap(first, second);
        }
        
        for(int i=2; i<nums.size(); ++i) {
            if(nums[i] > first) {
                ans = i;
                second = first;
                first = nums[i];
            }
            else if(nums[i] > second) {
                second = nums[i];
            }
        }
        return first >= 2 * second ? ans: -1;
    }
};
```

## 思路
照題意做即可

## 複雜度
O(n), one pass