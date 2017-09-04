# 380. Insert Delete GetRandom O(1) 

[Description](https://leetcode.com/problems/insert-delete-getrandom-o1/description/)

## 解法一
```C++
class RandomizedSet {
public:
    /** Initialize your data structure here. */
    RandomizedSet() {
        
    }
    
    /** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
    bool insert(int val) {
        if(m.find(val) != m.end()) { // already there
		    return false;
		}
		else {
		    m[val] = arr.size();
			arr.push_back(val);
			return true;
		}
    }
    
    /** Removes a value from the set. Returns true if the set contained the specified element. */
    bool remove(int val) {
        if(m.find(val) == m.end()) { // not found
		    return false;
		}
		else {
		    //int last = arr[m[val]];
			int last = arr.back();
			m[last] = m[val];
			//arr[m[val]] = last;
		    swap(arr[m[val]], arr.back());
			arr.pop_back();
			m.erase(val);
			return true;
		}
    }
    
    /** Get a random element from the set. */
    int getRandom() {
        int N = arr.size();
	    return arr[rand() % N];
    }
private:
	vector<int> arr;
	unordered_map<int, int> m;
};
```

## 思路
利用一個vector，一個hashmap維護，刪除時將元素調到尾部就可達成常數。

## 複雜度

## 解法二
```C++
```
## 思路

## 複雜度