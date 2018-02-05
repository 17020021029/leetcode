# Roman to Integer
## 题目描述
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

就是将一串罗马数字用整型数字表示输出
## 解题过程
这道题是期末考试题，之前也做过一遍，就是为了复习一下（是后面做的easy题都是二叉树啊，我不会！！！，之前手机丢了，下的数据结构的视频都没法看了，再做个之前的题增强一下自信心）
基本思路：遍历，前边的字母代表的整型数字比后边大或相等，则转为整型加到result，否则，取负数加到result

## 代码
#### now
```
int romanToInt(char* s) {
    int toint(char ch)
    {
        switch(ch)
        {
            case 'I':return 1;
            case 'V':return 5;
            case 'X':return 10;
            case 'L':return 50;
            case 'C':return 100;
            case 'D':return 500;
            case 'M':return 1000;
        }
        return 0;
    }
    int result=0;
    for(int i=0;i<strlen(s);i++)
    {
        if((toint(*(s+i)))>=(toint(*(s+i+1))))
            result+=toint(*(s+i));
        else result-=toint(*(s+i));
    }
    return result;
}
```
#### before
```
int romanToInt(char* s)
{
    int toInt(char ch);
    int i;
    int sum=0;
    for(i=1;i<=strlen(s);i++){
         if(toInt(*(s+i-1))<toInt(*(s+i)))
             sum -= toInt(*(s+i-1));  
        else sum += toInt(*(s+i-1));
    }
    return sum;
}
int toInt(char ch){
    switch(ch){
        case 'I':return 1;
        case 'V':return 5;
        case 'X':return 10;
        case 'L':return 50;
        case 'C':return 100;
        case 'D':return 500;
        case 'M':return 1000;
    }
    return 0;
}
```
## 错误代码
翻看之前的错误代码，怎么说呢，可能是已经把正确的思路记住了，我都不太相信那些是我写的

#### Runtime error
这一个思路是，先遍历将所有的字母转为整型放在新的数组里，然后，再遍历。大概是当时觉得两次遍历，时间太长了，而且又重新申请数组，空间也复杂，就放在了一次循环里，结果更错了，实现的还是有问题。
#### Wrong Answer
这个是在计算result的时候出错，由于当时没做笔记，当时的运算规则是什么一时间也看不懂了
##### 部分代码
```
int romanToInt(char* s)
{
    int toInt(char ch);
    int i;
    int sum=0;
    for(i=1;i<=strlen(s);i++){
         if(toInt(*(s+i-1))<toInt(*(s+i)))
             sum += toInt(*(s+i)) - 2*toInt(*(s+i-1));  
        else sum+=toInt(*(s+i));
    }
    return sum;
}
```
