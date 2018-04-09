# 813. Largest Sum of Averages

[Description](https://leetcode.com/problems/largest-sum-of-averages/description/)

## 解法一
```C++
class Solution {
public:
    double search(vector<int>& A, vector<vector<double>>& dp, int n, int k) {
        if(dp[n][k] > 0) return dp[n][k];
        // Two cases:
        // (1) Form a new group dp[n-1][k]...dp[1][k]
        // (2) dp[n-1][k]
        double sum = 0;
        for(int i=n-1; i>0; --i) {
            sum += A[i];
            int num = n-i;
            dp[n][k] = max(dp[n][k], search(A, dp, i, k-1) + sum/num);
        }
        return dp[n][k];
    }
    double largestSumOfAverages(vector<int>& A, int K) {
        int N = A.size();
        // dp[N][K] : max avg of first N numbers divided in K groups
        vector<vector<double>> dp(N+1, vector<double>(K+1, 0));
        // Initialization
        double sum = 0;
        for(int i=0; i<N; ++i) {
            int n = i+1;
            sum += A[i];
            dp[n][1] = sum/(n);
        }
        return search(A, dp, N, K);
    }
};
```

## 思路
動態規劃+Memoization，注意每次只照顧最後一組數字

## 複雜度
O(N*K)

## 解法二
```C++
```
## 思路

## 複雜度