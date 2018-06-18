# Linked List 鏈表

## 實現一
```C++
class MyLinkedList {
public:
    struct Node {
        Node(int v):val(v), next(nullptr) {}
        Node* next;
        int   val;
    };
    
    void printList() {
        Node* h = head_;
        while(h) {
            cout << h->val << " ";
            h = h->next;
        }
        cout << endl;
    }
    /** Initialize your data structure here. */
    MyLinkedList(): head_(nullptr) {
        
    }
    
    Node* getNode(int index) {
        Node* cur = head_;
        for(int i=0; i<index && cur; ++i) {
            cur = cur->next;
        }
        return cur;
    }
    
    Node* getTail() {
        Node* cur = head_;
        while(cur && cur->next) {
            cur = cur->next;
        }
        return cur;
    }
    
    /** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
    int get(int index) {
        Node* n = getNode(index);
        if(n) {
            return n->val;
        }
        else {
            return -1;
        }
    }
    
    /** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
    void addAtHead(int val) {
        Node* cur = new Node(val);
        if(head_) {
            cur->next = head_;
        }
        head_ = cur;
    }
    
    /** Append a node of value val to the last element of the linked list. */
    void addAtTail(int val) {
        Node* tail = getTail();
        Node* cur = new Node(val);
        if(tail) {
            tail->next = cur;
        }
        else {
            head_ = cur;
        }
    }
    
    /** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
    void addAtIndex(int index, int val) {
        if(index == 0) {
            addAtHead(val);
            return;
        }
        Node* prev = getNode(index-1);
        if(prev) {
            Node* cur = new Node(val);
            cur->next = prev->next;
            prev->next = cur;
        }
    }
    
    /** Delete the index-th node in the linked list, if the index is valid. */
    void deleteAtIndex(int index) {
        Node* cur = getNode(index);
        if(cur) {
            Node* prev = getNode(index-1);
            prev->next = cur->next;
            delete cur;
        }
    }
private:
    Node* head_;
};

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList obj = new MyLinkedList();
 * int param_1 = obj.get(index);
 * obj.addAtHead(val);
 * obj.addAtTail(val);
 * obj.addAtIndex(index,val);
 * obj.deleteAtIndex(index);
 */
```

## 實現二
```C++
class MyLinkedList {
public:
    /** Initialize your data structure here. */
    MyLinkedList():head_(nullptr), tail_(nullptr), size_(0) {
    }
    
    void printList() {
        Node* h = head_;
        while(h) {
            cout << h->val << " ";
            h = h->next;
        }
        cout << endl;
    }
    /** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
    int get(int index) {
        if(index < 0 || index >= size_) return -1;
        Node* h = head_;
        for(int i=0; i<index; ++i) {
            h = h->next;
        }
        return h->val;
    }
    
    /** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
    void addAtHead(int val) {
        Node* cur = new Node(val);
        if(head_) {
            cur->next = head_;
            head_ = cur;
        }
        else {
            head_ = cur;
            tail_ = cur;
        }        
        ++size_;
    }
    
    /** Append a node of value val to the last element of the linked list. */
    void addAtTail(int val) {
        Node* cur = new Node(val);
        if(tail_) {
            tail_->next = cur;
            tail_ = cur;
        }
        else {
            head_ = cur;
            tail_ = cur;
        }
        ++size_;
    }
    
    /** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
    void addAtIndex(int index, int val) {
        if(index < 0 || index > size_) 
            return;
        if(index == 0) {
            addAtHead(val);
            return;
        }
        else if(index == size_) {
            addAtTail(val);
            return;
        }
        else {
            Node* prev = head_;
            for(int i=0; i<index-1; ++i) {
                prev = prev->next;
            }
            Node* cur = new Node(val);
            cur->next = prev->next;
            prev->next = cur;
            ++size_;
        }
    }
    
    /** Delete the index-th node in the linked list, if the index is valid. */
    void deleteAtIndex(int index) {
        if(index < 0 || index >= size_) 
            return;
        if(size_ == 1) {
            Node* cur = head_;
            head_ = nullptr;
            tail_ = nullptr;
            delete cur;
        }
        if(index == 0) {
            Node* cur = head_;
            head_ = cur->next;
            delete cur;
        }
        if(index == size_ - 1) {
            Node* prev = head_;
            //cout << "PREV: " << prev->val << endl;
            while(prev->next != tail_) {
                prev = prev->next;
            }
            //cout << "PREV': " << prev->val << endl;
            prev->next = nullptr;
            delete tail_;
            tail_ = prev;
        }
        else {
            Node* prev = head_;
            for(int i=0; i<index-1; ++i) {
                prev = prev->next;
            }
            Node* cur = prev->next;
            prev->next = cur->next;
            delete cur;
        }
        --size_;
    }
private:
    struct Node {
        Node(int v): val(v), next(nullptr) {
            
        }
        Node* next;
        int  val;
    };
    Node* head_;
    Node* tail_;
    int  size_;
};

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList obj = new MyLinkedList();
 * int param_1 = obj.get(index);
 * obj.addAtHead(val);
 * obj.addAtTail(val);
 * obj.addAtIndex(index,val);
 * obj.deleteAtIndex(index);
 */
```