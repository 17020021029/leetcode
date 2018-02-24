# Pow(x,n)
幂函数
## Problem
自写一个幂函数
## Approach
### 方法一
基于学习幂函数时的方法，判断 n 的正负，若 n 小于0，则将 x 化作其倒数；for循环中连乘。但是超时，时间太复杂，需要再设计算法减小时间复杂度
#### 代码实现
```
double myPow(double x, int n) {
    long long N=n;
    if(N<0)
    {
        x=1/x;
        N=-N;
    } //判断n的正负
    double result=1;
    for(long long i=0;i<N;i++)
    {
        result=result*x;
    }
    return result;
}
```
### 方法二
不再一次一次相乘，将temp每次加倍相乘，此时循环i有奇偶之分；若当前i为奇数，不要再翻倍相乘，把当前的temp与要返回的数值相乘，否则，加倍相乘
### 代码实现
```ruby
double myPow(double x, int n) {
    long long N=n;
    if(N<0)
    {
        x=1/x;
        N=-N;
    }
    double result=1;
    double temp=x;
    for(long long i=N;i;i/=2)
    {
        if(i%2==1)
            result=result*temp;
        temp=temp*temp;
    }
    return result;
}
```
