#

[Description]()

## First Attemp = 解法一
```C++
class Solution {
public:
    int findRadius(vector<int>& houses, vector<int>& heaters) {
        //pivot
        heaters.push_back(-1e9);
        heaters.push_back(2e9);
        sort(houses.begin(),houses.end());
        sort(heaters.begin(), heaters.end());
        int rad = 0;
        
        for(auto house: houses) {
            int lo = 0;
            int hi = heaters.size()-1;
            int mid;
            while(lo < hi) {
                mid = lo + (hi-lo)/2;
                if(heaters[mid] <= house && house < heaters[mid+1]) {
                    break;
                }
                else if(house < heaters[mid]) {
                    hi = mid;
                }
                else if(heaters[mid+1] <= house) {
                    lo = mid + 1;
                }
            }
            rad = max(rad, min(house - heaters[mid], heaters[mid+1] - house));
        }
        return rad;
    }
};
```

## 思路
排序之後找區千

## 檢討
1. 二分搜索要熟練，各種變形，特別是以區間為尋找範圍時注意邊界
2. 標兵(pivot)可以使用

## 複雜度
o(nlogn)

## 解法二
```C++
class Solution {
public:
    int findRadius(vector<int>& houses, vector<int>& heaters) {
        if (heaters.size() == 0) {
            return 0;
        }
        sort(houses.begin(), houses.end());
        sort(heaters.begin(), heaters.end());
        int radius = 0;
        int index = 0;
        for (int i = 0; i < houses.size(); i++) {
            while (index + 1 < heaters.size() && (abs(heaters[index+1] - houses[i]) <= abs(heaters[index] - houses[i]))) {
                index++;
            }
            radius = max(radius, abs(heaters[index] - houses[i]));
        }
        return radius;
    }
};

```
## 思路
由於排序佔了大部分時間，線性搜索即可，簡化代碼