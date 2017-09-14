# 606. Construct String from Binary Tree 

[Description](https://leetcode.com/problems/construct-string-from-binary-tree/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    void traverse(TreeNode* r, string& ans) {
        if(!r) return;
        ans += to_string(r->val);
        if(r->left == NULL && r->right == NULL) return;
        ans += "(";
        traverse(r->left, ans);
        ans += ")";
        if(r->right) {
            ans += "(";
            traverse(r->right, ans);
            ans += ")";
        }
    }
    string tree2str(TreeNode* t) {
        string ans;
        if(!t) return ans;
        traverse(t, ans);
        return ans;
    }
};
```

## 思路
Tree Traverse

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度