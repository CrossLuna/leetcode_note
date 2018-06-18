# 92. Reverse Linked List II

[Description](https://leetcode.com/problems/reverse-linked-list-ii/description/)

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
    ListNode* reverseBetween(ListNode* head, int m, int n) {
        if(m == n) return head;
        ListNode* dm = new ListNode(-2);
        ListNode* p = dm;
        dm->next = head;
        for(int i=0; i<m-1; ++i) {
            p = p->next;
            head = head->next;
        }
        ListNode* left = p;
        ListNode* rear = head;

        ListNode* nh = NULL;
        ListNode* nxt = head->next;
        while(m++ < n) {
            head->next = nh;
            nh = head;
            head = nxt;
            nxt = head->next;
        }
        left->next = head;
        rear->next = nxt;
        head->next = nh;
        ListNode* ans = dm->next;
        delete dm;
        return ans;
    }
};
```

## 思路
利用dummy指針，記得求的是`prev`，其他就是小心邊界條件

## 複雜度
O(n)，one pass