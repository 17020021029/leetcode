# Count and Say
迭代
## Problem
The count-and-say sequence is the sequence of integers with the first five terms as following:

1.     1
2.     11
3.     21
4.     1211
5.     111221

1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.

Given an integer n, generate the nth term of the count-and-say sequence.

Note: Each term of the sequence of integers will be represented as a string. 
## 分析&解题思路
题意是从第一行为1开始，一直读出来作为下一行，像例子一样。</br>
题意本身就包含着递归迭代；计数的过程包括遍历，要注意int和字符的转换
## 代码实现
```ruby
char* countAndSay(int n) {
    if(n == 1) 
      return "1";
    char * result = malloc(2);
    char * temp;
    result[0] = '1';
    result[1] = 0;
    int len, idx, j, count;
    for(int i = 2; i <= n; i++) {
        len = strlen(result);
        temp = malloc(3 * len);
        memset(temp, 0, 3 * len); 
        count = 1;
        for(idx = 1; idx < len; idx++)
        {
            j=0;
            if(result[idx] == result[idx - 1]) count++;
            else
            {
                temp[j++] = '0' + count;  
                temp[j++] = result[idx - 1];
                count = 1;
            }
        }
        temp[j++]='0'+count;
        temp[j]=result[len-1];
        free(result);  //free():与malloc()函数配对使用，释放malloc函数申请的动态内存
        result = temp;
    }
 return result;   
}
```
## 总结
[free()](https://baike.baidu.com/item/free%28%29/9848328?fr=aladdin)</br>
[sizeof与strlen的区别](http://blog.csdn.net/21aspnet/article/details/1539951)
