# 116. Populating Next Right Pointers in Each Node 
[Description](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    void connect(TreeLinkNode *root) {
        if(!root) return;
        if(root->left) {
            root->left->next = root->right;
            if(root->next) {
                root->right->next = root->next->left;
            }
            connect(root->left);
            connect(root->right);
        }
    }
};
```

## 思路
關鍵是使用已有的資訊，右子樹可以使用到next

## 複雜度
O(n)
空間複雜度O(high)

## 解法二
```C++
class Solution {
public:
    void connect(TreeLinkNode *root) {
        if(!root) return;
        TreeLinkNode* pre = root;
        TreeLinkNode* cur = NULL;
        while(pre->left) {
            cur = pre;
            while(cur) {
                cur->left->next = cur->right;
                if(cur->next) cur->right->next = cur->next->left;
                cur = cur->next;
            }
            pre = pre->left;
        }
    }
};
```
## 思路
使用一個節點紀錄每層最左，再開始連結下一層

## 複雜度
O(n)