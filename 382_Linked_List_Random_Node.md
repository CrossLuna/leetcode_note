# 382. Linked List Random Node 

[Description](https://leetcode.com/problems/linked-list-random-node/discuss/)

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
    /** @param head The linked list's head.
        Note that the head is guaranteed to be not null, so it contains at least one node. */
    Solution(ListNode* head) {
        h = head;
    }
    
    /** Returns a random node's value. */
    int getRandom() {
        ListNode* head = h;
        ListNode* next = h->next;
        int cur = head->val;
        int N = 1;
        while(next) {
            ++N;
            if(rand() % N == 0) {
                cur = next->val;
            }
            head = next;
            next = next->next;
        }
        return cur;
    }
private:
    ListNode* h;
};

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(head);
 * int param_1 = obj.getRandom();
 */
```

## 思路
Resevoir Sampling，不知道長度時使用的隨機取樣法

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度