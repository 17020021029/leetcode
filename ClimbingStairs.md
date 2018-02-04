# Climbing Stairs
###  Description
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Note: Given n will be a positive integer.
###   解题过程
####    方法一
递归调用（Time Limit Exceeded）：应该是当时上机练习题，我也是这样写的，可是这次在n=44时就超时了，emmmmm，看来问题没那么简单
```
int climbStairs(int n) {
    if(n==1)
        return 1;
    if(n==2)
        return 2;
    else return climbStairs(n-1)+climbStairs(n-2);
}
```
####   方法二
for循环（AC）这个比较玄学了，定义了一个不是特别大的数组（1000），用for循环实现递归，竟然过了，看来递归算法的时间复杂度真的高，比for循环都要大

想一下之前学的递归的原理，包含压栈与出栈的过程，一次调用就比一次一次循环的时间要长，所以用for循环实现递归的方法还是比较可行的
*这个大概教程里也有吧，我竟然给忘了
```
    int i, a[999];
    if(n == 1) return 1;
    if(n == 2) return 2;
    a[0] = 0;a[1] = 1;a[2] = 2;
    for(i = 3;i <= n; i++){
        a[i] = a[i-1] + a[i-2];
    }
    return a[n];
```

### 总结：
核心思路没问题，主要是记住用for循环实现递归减小时间复杂度

This is a blog :[link to example](https://www.cnblogs.com/yxysuanfa/p/7001285.html)
