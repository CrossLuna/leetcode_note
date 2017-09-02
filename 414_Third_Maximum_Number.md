# 414. Third Maximum Number 

[Description](https://leetcode.com/problems/third-maximum-number/discuss/)

## 解法一
```C++
class Solution {
public:
    int thirdMax(vector<int>& nums) {
        int N = nums.size();
        vector<int> arr;
        for(int i=0; i<N; ++i) {
            if(arr.empty()) arr.push_back(nums[i]);
            else {
                auto it = arr.begin();
                for(; it != arr.end(); ++it) {
                    if(nums[i] > (*it)) {
                        arr.insert(it, nums[i]);
                        if(arr.size() > 3) arr.pop_back();
                        break;
                    }
                    else if(nums[i] == (*it)) {
                        break;
                    }
                }
                if(it == arr.end() && arr.size() < 3) {
                    arr.push_back(nums[i]);
                }
            }
        }
        if(arr.size() < 3) return arr[0];
        else return arr[2];
    }
};
```

## 思路

## 複雜度

## 解法二
```C++
int thirdMax(vector<int>& nums) {
    set<int> top3;
    for (int num : nums) {
        top3.insert(num);
        if (top3.size() > 3)
            top3.erase(top3.begin());
    }
    return top3.size() == 3 ? *top3.begin() : *top3.rbegin();
}
```
## 思路

## 複雜度