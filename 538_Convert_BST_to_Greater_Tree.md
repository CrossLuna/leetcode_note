# 538. Convert BST to Greater Tree 

[Description](https://leetcode.com/problems/convert-bst-to-greater-tree/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    TreeNode* convertBST(TreeNode* root) {
        vector<int> arr;
        traverse(root, arr);
        update(root, arr);
        return root;
    }
    void traverse(TreeNode* root, vector<int> & arr) {
        if(!root) return;
        traverse(root->left, arr);
        arr.push_back(root->val);
        traverse(root->right, arr);
    }
    void update(TreeNode* root, vector<int>& arr) {
        if(!root) return;
        root->val += accumulate(upper_bound(arr.begin(), arr.end(), root->val), arr.end(), 0);
        update(root->left, arr);
        update(root->right, arr);
    }
};
```

## 思路
中序遍歷

## 複雜度

## 解法二
```C++
class Solution {
private:
    int cur_sum = 0;
public:
    void travel(TreeNode* root){
        if (!root) return;
        if (root->right) travel(root->right);
        
        root->val = (cur_sum += root->val);
        if (root->left) travel(root->left);
    }
    TreeNode* convertBST(TreeNode* root) {
        travel(root);
        return root;
    }
};
```
## 思路
中序遍歷，但從右邊開始做，如此每次節點可以直接累加

## 複雜度