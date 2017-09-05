# 653. Two Sum IV - Input is a BST 

[Description](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/)

## 解法一
```C++
class Solution {
public:
    void traverse(TreeNode* root, vector<int>& arr) {
        if(!root) return;
        traverse(root->left, arr);
        arr.push_back(root->val);
        traverse(root->right, arr);
    }
    bool findTarget(TreeNode* root, int k) {
        if(!root) return false;
        vector<int> arr;
        traverse(root, arr);
        for(int i=0; i<arr.size()-1; ++i) {
            if(binary_search(arr.begin()+i+1, arr.end(), k-arr[i])) 
                return true;
        }
        return false;
    }
};
```

## 思路
中序遍歷後有序，使用二分搜索

## 複雜度
時間複雜度O(nlogn)，空間複雜度O(n)

## 解法二
```C++
class Solution {
public:
    void traverse(TreeNode* root, unordered_multiset<int>& ms) {
        if(!root) return;
        traverse(root->left, ms);
        ms.insert(root->val);
        traverse(root->right, ms);
    }
    bool findTarget(TreeNode* root, int k) {
        if(!root) return false;
        unordered_multiset<int> ms;
        traverse(root, ms);
        for(auto it = ms.begin(); it != ms.end(); ++it) {
            auto jt = ms.find(k-*it);
            if(jt != ms.end() && it != jt) return true;
        }
        return false;
    }
};
```
## 思路
使用hashmap降低時間複雜度

## 複雜度
O(n)
