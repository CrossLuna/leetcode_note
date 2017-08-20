#623. Add One Row to Tree 

[Description](https://leetcode.com/problems/add-one-row-to-tree/description/)

## TODO: 尚未AC

## First Attemp
```C++
class Solution {
public:
    TreeNode* addOneRow(TreeNode* root, int v, int d) {
        queue<TreeNode*> q1;
        q1.push(root);
        bool enough_layer = true;
        while(d-- > 2) {
            if(q1.empty()) {
                enough_layer = false;
                break;
            }
            queue<TreeNode*> q2;
            while(!q1.empty()) {
                auto node = q1.front();
                if(node->left) q2.push(node->left);
                if(node->right) q2.push(node->right);
                q1.pop();
            }
            swap(q1, q2);
        }
        if(enough_layer) {
            while(!q1.empty()) {
                auto node = q1.front();
                if(node->left) {
                    TreeNode* new_node = new TreeNode(v);
                    new_node->left = node->left;
                    node->left = new_node;
                }
                if(node->right) {
                    TreeNode* new_node = new TreeNode(v);
                    new_node->right = node->right;
                    node->right = new_node;
                }
                q1.pop();
            }
        }
        return root;
    }
};
```

## 解法一
``` C++
class Solution {
public:
    TreeNode* addOneRow(TreeNode* root, int v, int d) {
        if(d == 1) {
            TreeNode* new_node = new TreeNode(v);
            new_node->left = root;
            return new_node;
        }
        queue<TreeNode*> q1;
        q1.push(root);
        bool enough_layer = true;
        while(d-- > 2) {
            if(q1.empty()) {
                enough_layer = false;
                break;
            }

            queue<TreeNode*> q2;
            while(!q1.empty()) {
                auto node = q1.front();
                if(node->left) q2.push(node->left);
                if(node->right) q2.push(node->right);
                //q3.push(node);
                q1.pop();
            }
            swap(q1, q2);
        }
        if(q1.empty()) {
            return NULL;
        }
        //if(enough_layer) {
        while(!q1.empty()) {
            auto node = q1.front();
            if(node->left) {
                TreeNode* new_node = new TreeNode(v);
                new_node->left = node->left;
                node->left = new_node;
            }
            else {
                TreeNode* new_node = new TreeNode(v);
                node->left = new_node;
            }
            if(node->right) {
                TreeNode* new_node = new TreeNode(v);
                new_node->right = node->right;
                node->right = new_node;
            }
            else {
                TreeNode* new_node = new TreeNode(v);
                node->right = new_node;
            }
            q1.pop();
        }
        return root;
    }
};
```

## 思路
層次遍歷

## 解法二
## TODO: 參考三種解法
```C++
```
## 思路