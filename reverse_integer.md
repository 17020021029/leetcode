# Reverse Integer
整数反转
## Problem
Given a 32-bit signed integer, reverse digits of an integer.
## 分析
注意题目为32个字节整型，因此最终返回为long int
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
```
## Approach2
利用除法和mod运算
### 代码实现
```ruby
int reverse(int x) {
    int sign;
    if(x>0)
        sign=1;
    else{
        sign=-1;
        x=abs(x);
    }
    long result=0;
    while(x>0)
    {  
        result=result*10+x%10;
        x=x/10;
    }
    if(result>2147483647)
        return 0;
    return result*sign;
}
```
