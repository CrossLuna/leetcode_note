# 273. Integer to English Words 

[Description](https://leetcode.com/problems/integer-to-english-words/description/)

## First Attemp = 解法一
```C++
class Solution {
public:
    string three_digit(int num, unordered_map<int, string>& digit_map) {
        string ans;
        if(num/100 > 0) {
            ans += digit_map[num/100];
            ans += " Hundred";
            ans += ' ';
            num %= 100;
        }

        if(num >= 21) {
            ans += digit_map[num/10*10];
            if(num % 10 > 0) {
                ans += ' ';
                ans += digit_map[num% 10];
            }
            ans += ' ';
        }
        else if (num > 0){
            ans += digit_map[num];
            ans += ' ';
        }
        return ans;
    }
    string numberToWords(int num) {
        unordered_map<int, string> digit_map;
        digit_map[0] = "Zero";
        digit_map[1] = "One";
        digit_map[2] = "Two";
        digit_map[3] = "Three";
        digit_map[4] = "Four";
        digit_map[5] = "Five";
        digit_map[6] = "Six";
        digit_map[7] = "Seven";
        digit_map[8] = "Eight";
        digit_map[9] = "Nine";
        digit_map[10] = "Ten";
        digit_map[11] = "Eleven";
        digit_map[12] = "Twelve";
        digit_map[13] = "Thirteen";
        digit_map[14] = "Fourteen";
        digit_map[15] = "Fifteen";
        digit_map[16] = "Sixteen";
        digit_map[17] = "Seventeen";
        digit_map[18] = "Eighteen";
        digit_map[19] = "Nineteen";
        digit_map[20] = "Twenty";
        digit_map[30] = "Thirty";
        digit_map[40] = "Forty";
        digit_map[50] = "Fifty";
        digit_map[60] = "Sixty";
        digit_map[70] = "Seventy";
        digit_map[80] = "Eighty";
        digit_map[90] = "Ninety";

        //return three_digit(num, digit_map);
        if(num == 0) return "Zero";
        string ans;
        int base = 1e9;
        if(num/base > 0) {
            ans += three_digit(num/base, digit_map);
            ans += "Billion ";
            num %= base;
        }
        base /= 1e3;
        if(num/base > 0) {
            ans += three_digit(num/base, digit_map);
            ans += "Million ";
            num %= base;
        }
        base /= 1e3;
        if(num/base > 0) {
            ans += three_digit(num/base, digit_map);
            ans += "Thousand ";
            num %= base;
        }
        ans += three_digit(num, digit_map);
        ans.pop_back();
        return ans;
    }
};
```

## 思路

## 複雜度

## 解法二
```C++
class Solution {
public:
    static string numberToWords(int n) {
        if(n == 0) return "Zero";
        else return int_string(n).substr(1);
    }
private:
    static const char * const below_20[];
    static const char * const below_100[];
    static string int_string(int n) {
        if(n >= 1000000000)   return int_string(n / 1000000000) + " Billion" + int_string(n - 1000000000 * (n / 1000000000));
        else if(n >= 1000000) return int_string(n / 1000000) + " Million" + int_string(n - 1000000 * (n / 1000000));
        else if(n >= 1000)    return int_string(n / 1000) + " Thousand" + int_string(n - 1000 * (n / 1000));
        else if(n >= 100)     return int_string(n / 100) + " Hundred" + int_string(n - 100 * (n / 100));
        else if(n >= 20)      return string(" ") + below_100[n / 10 - 2] + int_string(n - 10 * (n / 10));
        else if(n >= 1)       return string(" ") + below_20[n - 1];
        else return "";
        }
    }
};

const char * const Solution::below_20[] =  {"One", "Two", "Three", "Four","Five","Six","Seven","Eight","Nine","Ten", "Eleven","Twelve","Thirteen","Fourteen","Fifteen","Sixteen","Seventeen","Eighteen","Nineteen"};
const char * const Solution::below_100[] = {"Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"};
```
## 思路

## 複雜度