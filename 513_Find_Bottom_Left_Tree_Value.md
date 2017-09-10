# 513. Find Bottom Left Tree Value 

[Description](https://leetcode.com/problems/find-bottom-left-tree-value/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int findBottomLeftValue(TreeNode* root) {
        queue<TreeNode*> q1;
        queue<TreeNode*> q2;
        q1.push(root);
        int bottom_left;
        while(!q1.empty()) {
            auto r = q1.front();
             bottom_left = r->val;
            while(!q1.empty()) {
                auto f = q1.front();
                if(f->left) q2.push(f->left);
                if(f->right) q2.push(f->right);
                q1.pop();
            }
            swap(q1, q2);
        }
        return bottom_left;
    }
};
```

## 思路
層次遍歷，每次紀錄queue首

## 複雜度
O(# of node)

## 解法二
```C++
```
## 思路

## 複雜度