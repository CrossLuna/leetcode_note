# 285. Inorder Successor in BST 

[Description](https://leetcode.com/problems/inorder-successor-in-bst/description/)

## 解法一
```C++
class Solution {
public:
    TreeNode* leftmost(TreeNode* n) {
        // not null
        if(!n->left) return n;
        else return leftmost(n->left);
    }
    void search(TreeNode* cur, TreeNode* tar, vector<TreeNode*>& vec) {
        vec.push_back(cur);
        if(cur->val == tar->val) return;
        else if(tar->val < cur->val && cur->left) search(cur->left, tar, vec);
        else search(cur->right, tar, vec);
    }
    TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
        if(!root) return nullptr;
        // search
        vector<TreeNode*> vec;
        search(root, p, vec);
        if(p->right) return leftmost(p->right);
        TreeNode* cur = p;
        for(int i=vec.size()-2; i>=0; --i) {
            auto par = vec[i];
            if(par->left == cur) return par;
            cur = par;
        }
        return nullptr;
    }
};
```

## 思路
用一個vector儲存root到target的路徑，沿路向上檢查

## 複雜度
時間複雜度O(h)
空間複雜度O(h)

## 解法二
```C++
class Solution {
public:
    TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
        TreeNode* ans = nullptr;
        while(root) {
            if(p->val < root->val) {
                ans = root;
                root = root->left;
            }
            else root = root->right;
        }
        return ans;
    }
};
```
## 思路
更巧妙控制

## 複雜度
同

## 補充
中序遍歷的前驅與後繼
```C++
TreeNode* successor(TreeNode* root, TreeNode* p) {
    if(!root) return nullptr;
    if(root->val <= p->val) {
        return successor(root->right, p);
    }
    else {
        TreeNode* left = successor(root->left, p);
        if(left) return left;
        return root;
    }
}

TreeNode* predecessor(TreeNode* root, TreeNode* p) {
    if(!root) return nullptr;
    if(root->val >= p->val) {
        return predecessor(root->left, p);
    }
    else {
        TreeNode* right = predecessor(root->right, p);
        if(right) return right;
        return root;
    }
}
```