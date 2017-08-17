# 396. Rotate Function 

[Description](https://leetcode.com/problems/rotate-function/description/)

## First Attemp
``` C++
class Solution {
public:
    int maxRotateFunction(vector<int>& A) {
        vector<int> F;
        int f_0;  // !!! trash value
        int N = A.size();
        int sum = 0;
        for(int i = 0; i < N; ++i) {
            f_0 += i * A[i];
            sum += A[i];
        }
        F.push_back(f_0);
        for(int i = 1; i < N; ++i) {
            F.push_back(F[i-1] + sum - 4*A[N-i]);
        }
        return *max_element(F.begin(), F.end());
    }
};
```

## 思路
仔細觀察F(k)結構發現，
F[0] = 0A + 1B + 2C + 3D
F[1] = 0D + 1A + 2B + 3C
...  

F[1] = F[0] + sum - 4 * D = F[0] + sum - 4 * A[3];
也就是

F[i] = F[i-1] + sum - N * A[N-i]

## 解法一
``` C++
class Solution {
    typedef long long LL;
public:
    int maxRotateFunction(vector<int>& A) {
        vector<LL> F;
        LL f_0 = 0;
        int N = A.size();
        LL sum = 0;
        for(int i = 0; i < N; ++i) {
            f_0 += i * A[i];
            sum += A[i];
        }
        F.push_back(f_0);
        for(int i = 1; i < N; ++i) {
            F.push_back(F[i-1] + sum - N*A[N-i]);
        }
        return *max_element(F.begin(), F.end());
    }
};
```

## 複雜度
O(n)


## 檢討
1. 變數初始化！！！！
2. 記得一般化時，特殊例子值要改成變數
3. 注意整數範圍，小心overflow，適當時機用long long

## 解法二(參考)
```C++

```

## 思路