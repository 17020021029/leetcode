# Pow(x,n)
## 题目描述
就是求浮点数的整数次方，开始觉得medium题怎么emmmm，但是发现事情并不简单，可能涉及时间复杂度是问题，用了好几种算法都不行（自我感觉没问题啊），又有点偷懒
了，不想研究了，先记一下出错的代码

### compile error2

```
double myPow(double x, int n) {
    double funtion_pow(double x)
    {
        double result=1.0;
        result=result*x;
    }
    if(n>0)
    {
        double result;
        while(n--)
        {
            result=funtion_pow(x);
        }
        return result;
    }
    if(n==0)
    {
        return 1.0;
    }
    if(n<0)
    {
        double result;
        while((-n)--)
        {
            result=funtion_pow(1/x);
        }
        return result;
    }
}
```
### compile error1
```
double myPow(double x, int n) {
    if(n>0){
    double result=1;
    for(int i=0;i<n;i++)
    {
        result=result*x;
    }
    return result;
    }
    else if(n<0)
    {
        double result=1;
        double new_x;
        new_x=1/x;
        for(int i=0;i<-n;i++)
        {
            result=result*new_x;
        }
    return result;
    }
    else if(n==0)
    {
        return 1.0;
    }
}
```
*上面程序本质上是一样的，都是分类讨论n的正负，然后循环计算result

### runtime error
这个抱着侥幸的心理直接用了pow函数

找了几种runtime error 的原因
1. 除以零
2. 数组越界：int a[3]; a[10000000]=10;
3. 指针越界：int * p; p=(int *)malloc(5 * sizeof(int)); *(p+1000000)=10;
4. 使用已经释放的空间：int * p; p=(int *)malloc(5 * sizeof(int));free(p); *p=10;
5. 数组开得太大，超出了栈的范围，造成栈溢出：int a[100000000];

*立个flag，明天接着做
