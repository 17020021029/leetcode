# Integer to Roman
harder than "Roman t Integer"也是期末考试题
## Problem
Given an integer, convert it to a roman numeral.
Input is guaranteed to be within the range from 1 to 3999.
## 解题过程
### 一
题目范围是1到3999，不是很大，因此可以直接将字符连起来，每次减去能表示的最大整数，将表示的字符连起来。

但是，有个问题，c里没有string类型，就是忘了这一点，这种解法不能通过

```
char* intToRoman(int num) {
        char *str;    
        char symbol[]={"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};    
        int value[]={1000,900,500,400,100,90,50,40,10,9,5,4,1};   
        for(int i=0;num!=0;++i)  
        {  
            while(num>=value[i])  
            {  
                num-=value[i];  
                str+=symbol[i];  
            }  
        }  
        return str;  
}
```
### 二
干脆用c++试一次，结果：初始化太多字符
```
class Solution {
public:
    string intToRoman(int num) {
        char *str;    
        char symbol[]={"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};    
        int value[]={1000,900,500,400,100,90,50,40,10,9,5,4,1};   
        for(int i=0;num!=0;++i)  
        {  
            while(num>=value[i])  
            {  
                num-=value[i];  
                str+=symbol[i];  
            }  
        }  
        return str;  
    }
};
```
### 三
实在不想再想其它算法，干脆分类讨论
```ruby
class Solution {
public:
    string intToRoman(int num) {
        string s;       
        if (num >= 1000) {
            while (num >= 1000) {
                s += 'M';
                num -= 1000;
            }
        }   
        if (num >= 900) {
            s += "CM";
            num -= 900;
        }
        if (num >= 500) {
            s += 'D';
            num -= 500;
        }
        if (num >= 400) {
            s += "CD";
            num -= 400;
        }
        while (num >= 100) {
            s += 'C';
            num -= 100;
        }       
        if (num >= 90) {
            s += "XC";
            num -= 90;
        }
        if (num >= 50) {
            s += 'L';
            num -= 50;
        }
        if (num >= 40) {
            s += "XL";
            num -= 40;
        }
        while (num >= 10) {
            s += 'X';
            num -= 10;
        }    
        if (num >= 9) {
            s += "IX";
            num -= 9;
        }
        if (num >= 5) {
            s += 'V';
            num -= 5;
        }
        if (num >= 4) {
            s += "IV";
            num -= 4;
        }
        while (num > 0) {
            s += 'I';
            num--;
        }       
        return s;
    }
};
```
## 反思
很多用法还是不熟练，不能用来解决问题

之后还得再回头做这道题

另外[string类型](http://blog.csdn.net/tengfei461807914/article/details/52203202)的用法
## C++算法
```ruby
class Solution {
public:
    string intToRoman(int num) {
        char* c[4][10]={
            {"","I","II","III","IV","V","VI","VII","VIII","IX"},
            {"","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"},
            {"","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"},
            {"","M","MM","MMM"}
        };
        string roman;
        roman.append(c[3][num / 1000 % 10]);    //将字符（串）连接到roman字符串后边
        roman.append(c[2][num / 100 % 10]);
        roman.append(c[1][num / 10 % 10]);
        roman.append(c[0][num % 10]);
         
        return roman;
    }
};
```
