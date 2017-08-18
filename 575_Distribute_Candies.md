#575. Distribute Candies 

[Description](https://leetcode.com/problems/distribute-candies/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    int distributeCandies(vector<int>& candies) {
        int N = candies.size();
        unordered_set<int> ss;
        for(auto n: candies) {
            ss.insert(n);
        }

        return min(N/2, static_cast<int>(ss.size()));
    }
};
```

## 思路
貪心，如果糖果比姊妹可拿的數量還多，就拿可拿的最多種
否則有幾種拿幾種

## 複雜度
O(n)

## 解法二
```C++
int distributeCandies(vector<int>& candies) {
    bitset<200001> hash;
    int count = 0;
    for (int i : candies) {
        if (!hash.test(i+100000)) {
            count++;
            hash.set(i+100000);
        }
    }
    int n = candies.size();
    return min(count, n/2);
}
```
## 思路
基本相同，但若hashmap不計數，可用bitset