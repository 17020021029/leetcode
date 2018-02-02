#Sqrt(x)

题目描述

Implement int sqrt(int x).

Compute and return the square root of x.

x is guaranteed to be a non-negative integer.

示例

·Input: 4

 Output: 2
 
·Input: 8

 Output: 2
 
 Explanation: The square root of 8 is 2.82842..., and since we want to return an integer, the decimal part will be truncated.
 
##解题过程

###wrong answer

算法很简单，很暴力，简单的认为只要取中间值缩小范围，再用一次循环遍历找到返回值即可

```
int mySqrt(int x) {
    if(x==0)
        return 0;
    int mid;
    mid=(1+x)/2;
    int i;
    for(i=1;i<=mid;i++)
    {
        if((float)x/i-i==0)
            break;
    }
    return i;
}
```
###accepted

参考discuss，发现我想的确实太简单了，不过开方的情况较少，可以用if列举情况，（不知道为什么，就觉得这种题与中间值有关，缩小运行时间？），好像还是很暴力，应该算二分迭代吧 


思路：
```
int mySqrt(int x){
    if(x == 0)
    {
        return 0;
    }
    int left = 1, right = x;
    int mid = (left + right)/2;
    while(true)
    {
        if(x/mid > mid)
        {
            if((x/mid - mid) == 1)
            {
                return mid;
            }
            left = mid;
            mid = (left + right)/2;
        }else if(x/mid < mid)
        {
            if((mid - x/mid) == 1)
            {
                return x/mid;
            }
            right = mid;
            mid = (left + right)/2;
        }else
        {
            return mid;
        }
    }
   }
   ```
   ####总结
   
   题目大概设计二分的概念，但对此算法没有深入的理解，还要多练。此外，看到discuss好像还有牛顿迭代法，应该是个常用的工具
