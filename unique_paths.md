# Unique Paths
## Problem
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![图片](https://leetcode.com/static/images/problemset/robot_maze.png)

Above is a 3 x 7 grid. How many possible unique paths are there?

Note: m and n will be at most 100.
## 问题分析
向下走和向右走的步数是一定的,一共走m+n-2步，其中m-1步往一个方向走，n-1步往另一个方向走，该题就转化为了排列组合的问题，从m+n-2步中选出m-1步来或从m+n-2选出n-1步来，结果都是一样的
## 代码实现
```ruby
int uniquePaths(int m, int n) {
    long x m+n-2;  //一定要用long，阶乘数太大了
    long y=(m<n?m:n)-1;
    long up=1,down=1;   
    if(m==1||n==1) 
        return 1;
    for(int i=0;i<y;i++){
        up *= x--;
    }
    for(int i=y;i>0 ;i--){
        down *= i;
    }
    return (int)(up/down);
}
```
