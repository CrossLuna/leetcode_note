# 121. Best Time to Buy and Sell Stock 
 
[Description](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

## First Attemp
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int rev = 0;
        for(int i=0; i<prices.size(); ++i) {
            for(int j=i+1; j<prices.size(); ++j) {
                rev = max(rev, prices[j]-prices[i]);
            }
        }
        return rev;
    }
};
```

## 思路
Trivial

## 複雜度
O(n^2) LTE

## 解法一
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if(prices.size() == 0) return 0;
        int cur_low = prices[0];
        int max_rev = 0;
        for(int i=0; i<prices.size(); ++i) {
            max_rev = max(max_rev, prices[i]- cur_low);
            if(prices[i] < cur_low) cur_low = prices[i];
        }
        return max_rev;
    }
};
```
## 思路
儲存當前最低值，逐個比較

## 複雜度
O(n)

## 解法二
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int cur_max_sum = 0;
        int cur_sum = 0;
        for(int i=1; i<prices.size(); ++i) {
            cur_sum += prices[i] - prices[i-1];
            if(cur_sum < 0) cur_sum = 0;
            cur_max_sum = max(cur_max_sum, cur_sum);
        }
        return cur_max_sum;
    }
};
```
## 思路
Kadane's algorithm: 線性求取maximum subarray sum
取每個相鄰價格價差，求取maximum subarray sum，當累積為負，就歸零。


## 複雜度
O(n)