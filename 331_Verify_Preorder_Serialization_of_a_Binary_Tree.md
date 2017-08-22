# 331. Verify Preorder Serialization of a Binary Tree 

[Description](https://leetcode.com/problems/verify-preorder-serialization-of-a-binary-tree/description/)

## First Attemp
```C++
class Solution {
public:
    vector<int> build_serial(string& s) {
        vector<int> arr;
        int front = 0;
        int back = 0;
        while(front < s.size()) {
            while(back < s.size()) {
                if(s[back] == ',') {
                    if(s[front] == '#') {
                        arr.push_back(-1);
                    }
                    else {
                        arr.push_back(stoi(s.substr(front, back-front)));
                    }
                    back++;
                    break;
                }
                back++;
            }
            // last number
            if(back == s.size()) {
                if(s[front] == '#') {
                    arr.push_back(-1);
                }
                else {
                    arr.push_back(stoi(s.substr(front, back-front)));
                }
            }
            front = back;
        }
        return arr;
    }
    bool isValidSerialization(string preorder) {
        vector<int> arr = build_serial(preorder);
        if(arr.size() == 1) {
            if(arr[0] == -1) return true;
            else            return false;
        }
        if(arr[0] == -1 && arr.size() != 1) return false;
        stack<int> s_node;
        stack<int> s_cnt;
        s_node.push(arr[0]);
        s_cnt.push(0);
        for(int i=1; i<arr.size(); ++i) {
            if(arr[i] == -1) {
                if(s_cnt.size() > 0)
                    ++s_cnt.top();
                else
                    return false;
            }
            else {
                if(s_cnt.size() == 0) return false;
                ++s_cnt.top();
                s_node.push(arr[i]);
                s_cnt.push(0);
            }

            while(s_cnt.size() > 0 && s_cnt.top() == 2) {
                s_node.pop();
                s_cnt.pop();
            }
        }

        if(s_node.empty() && s_cnt.empty()) return true;
        return false;
    }
};
```

## 思路
用兩個棧

## 複雜度

## 檢討
1. 使用棧時注意邊界條件
2. 用C++ Parse的routine
```C++
//Input: preorder
//Token: ','
istringstream in(preorder);
vector<string> v;
string val;
while(getline(in, val, ',')) v.push_back(val);
```

## 解法二
```C++
class Solution {
public:
    bool isValidSerialization(string preorder) {
        istringstream in(preorder);
        vector<string> v;
        string val;
        while(getline(in, val, ',')) v.push_back(val);
        int diff = 1;
        for(auto& node: v) {
            if(diff <= 0) return false;
            if(node == "#") --diff;
            else ++diff;
        }
        return diff == 0;
    }
};
```
## 思路
利用入度及出度，注意維持 diff = 出度-入度 = 可塞的leaf數，隨時為正且最後為0
每遇到一個非空節點，可以多提供一個leaf，遇到空節點則是減少一個
想法太絕了


## 複雜度


## 檢討
1. 遇到preorder，想到棧
2. 遇到樹合法性問題，想到入度出度平衡