# 148. Sort List

[Description](https://leetcode.com/problems/sort-list/description/)

## 解法一
```C++
class Solution {
public:
    ListNode* merge(ListNode* slow, ListNode* fast) {
        ListNode* dm = new ListNode(-1);
        ListNode* h = dm;
        while(slow && fast) {
            if(fast->val < slow->val) {
                h->next = fast;
                fast = fast->next;
            }
            else {
                h->next = slow;
                slow = slow->next;
            }
            h = h->next;
        }

        if(slow) {
            h->next = slow;
        }
        if(fast) {
            h->next = fast;
        }

        return dm->next;
    }
    ListNode* sortList(ListNode* head) {
        if(head == nullptr || head->next == nullptr) return head;
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast->next && fast->next->next) {
            slow = slow->next;
            fast = fast->next->next;
        }
        fast = slow->next;
        slow->next = nullptr;
        head = sortList(head);
        fast = sortList(fast);
        head = merge(head, fast);
        return head;
    }
};
```

## 思路
Top-Bottom Merge Sort

## 複雜度
O(nlogn)

## 解法二
```C++
class Solution {
public:
    /*
    divide n elements starting from head
    if not enough n elements, return NULL
    */
    ListNode* divide(ListNode* head, int n) {
        ListNode* tail = head;
        for(int i=0; i<n-1 && tail; ++i) {
            tail = tail->next;
        }
        if(tail == nullptr || tail->next == nullptr) return nullptr;
        ListNode* second = tail->next;
        tail->next = nullptr;
        return second;
    }
    /*
    * Merge two list and return the tail pointer
    */
    ListNode* merge(ListNode* left, ListNode* right, ListNode* head) {
        ListNode* p = head;
        while(left && right) {
            if(right->val < left->val) {
                p->next = right;
                right = right->next;
            }
            else {
                p->next = left;
                left = left->next;
            }
            p = p->next;
        }
        
        if(left) {
            p->next = left;
        }
        if(right) {
            p->next = right;
        }
        
        while(p->next) {
            p = p->next;
        }
        return p;        
    }
    
    void printList(ListNode* h) {
        while(h) {
            cout << h->val << " ";
            h = h->next;
        }
        cout << endl;
    }
    
    ListNode* sortList(ListNode* head) {
        if(head == nullptr || head->next == nullptr) return head;
        ListNode* dummy = new ListNode(-2);
        dummy->next = head;
        int len = 0;
        ListNode* h = head;
        while(h) {
            ++len;
            h = h->next;
        }
        
        ListNode* tail = dummy;
        for(int base = 1; base < len; base <<= 1) {
            h = dummy->next;
            tail = dummy;
            while(h) {
                ListNode* left = h;
                ListNode* right = divide(left, base);
                h = divide(right, base);
                tail = merge(left, right, tail);
                
            }
        }
        ListNode* ans = dummy->next;
        delete dummy;
        return ans;
    }
};
```
## 思路
Bottom-Up Merge Sort

## 複雜度
O(nlogn)