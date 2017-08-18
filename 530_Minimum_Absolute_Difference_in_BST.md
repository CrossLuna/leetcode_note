530. Minimum Absolute Difference in BST

[Description](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/)

## First Attemp = 解法一
```C++
class Solution {
public:

    void inorder(TreeNode* root, vector<int>& arr) {
        if(!root) return;
        inorder(root->left, arr);
        arr.push_back(root->val);
        inorder(root->right, arr);
    }
    
    int getMinimumDifference(TreeNode* root) {
        vector<int> arr;
        inorder(root, arr);
        int min_dist = arr[1] - arr[0];
        for(int i=1; i<arr.size()-1; ++i) {
            min_dist = min(min_dist, arr[i+1] - arr[i]);
        }
        return min_dist;
    }
};
```

## 思路
中序遍歷就是sorted array，再按題目要求算出difference即可

## 複雜度
時間O(n)，空間O(n)


## 解法二
```C++
void inorderTraverse(TreeNode* root, int& val, int& min_dif) {
    if (root->left) inorderTraverse(root->left, val, min_dif);
    if (val >= 0) min_dif = min(min_dif, root->val - val);
    val = root->val;
    if (root->right) inorderTraverse(root->right, val, min_dif);
}
int getMinimumDifference(TreeNode* root) {
    auto min_dif = INT_MAX, val = -1;
    inorderTraverse(root, val, min_dif);
    return min_dif;
}
```

## 思路
基本想法相同，注意如何當下就求diff的技巧
