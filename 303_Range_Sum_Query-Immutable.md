# 303. Range Sum Query - Immutable

[Description](https://leetcode.com/problems/range-sum-query-immutable/description/)

## 解法一
```C++
class NumArray {
public:
    NumArray(vector<int> nums): sums(nums.size()+1, 0) {
        for(int i=1; i<=nums.size(); ++i) {
            sums[i] = sums[i-1] + nums[i-1];
        }
    }
    
    int sumRange(int i, int j) {
        return sums[j+1] - sums[i];
    }

private:
    vector<int> sums;
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * int param_1 = obj.sumRange(i,j);
 */
```

## 思路
另外放一個向量存從第一個元素到當前的總和，注意index邊界

## 複雜度
sumRange時間 O(1)  
空間 O(n)
