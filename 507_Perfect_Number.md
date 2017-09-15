# 507. Perfect Number 

[Description](https://leetcode.com/problems/perfect-number/description/)

## 解法一
```C++
class Solution {
public:
    bool checkPerfectNumber(int num) {
        if(num == 1) return false;
        int sum = 1;
        for(int n=2; n <= num/n; ++n) {
            if(num % n == 0) {
                if(num/n == n) sum += n;
                else {
                    sum += n;
                    sum += num/n;
                }
            }
        }
        return sum == num;
    }
};
```

## 思路

## 複雜度

## 解法二
```C++
class Solution {
public:
    int pn(int p) {
        return (1 << (p-1)) * ((1 << p)-1);
    }
    bool checkPerfectNumber(int num) {
        vector<int> primes {2, 3, 5, 7, 13, 17, 19, 31};
        for(int prime: primes) {
            if(pn(prime) == num)
                return true;
        }
        return false;
    }
};
```
## 思路
Euclid-Euler Theore，梅森質數法
## 複雜度