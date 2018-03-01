# Container With Most Water
## Problem
Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2
## 问题分析
这问题问的不清楚啊，不试一下的话都不知道最后要返回什么</br>
最终要返回的是area</br>
这个题一般是要遍历所有的组合，用一个max做比较，返回遍历完后的max；</br>
但是这样很麻烦，时间复杂度也大，总结一下，我们发现，假设最终的两个高度为i,j&&i<j,那么j之后的高度一定都比a[j]小，同理，i之前的高度一定都比a[i]小</br>
## 解题思路
从两端开始遍历，不断更新端点值（若前一个高，则从后一个往前找大的值，否则从前一个从后找大的值）；比较当前area值与max值，最终返回最终的max值
## 代码实现
```ruby
int maxArea(int* height, int heightSize) {
    int max=0,area;
    int i=0,j=heightSize-1;
    while(i<j)
    {
        area=(height[i]<height[j]?height[i]:height[j])*(j-i);
        max=max>area?max:area;
        if(height[i]<height[j])
        {
            int k=i;
            while(i<j && height[i]<=height[k])
                i++;
        }
        else{
            int k=j;
            while(i<j && height[j]<=height[k])
                j--;
        }
    }
    return max;
}
```
## 总结
这种不断更新端点值的算法之前也经常用,能记得的有 sum 的一系列问题（3sum,3sum closest,4sum等）;二分查找法也是这样，不断更新端点值来求中间值
