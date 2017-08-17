# 561. Array Partition I

[Description](https://leetcode.com/problems/array-partition-i/description/)

## First attemp
``` C++
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        nums.sort();    // Compilation Error
        int ans = 0;
        for(int i = 0; i < nums.size(); i += 2) {
            ans += nums[i];
        }
        return sum;    // 'sum' not defined
    }
};
```
Result: compilation error

## 思路
貪心，每一組min都要'犧牲'一個較大的數，先排序之後按序犧牲
注意整數範圍大小是否夠用

## 解法一
``` C++
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int ans = 0;
        for(int i = 0; i < nums.size(); i += 2) {
            ans += nums[i];
        }
        return ans;
    }
};
```

## 複雜度
排序 O(nlogn)


## 檢討
1. 排序API要記熟
2. 變數名隨時檢查

## 解法二 (參考)
``` C++
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        vector<int> hashmap (20001,0);
        for(auto n: nums) {
            hashmap[n+10000] += 1;
        }
        int ans = 0;
        bool flag = true;
        for(int i=0; i<20001;) {
            if(hashmap[i] > 0 && flag) {
                ans += i-10000;
                flag = false;
                hashmap[i]--;
            }
            else if(hashmap[i] > 0) {
                hashmap[i]--;
                flag = true;
            }
            else {
                i++; // not proceed until the count is zero
            }
        }
        return ans;
    }
};
```

## 思路
hashmap，空間換時間，複雜度O(n)，
從數字小的開始檢查，如果該數字之前有被計數，則減一直到計數歸零才換下一個數字