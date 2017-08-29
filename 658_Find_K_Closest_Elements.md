# 658. Find K Closest Elements 

[Description](https://leetcode.com/problems/find-k-closest-elements/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    struct Comp {
        bool operator() (int a, int b) {
            if(abs(a) == abs(b)) return a > b;
            return abs(a) > abs(b);
        }
    };
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        priority_queue<int, vector<int>, Comp> pq;
        for(auto n: arr) {
            pq.push(n-x);
        }
        vector<int> ans;
        while(k-->0) {
            ans.push_back(pq.top() + x);
            pq.pop();
        }
        sort(ans.begin(), ans.end());
        return ans;
    }
};
```

## 思路
優先級隊列

## 複雜度
O(nlogn)

## 解法二
```C++
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        int idx = lower_bound(arr.begin(), arr.end(), x) - arr.begin();
        int left = idx-1;
        int right = idx;
        while(k-->0) {
            // range: (left, right)
            if(left < 0) {
                ++right;
            }
            else if(right >= arr.size()) {
                --left;
            }
            else {
                if(abs(arr[left]-x)>abs(arr[right]-x))
                    ++right;
                else 
                    --left;
            }
        }
        return vector<int> (arr.begin() + left + 1, arr.begin() + right);
    }
};
```
## 思路
二分搜尋+雙指針，注意lower_bound的用法
lower_bound: 第一個不小於元素的位置
upper_bound: 第一個大於該元素的位置
`upper_bound - lower_bound`就是該元素的個數

## 複雜度
O(logn + K)