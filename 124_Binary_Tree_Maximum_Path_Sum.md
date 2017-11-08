#

[Description]()

## First Attemp = 解法一
```C++
class Solution {
public:
    int find_max(TreeNode* r) {
        if(!r) return 0;
        int val_this = r -> val;
        int max_tmp = val_this;
        int val_left = find_max(r->left);
        int val_right = find_max(r->right);
        max_path_val = max(max_path_val, val_this + val_left + val_right);
        max_tmp = max(max_tmp, val_this + val_left);
        max_tmp = max(max_tmp, val_this + val_right);
        max_path_val = max(max_path_val, max_tmp);
        return max_tmp;
    }
    int maxPathSum(TreeNode* root) {
        if(!root) return 0;
        max_path_val = root->val;
        find_max(root);
        return max_path_val;
    }
private:
    int max_path_val;
};
```

## 思路
深度優先搜索，路徑分成四種

## 複雜度
O(n)

## 解法二
```C++
class Solution {
    int maxToRoot(TreeNode *root, int &re) {
        if (!root) return 0;
        int l = maxToRoot(root->left, re);
        int r = maxToRoot(root->right, re);
        if (l < 0) l = 0;
        if (r < 0) r = 0;
        if (l + r + root->val > re) re = l + r + root->val;
        return root->val += max(l, r);
    }
public:
    int maxPathSum(TreeNode *root) {
        int max = -2147483648;
        maxToRoot(root, max);
        return max;
    }
};
```
## 思路

## 複雜度