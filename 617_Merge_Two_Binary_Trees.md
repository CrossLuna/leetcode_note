# 617. Merge Two Binary Trees 

[Description](https://leetcode.com/problems/merge-two-binary-trees/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    TreeNode* mergeTrees(TreeNode* t1, TreeNode* t2) {
        if(!t1 && !t2) return NULL;
        if(!t1) {
            return t2;
        }
        else if(!t2) {
            return t1;
        }
        else {
            t1->val += t2->val;
            t1 -> left = mergeTrees(t1->left, t2->left);
            t1 -> right = mergeTrees(t1->right, t2->right);
            return t1;
        }
    }
};
```

## 思路
遞迴，處理好邊界就好

## 複雜度

## TODO
## 解法二
```C++
```
## 思路
迭代

## 複雜度