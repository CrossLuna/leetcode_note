# 690. Employee Importance 

[Description](https://leetcode.com/problems/employee-importance/description/)

## First Attemp = 解法一
```C++
/*
// Employee info
class Employee {
public:
    // It's the unique ID of each node.
    // unique id of this employee
    int id;
    // the importance value of this employee
    int importance;
    // the id of direct subordinates
    vector<int> subordinates;
};
*/
class Solution {
public:
    Employee* find_emp(vector<Employee*>& employees, int id) {
        for(auto e: employees) {
            if(e->id == id) return e;
        }
        return NULL;
    }
    int get_value(vector<Employee*>& employees, Employee* e) {
        if(!e) return 0;
        int value = e->importance;
        for(int sub_id: e->subordinates) {
            auto e = find_emp(employees, sub_id);
            value += get_value(employees, e);
        }
        return value;
    }
    int getImportance(vector<Employee*> employees, int id) {
        return get_value(employees, find_emp(employees, id));
    }
};
```

## 思路
遞迴遍歷員工樹

## 複雜度
O(# of 員工)

## 解法二
```C++
```
## 思路

## 複雜度