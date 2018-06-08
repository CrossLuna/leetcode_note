# 841. Keys and Rooms

[Description](https://leetcode.com/problems/keys-and-rooms/description/)

## 解法一
```C++
class Solution {
public:
    bool canVisitAllRooms(vector<vector<int>>& rooms) {
        int N = rooms.size();
        vector<bool> hm (N, false);
        hm[0] = true;
        queue<int> q;
        q.push(0);
        for(auto k: rooms[0]) {
            q.push(k);
        }

        while(!q.empty()) {
            auto i = q.front();
            if(!hm[i]) {
                hm[i] = true;
                for(auto k: rooms[i]) {
                    q.push(k);
                }
            }
            p.pop();
        }

        for(auto b: hm) {
            if(!b) return false;
        }
        return true;
    }
};
```

## 思路
Hashmap，遍歷每個鑰匙

## 複雜度
時間複雜度 O(Keys)
空間複雜度 O(Rooms)

## 解法二
```C++
```
## 思路

## 複雜度