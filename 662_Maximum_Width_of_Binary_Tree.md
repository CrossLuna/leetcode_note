# 662. Maximum Width of Binary Tree 

[Description](https://leetcode.com/problems/maximum-width-of-binary-tree/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        if(!root) return 0;
        int ans = 1;
        queue<int> q_curr_num;
        queue<TreeNode*> q_curr_node;
        queue<int> q_next_num;
        queue<TreeNode*> q_next_node;
        q_curr_num.push(0);
        q_curr_node.push(root);
        while(!q_curr_node.empty()) {
            if(q_curr_num.size() > 1) ans = max(ans, q_curr_num.back()-q_curr_num.front()+1);
            while(!q_curr_node.empty()) {
                TreeNode* p = q_curr_node.front();
                int f = q_curr_num.front();
                if(p->left) {q_next_node.push(p->left); q_next_num.push(2*f);}
                if(p->right) {q_next_node.push(p->right); q_next_num.push(2*f+1);}
                q_curr_num.pop();
                q_curr_node.pop();
            }
            swap(q_curr_num, q_next_num);
            swap(q_curr_node, q_next_node);
        }
        return ans;
    }
};
```

## 思路
兩個queue，層次遍歷，BFS

## 複雜度
O(n)

## 解法二
```C++
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        vector<int> lefts; // left most nodes at each level;
        int maxwidth = 0;
        dfs(root, 1, 0, lefts, maxwidth);
        return maxwidth;
    }
private:
    void dfs(TreeNode* node, int id, int depth, vector<int>& lefts, int& maxwidth) {
        if (!node) return;
        if (depth >= lefts.size()) lefts.push_back(id);  // add left most node
        maxwidth = max(maxwidth, id + 1 - lefts[depth]);
        dfs(node->left, id * 2, depth + 1, lefts, maxwidth);
        dfs(node->right, id * 2 + 1, depth + 1, lefts, maxwidth);
    }
};
```
## 思路
DFS

## 複雜度
O(n)