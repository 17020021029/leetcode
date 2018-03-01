# Longest Palindromatic Substring
最长回文子串
## Problem
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example:

Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
 

Example:

Input: "cbbd"

Output: "bb"
## 解题思路
比较暴力的解法：分奇偶情况，遍历找到最大长度的子串
## 代码实现
```ruby
int odd(char* s,int media)
{
    int i=media-1,j=media+1;
    while(i>=0 && s[j])
    {
        if(s[i]!=s[j])
            return j-1;
        i--;
        j++;
    }
    return j-1;
} //找到奇数情况下最后一个回文子串的索引
int even(char* s,int media)
{
    int i=media,j=media+1;
    while(i>=0 && s[j])
    {
        if(s[i]!=s[j])
            return j-1;
        i--;
        j++;
    }
    return j-1;
} //偶数情况
char* longestPalindrome(char* s) {
    int max=1;
    int a,b,end;
    for(int i=0;s[i];i++)
    {
        end=odd(s,i);
        if(max<(end-i)*2+1){
            max=(end-i)*2+1;
            a=i+i-end;
            b=end;
        }
        end=even(s,i);
        if(max<(end-i)*2){
            max=(end-i)*2;
            a=i+i-end+1;
            b=end;
        }
    }
    s[b+1]=0; //清除回文子串后面的元素
    return s+a; 
}
```
## 总结
算法很简单，关键在记录子串最后一个的索引和第一个的索引，清除最后一个之后的字符，然后直接返回字符串
