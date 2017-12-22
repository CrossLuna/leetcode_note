# 734. Sentence Similarity

[Description](https://leetcode.com/problems/sentence-similarity/description/)

## 解法一
```C++
class Solution {
public:
    bool areSentencesSimilar(vector<string>& words1, vector<string>& words2, vector<pair<string, string>> pairs) {
        if(words1.size() != words2.size()) return false;
        for(int i=0; i<words1.size(); ++i) {
            if(words1[i] == words2[i] ||
                find(pairs.begin(), pairs.end(), make_pair(words1[i], words2[i])) != pairs.end() ||
                find(pairs.begin(), pairs.end(), make_pair(words2[i], words1[i])) != pairs.end())
                continue;
            else
                return false;
        }
        return true;
    }
};
```

## 思路
暴力破解

## 複雜度
O(n^2)

## 解法二
```C++
class Solution {
public:
    bool areSentencesSimilar(vector<string>& words1, vector<string>& words2, vector<pair<string, string>> pairs) {
        if (words1.size() != words2.size()) return false;
        map<string, set<string>> map;
        for (pair<string, string> p : pairs)
            map[p.first].insert(p.second);

        for (int i = 0; i < words1.size(); i++)
            if (words1[i] != words2[i] && !map[words1[i]].count(words2[i]) && !map[words2[i]].count(words1[i]))
                return false;
        return true;
    }
};
```
## 思路
用map解

## 複雜度
O(nlogn)


## 解法三
```C++
class Solution {
public:
    bool areSentencesSimilar(vector<string>& words1, vector<string>& words2, vector<pair<string, string>> pairs) {
        if (words1.size() != words2.size()) return false;
        unordered_map<string, unordered_set<string>> map;
        for (pair<string, string> p : pairs)
            map[p.first].insert(p.second);

        for (int i = 0; i < words1.size(); i++)
            if (words1[i] != words2[i] && !map[words1[i]].count(words2[i]) && !map[words2[i]].count(words1[i]))
                return false;
        return true;
    }
};
```
## 思路
用hashmap解

## 複雜度
O(n)

## 註
可以看出，若用得不好，hashmap的常數級別可能非常慢

