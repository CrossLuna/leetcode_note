# 23. Merge k Sorted Lists

[Description](https://leetcode.com/problems/merge-k-sorted-lists/description/)

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
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        ListNode* dum = new ListNode(-1);
        ListNode* p = dum;
        auto comp = [](ListNode* a, ListNode* b) {
            return a->val > b->val;
        };
        priority_queue<ListNode*, vector<ListNode*>, decltype(comp)> pq(comp);
        for(auto n: lists) {
            if(n) {
                pq.push(n);
            }
        }
        while(pq.size() > 0) {
            auto t = pq.top();
            pq.pop();
            if(t->next) {
                pq.push(t->next);
            }
            p->next = t;
            p = t;
        }
        auto ans = dum->next;
        delete dum;
        return ans;
    }
};
```

## 思路
用優先級隊列，每次取出要放的node之後，將其下一個放入隊列中，  
注意自訂compare的寫法

## 複雜度
O(NlogN)
N是List中所有Node的總和

## 解法二
```C++
```
## 思路

## 複雜度