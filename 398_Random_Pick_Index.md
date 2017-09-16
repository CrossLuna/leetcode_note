# 398. Random Pick Index 

[Description](https://leetcode.com/problems/random-pick-index/description/)

## First Attemp
```C++
class Solution {
public:
    Solution(vector<int> nums) {
        for(int i=0; i<nums.size(); ++i) {
            m[nums[i]].push_back(i);
        }
    }
    
    int pick(int target) {
        int N = m[target].size();
        return m[target][rand()%N];
    }
private:
    unordered_map<int, vector<int>> m;
};

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int param_1 = obj.pick(target);
 */
```
MLE

## 思路

## 複雜度

## 解法二
```C++
class Solution {
public:
    Solution(vector<int> nums) {
        arr = nums;
    }
    
    int pick(int target) {
        int N = 1;
        int ans = 0;
        for(int i=0; i<arr.size(); ++i) {
            if(arr[i] == target) {
                if(rand() % N == 0) ans = i;
                ++N;
            }
        }
        return ans;
    }
private:
    vector<int> arr;
};
```
## 思路
Resevoir Sampling

## 複雜度
時間複雜度 O(n)
空間複雜度 O(1)
