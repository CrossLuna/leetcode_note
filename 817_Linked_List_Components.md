# 817. Linked List Components

[Description](https://leetcode.com/problems/linked-list-components/description/)

## 解法一
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    int numComponents(ListNode* head, vector<int>& G) {
        unordered_set<int> hs;
        for(auto n: G) {
            hs.insert(n);
        }
        bool in_group = false;
        int ans = 0;
        while(head) {
            int v = head->val;
            if(hs.find(v) != hs.end()) {
                if(!in_group) {
                    in_group = true;
                }
                hs.erase(v);
            }
            else {
                if(in_group) {
                    ++ans;
                    in_group = false;
                }
            }
        }
        if(in_group) {
            ++ans;
        }
        return ans;
    }
};
```

## 思路
用哈希集合，小心操作鏈表

## 複雜度
O(n)

## 解法二
```C++
class Solution {
public:
    int numComponents(ListNode* head, vector<int>& G) {
        unordered_set<int> hs(G.begin(), G.end());
        int ans = 0;
        while(head) {
            if(hs.count(head->val) > 0 && (head->next == NULL || hs.count(head->next->val) == 0)) {
                ++ans;
            }
            head = head->next;
        }
        return ans;
    }
};
```
## 思路
將解法一的邏輯精簡化，注意`unordered_set`可以用iterator初始化並且可以用`count`來找尋，
後面將多個條件合併簡化代碼

## 複雜度