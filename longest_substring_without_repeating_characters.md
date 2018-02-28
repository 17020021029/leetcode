#  Longest Substring Without Repeating Characters
## Problem
Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
## 问题分析
题目很简单，找到最长的没有重复元素的子字符串的长度
## 解题思路
思路一：遍历，从每一个字符起计算其符合的子字符串长度，比较得出最大值
思路二：看到discuss里边的，[具体解析](http://blog.csdn.net/javays1/article/details/47413605)
## 代码实现
思路一
```ruby
int lengthOfLongestSubstring(char* s) {
    int temp,maxlen=-1;;
    int i,j,k;
    int len;
    len=strlen(s);
    int count;
    if(len==0)
        return 0; //因为初始maxlen为0，所以不要省略长度为0的情况
    for(i=0;i<len;i++)  //第一层循环，标记初始子字符串
    {
        j=i+1;
        count=0;    //若遇到相同的元素，则改为1
        temp=1;
        while(j<len && count==0)
        {
            k=i;
            while(k<j)
            {
                if(s[j]!=s[k])
                    k++;
                else{
                    count=1;
                    break;
                }
            }
            if(k==j)
            {
                j++;
                temp++;
            }
        }
        maxlen=maxlen>temp?maxlen:temp;
    }
    return maxlen;
}
```
思路二
```ruby
int lengthOfLongestSubstring(char* s)
{
	int len=0;
    char *end=s,*temp;
	char* addressTable[128]={NULL};
	while(*end){
		temp = addressTable[*end];
		addressTable[*end]=end;
		if(temp>=s){
		len=end-s>len?end-s:len;
		s = temp+1;
		}end++;
	}
	len=end-s>len?end-s:len;
	return len;
}
```




