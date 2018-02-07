# [Implement strStr()](https://leetcode.com/problems/implement-strstr/description/)
## Problem
Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack. 
## 二、分析&思路
一旦needle第一个元素不在haystack中，则返回-1；若第一个元素在haystack中存在，则继续遍历，同时记录heedle数组下标，（此时是循环后加一，j++)若下一个元素不相同，停止记录。若j值等于needle长度，则返回此时的haystack数组下标，即与needle[1]相等的元素的数组下标。
## 代码实现
```ruby
int strStr(char* haystack, char* needle) {
    int m=strlen(haystack);
    int n=strlen(needle);
    if(n==0) return 0;  //needle长度为0时，直接返回0
    if(m<n) return -1;  //若haystack长度小于needle,则一定有元素不符合，则一定返回-1
    for(int i=0;i<m;i++)
    { //第一层循环：找到与needle[0]相同的位置
        int j=0;
        if(*(haystack+i)==*(needle+j))
        { //若找到相应位置，开始内层循环，看是否所有的needle都包含在haystack中
            for(;j<n;j++)  //可以加一个i+j<m防止溢出，但是不加也能通过
            {
                if(*(haystack+i+j)!=*(needle+j))
                   break;
            }
            if(j==n)
                return i;
        }
    } 
    //除上述情况要返回索引外，其他情况都要返回-1
    return -1;
}
```
## 总结
注意先要讨论两数组长度导致返回值不同的情况</br>
弄懂题意：照*[分析&思路](#二)来</br>
此问题只有一种情况需要返回索引，所以其他情况可以一并返回-1
