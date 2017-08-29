#

[Description]()

## First Attemp = 解法一
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        for(auto it=numbers.begin(); *it <= target/2; ++it) {
            auto jt_left = lower_bound(numbers.begin(), numbers.end(), target - *it);
            auto jt_right = upper_bound(numbers.begin(), numbers.end(), target - *it);
            for(auto jt = jt_left; jt != jt_right; ++jt)
                if(*it + *jt == target && it < jt) 
                    return vector<int> {it-numbers.begin()+1, jt-numbers.begin()+1};
        }
    }
};
```

## 思路
二分搜尋

## 複雜度
O(max 元素個數)

## 解法二
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
    int lo=0, hi=numbers.size()-1;
    while (numbers[lo]+numbers[hi]!=target){
        if (numbers[lo]+numbers[hi]<target){
            lo++;
        } else {
            hi--;
        }
    }
    return vector<int>({lo+1,hi+1});
}
};
```
## 思路
簡單線性遍歷

## 複雜度
O(n)