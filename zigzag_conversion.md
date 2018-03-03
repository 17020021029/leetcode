# ZigZag Conversion
锯齿形转换
## Problem
 The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
````
P   A   H   N
A P L S I I G
Y   I   R
````
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string text, int nRows);

convert("PAYPALISHIRING", 3) should return "PAHNAPLSIIGYIR". 
## 问题分析
关键是明白题意找到规律：
1. 题意是给定一个字符串和行数，将按锯齿形排列，然后逐行顺序读出字符；
2. 第一行和最后一行每个字符的索引相差2*numRows-2；
3. 中间几行索引离本次循环的距离为2*numRows-2*i；
## 代码实现
```ruby
char* convert(char* s, int numRows) {
    if(s==NULL || numRows<1)
        return NULL;
    int len=strlen(s);
    char* result=(int*)malloc(sizeof(char)*(len+1));
    char *p=result;
    result[len]='\0';
    if(numRows ==1)
        return s;
    for(int row=0;row<numRows;row++)
    {
        for(int i=row;i<len;i+=2*numRows-2)
        {
            *result++ =s[i];
            if(row>0 && row<numRows-1 && (i+2*numRows-2-2*row)<len)
            {
                *result++ =s[i+2*numRows-2-2*row];
            }
        }
    }
    return p;
}
```
## 总结
解题的关键是找规律
