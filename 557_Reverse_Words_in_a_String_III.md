# 557. Reverse Words in a String III 

[Description](https://leetcode.com/problems/reverse-words-in-a-string-iii/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    void inverse_part(string& s, int left, int right) {
        while(left < right) {
            swap(s[left], s[right]);
            ++left;
            --right;
        }
    }
    string reverseWords(string s) {
        int N = s.size();
        int slow = 0;
        int fast = slow;
        while(0 <= slow && slow < N && 0 <= fast && fast < N) {
            fast = s.find(" ", slow);
            if(fast < slow) {
                inverse_part(s, slow, N-1);
                break;
            }
            inverse_part(s, slow, fast-1);
            slow = fast + 1;
        }
        return s;
    }
};
```

## 思路
找到空格，反轉部份

## 複雜度

## 解法二
```C++
class Solution {
public:
    string reverseWords(string s) {
        for (int i = 0; i < s.length(); i++) {
            if (s[i] != ' ') {   // when i is a non-space
                int j = i;
                for (; j < s.length() && s[j] != ' '; j++) { } // move j to the next space
                reverse(s.begin() + i, s.begin() + j);
                i = j - 1;
            }
        }
        
        return s;
    }
};
```
## 思路
可以使用STL的reverse

## 複雜度