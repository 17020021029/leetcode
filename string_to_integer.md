# String to Integer
自写atoi函数
## Problem
Implement atoi to convert a string to an integer.

Hint: Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

Notes: It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.

Requirements for atoi:

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned. If the correct value is out of the range of representable values, INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.
## 分析
题目给了很多提示
1. 跳过空格，找到开始转化为整型的位置
2. 最终的整数是有正负的
3. 跳过不符合转化的字符
4. 最终的整数可能超出整型范围，则返回INT_MIN或INT_MAX
## 代码实现
```ruby
int myAtoi(char* str) {
    char *s = str;
    while (*s && *s==' ')   //跳过空格
        s++;
    int result=0;
    if (*s){
        int sign = 1;
        if (*s == '+')
            s++;
        else if (*s == '-') {
            sign = -1;
            s++;
        }
    //跳过可代表正负的符号，并记录正负
        while (*s && (*s)>='0' && (*s)<='9') {  //跳过不符合转化为整数的字符
            int temp=result;
            result=result*10 + (*s++ - '0'); //计算除正负以外的整数
            if (result/10 != temp) { //若整数超过了整型范围，则返回要求的情况
                if (sign<0)
                    return INT_MIN;
                else 
                    return INT_MAX;
            }
        }    
        result=result*sign; //最后返回的数值有正负
    }
    return result;
}
```
