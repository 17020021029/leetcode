# Longest Common Prefix
涉及二维数组的使用
## Problem
Write a function to find the longest common prefix string amongst an array of strings. </br>
## 问题分析
寻找最长的公共前缀字符串</br>
要求返回的是“字符串”
## 解题思路
若字符串个数为0，直接返回空字符串</br>
用第一个字符串与其他的字符串比较，申请一个字符型指针用于返回字符串，赋初始值为第一串字符strs[0],遍历，当找到不相同的地方时，中止要返回的字符串
## 代码实现
```ruby
char* longestCommonPrefix(char** strs, int strsSize) {
    char* str=strs[0];
    if(strsSize==0)
        return "";
    int i,j;
    for(i=1;i<strsSize;i++)
    {
        for(j=0;str[j]&&strs[i][j];j++){
            if(str[j]==strs[i][j])
            continue;
        break;
        }
        str[j]='\0';
    }
    return str;
}
```
## 总结
关键在于记录j的大小，若遍历时，str[j]和strs[i][j]都存在且相等，遍历一直继续，否则终止；终止后的j即为字符不相同时的数组下标
