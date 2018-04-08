# 812. Largest Triangle Area

[Description](https://leetcode.com/contest/weekly-contest-79/problems/largest-triangle-area/)

## 解法一
```C++
class Solution {
public:
    double len(int a, int b) {
        return sqrt(a*a + b* b);
    }
    double area(vector<int> a, vector<int> b, vector<int> c) {
        int A0 = b[0]-a[0];
        int A1 = b[1]-a[1];
        int B0 = c[0]-a[0];
        int B1 = c[1]-a[1];
        double Alen = len(A0, A1);
        double Blen = len(B0, B1);
        double costheta = 1.0 * (A0 *B0 + A1*B1) / (Alen * Blen);
        double sintheta = sqrt(1 - costheta * costheta);
        double ans = AA * BB * sintheta * 0.5;
        if(ans < 0) return 0;
        return ans;
    }
    double largestTriangleArea(vector<vector<int>>& points) {
        int N = points.size();
        double ans = 0.0;
        for(int i=0; i<N; ++i) {
            for(int j=i+1; j<N; ++j) {
                for(int k=j+1; k<N; ++k) {
                    ans = max(ans, area(points[i], points[j], points[k]));
                }
            }
        }
        return ans;
    }
};
```

## 思路

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度