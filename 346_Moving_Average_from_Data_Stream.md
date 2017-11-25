# 346. Moving Average from Data Stream 

[Description](https://leetcode.com/problems/moving-average-from-data-stream/description/)

## First Attemp = 解法一
```C++
class MovingAverage {
public:
    /** Initialize your data structure here. */
    MovingAverage(int size) {
        size_ = size;
        sum_ = 0;
    }
    
    double next(int val) {
        if(q_.size() < size_) {
            q_.push(val);
        }
        else {
            sum_ -= q_.front();
            q_.pop();
            q_.push(val);
        }
        sum_ += val;
        return static_cast<double>(sum_)/q_.size();
    }
private:
    queue<int> q_;
    int sum_;
    int size_;
};

/**
 * Your MovingAverage object will be instantiated and called as such:
 * MovingAverage obj = new MovingAverage(size);
 * double param_1 = obj.next(val);
 */
```

## 思路
用一個queue

## 複雜度
時間複雜度 Amortized O(1)
空間複雜度O(size)

## 解法二
```C++
```
## 思路

## 複雜度