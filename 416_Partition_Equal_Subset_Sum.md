# 416. Partition Equal Subset Sum

[Description](https://leetcode.com/problems/partition-equal-subset-sum/description/)

## 解法一
```C++
class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int N = nums.size();
        int sum = 0;
        for(auto n: nums) {
            sum += n;
        }
        if(sum % 2 != 0) return false;
        int target = sum/2;
        vector<vector<bool>> dp (N, vector<bool>(target+1, false));
        for(int i=0; i<N; ++i) {
            dp[i][0] = true;
        }
        dp[0][nums[0]] = true;
        for(int i=1; i<N; ++i) {
            for(int j=1; j<=target; ++j) {
                int num = nums[i];
                //dp[i][j] = dp[i][j] || dp[i-1][j];
                if(dp[i-1][j]) dp[i][j] = true;
                if(j-num > 0 && dp[i-1][j-num]) dp[i][j] = true;
            }
        }
        return dp.back().back();
    }
};
```

## 思路
Dynamic Programming  
DP[i][j] 表示前i個數字的subset是否能組成j  
DP[i][0] 衡真，因為空集和一定可以組成0  
DP[0][j] 只有 j == nums[i] 可以組成
DP[i][j] 有兩種情況，DP[i-1][j]，表示用前面i-1個就可以組成了，再多加一個當然也可以，DP[i-1][j-nums[i]]表示，現在這一個正好補上缺口

## 複雜度
O(target * n)

## 解法二
```C++
```
## 思路

## 複雜度