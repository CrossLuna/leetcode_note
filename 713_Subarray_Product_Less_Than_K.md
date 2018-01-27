# 713.Subarray Product Less Than K

[Description](https://leetcode.com/problems/subarray-product-less-than-k/description/)

## 解法一
```C++
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int>& nums, int k) {
        long long product = 1;
        int j = 0;
        long long result = 0;
        for(int i=0; i<nums.size(); ++i) {
            if(j < i) {
                product = 1;
                j = i;
            }
            while(product * nums[j] < k && j < nums.size()) {
                product *= nums[j++];
            }
            
            result += j - i;
            product /= nums[i];
        }
        return result;
    }
};

```

## 思路
雙指針

## 複雜度
O(N)

## 解法二
```C++
```
## 思路

## 複雜度