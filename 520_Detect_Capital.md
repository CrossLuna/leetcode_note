# 520. Detect Capital

[Description](https://leetcode.com/problems/detect-capital/description/)

## First Attemp
``` C++
class Solution {
public:
    bool detectCapitalUse(string word) {
        bool first_cap = isupper(word[0]);
        bool ans = true;
        if(first_cap) {
            if(word.size() > 1) {
                if(isupper(word[1])) {
                    for(int i=2; i<word.size(); ++i) {
                        if(islower(word[i])) {
                            ans = false;
                            break;
                        }
                    }
                }
                else {
                    for(int i=2; i<word.size(); ++i) {
                        if(isupper(word[i])) {
                            ans = false;
                            break;
                        }
                    }
                }
            }
        }
        else {
            for(size_i i = 1; i < word.size(); ++i) { // compilation error
                if (isupper(word[i])) {
                    ans = false;
                    break;
                }
            }
        }
        return ans;
    }
};
```

## 思路
根據規則撰寫選擇結構

## 解法一
``` C++
class Solution {
public:
    bool detectCapitalUse(string word) {
        bool first_cap = isupper(word[0]);
        bool ans = true;
        if(first_cap) {
            if(word.size() > 1) {
                if(isupper(word[1])) {
                    for(int i=2; i<word.size(); ++i) {
                        if(islower(word[i])) {
                            ans = false;
                            break;
                        }
                    }
                }
                else {
                    for(int i=2; i<word.size(); ++i) {
                        if(isupper(word[i])) {
                            ans = false;
                            break;
                        }
                    }
                }
            }
        }
        else {
            for(size_t i = 1; i < word.size(); ++i) {
                if (isupper(word[i])) {
                    ans = false;
                    break;
                }
            }
        }
        return ans;
    }
};

```

## 複雜度
O(n)


## 檢討
1. size_t 不要拼錯
2. index的資料類型要統一，不要一下int一下size_t

## 解法二(參考)
```C++
class Solution {
public:
    bool detectCapitalUse(string word) {
        int cnt = 0;
        for(auto ch: word) {
            if(isupper(ch)) ++cnt;
        }
        return (cnt == 0 || cnt == word.size() || cnt==1 && isupper(word[0]));
    }
};
```

## 思路
基本相同，語法更concise，隨時思考怎麼用簡單且濃縮的語法表達相同概念並維持可讀性