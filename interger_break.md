# Interger Break
medium
## Problem
 Given a positive integer n, break it into the sum of at least two positive integers and maximize the product of those integers. Return the maximum product you can get.

For example, given n = 2, return 1 (2 = 1 + 1); given n = 10, return 36 (10 = 3 + 3 + 4).

Note: You may assume that n is not less than 2 and not larger than 58.
## 问题分析&解题思路
拆出足够多的3就能使乘积最大

这道题的难点其实在于证明为什么拆出足够多的 3就能使得乘积最大。下面我就试着证明一下。

首先证明拆出的因子大于 4 是不行的。设 x
是一个因子，x>4，那么可以将这个因子再拆成两个因子 x−2 和 2，易证 (x−2)×2>x

。所以不能有大于 4 的因子。

4
这个因子也是可有可无的，4=2+2，4=2×2。因此 4 这个因子可以用两个 2

代替。

除非没有别的因子可用，1
也不能选作因子。一个数 x 当它大于 3 时，有 (x−2)×2>(x−1)×1

。

这样呢，就只剩下 2
和 3 这两个因子可以选了。下面再证明 3 比 2

好。

一个数 x=3m+2n
，那么 f=3m×2n=3m×2x−3m2

可以对它取个对数。
lnf===mln3+nln2mln3+x−3m2ln2x2ln2+(ln3−32ln2)m

其中 ln3−32ln2>0
所以 f 是 m 的增函数，也就是说 m 越大越好。所以 3

越多越好。

再多说一句，如果拆出的因子不限于整数的话，可以证明e=2.718…

是最佳的选择。感兴趣的可以试着证明一下。
## 代码实现
```C++
class Solution {
public:
    int integerBreak(int n) {
        if(n==2) return 1;
        if(n==3) return 2;
        int res=1;
        while(n>4){
            res*=3;
            n-=3;
        }
        return res*n;
    }
};
```
## 参考
![https://blog.csdn.net/liyuanbhu/article/details/51198124]
