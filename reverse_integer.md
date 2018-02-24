# Reverse Integer
整数反转
## Problem
Given a 32-bit signed integer, reverse digits of an integer.
## Approach1
将整型转化为字符型数组处理
### 代码实现
```ruby
int reverse(int x)
{
  long result;
  char temp;
  int sign;
  int length;
  if(x>0)
    sign=1;
  else {
    sign=-1;
    x=abs(x);
    }
  sprintf(string,"%d,x);
  length=strlen(string);
  for(int i=0;i<length/2;i++)
  {
    temp=string[i];
    string[i]=string[length-1-i];
    string[length-1-i]=temp;
    }
    result=atol(string);
    if(result>2147483647||result<-2147483648)
      return 0;
     return (int)result*sign;
}
## Approach2
### 代码实现
