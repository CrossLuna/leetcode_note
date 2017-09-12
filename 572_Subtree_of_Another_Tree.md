# 572. Subtree of Another Tree 

[Description](https://leetcode.com/problems/subtree-of-another-tree/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    bool is_same(TreeNode* s, TreeNode* t) {
        if(!s && !t) return true;
        else if(!s || !t) return false;
        else if(s->val != t->val) return false;
        else return is_same(s->left, t->left) && is_same(s->right, t->right);
    }
    bool isSubtree(TreeNode* s, TreeNode* t) {
        queue<TreeNode*> q;
        q.push(s);
        while(!q.empty()) {
            TreeNode* r = q.front();
            if(r->val == t->val && is_same(r, t)) return true;
            if(r->left) q.push(r->left);
            if(r->right) q.push(r->right);
            q.pop();
        }
        return false;
    }
};
```

## 思路
Traverse

## 複雜度
O(n)? O(n^2)??

## 解法二
```C++
```
## 思路
也可以使用preorder traverse，比較是否為子串

## 複雜度