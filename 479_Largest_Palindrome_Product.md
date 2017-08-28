#

[Description]()

## First Attemp
```C++
class Solution {
public:
    bool is_palim(const string& s) {
        int N = s.size();
        for(int i=0; i<N/2; ++i) {
            if(s[i] != s[N-i-1]) {
                return false;
            }
        }
        return true;
    }
    long long power_ten(int n) {
        long long ans = 1;
        while(n-->0) {
            ans *= 10;
        }
        return ans;
    }
    int largestPalindrome(int n) {
        long long max_palim = 0;
        long long i = power_ten(n) - 1;
        long long j = power_ten(n) - 1;
        long long i_min = power_ten(n-1);
        long long j_min = power_ten(n-1);
        for(; i >= i_min; --i ) {
            j = i;
            for(; j >= j_min; --j) {
                long long n = i * j;
                if(is_palim(to_string(n))) {
                    max_palim = max(max_palim, n);
                }
            }
        }
        return max_palim % 1337;
    }
};
```
超時

## Second Attemp
```C++
class Solution {
public:
    long long power_ten(int n) {
        long long ans = 1;
        while(n-->0) {
            ans *= 10;
        }
        return ans;
    }
    bool is_div(long long num, int n) {
        long long x = power_ten(n) - 1;
        long long y = power_ten(n) - 1;
        long long x_min = power_ten(n-1);
        long long y_min = power_ten(n-1);
        for(; x >= x_min; --x) {
            for(y = x; y>= y_min; --y) {
                if(x * y == num) return true;
            }
        }
        return false;
    }
    int largestPalindrome(int n) {
        if(n == 1) return 9;
        long long comp = power_ten(n) - 1;
        long long comp_min = power_ten(n-1);
        for(; comp >= comp_min; --comp) {
            //cout << "COMP: " << comp << endl;
            long long cand = 0;
            for(int i = 0; i < 2*n; ++i) {
                long long digit = (comp / power_ten(i))%10;
                cand += digit * power_ten(n-1-i);
                cand += digit * power_ten(n+i);
            }
            //cout << "CAND: " << cand << endl;
            if(is_div(cand, n)) {
                //cout << "CAND: " << cand << endl;
                return cand % 1337;
            }
        }
        return 0;
    }
};
```
超時

## 解法一


## 思路

## 解法二
```C++
```
## 思路