# 199. Binary Tree Right Side View 

[Description](https://leetcode.com/problems/binary-tree-right-side-view/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    vector<int> rightSideView(TreeNode* root) {
        vector<int> ans;
        if(!root) return ans;
        queue<TreeNode*> q1;
        queue<TreeNode*> q2;
        q1.push(root);
        while(!q1.empty()) {
            ans.push_back(q1.back()->val);
            while(!q1.empty()) {
                auto p = q1.front();
                if(p->left) q2.push(p->left);
                if(p->right) q2.push(p->right);
                q1.pop();
            }
            swap(q1, q2);
        }
        return ans;
    }
};
```

## 思路
層次遍歷，取每個queue最右邊值

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度