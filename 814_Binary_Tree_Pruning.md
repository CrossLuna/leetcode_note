# 814. Binary Tree Pruning

[Description](https://leetcode.com/contest/weekly-contest-79/problems/binary-tree-pruning/)

## 解法一
```C++
class Solution {
public:
    bool iszero(TreeNode* root) {
        if(!root) return true;
        bool leftans = iszero(root->left);
        if(leftans) root->left = nullptr;
        bool rightans = iszero(root->right);
        if(rightans) root->right = nullptr;
        return leftans && rightans && root->val == 0;
    }
    TreeNode* pruneTree(TreeNode* root) {
        bool z = iszero(root);
        if(z) return nullptr;
        return root;
    }
};
```

## 思路
遞歸解，每次先檢查左右子節點需不需要刪除，若需要則刪除，最後再檢查自己本身

## 複雜度
O(n)，n是節點數量

## 解法二
```C++
```
## 思路

## 複雜度