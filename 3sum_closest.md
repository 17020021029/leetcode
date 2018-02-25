# 3Sum Closest
类似于3Sum
## Problem
Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

    For example, given array S = {-1 2 1 -4}, and target = 1.
    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
## 问题分析
与 3sum 类似，可以用相似的算法
## 解题思路
写一个快排函数，对给定数组排序，避免使用冒泡排序增加的时间复杂度；定义初始最小值，赋值为INT_MAX,作为比较的最小距离；在一次循环中，设置begin,end与for循环中的i作为数组下标，计算当前的sum值，计算此时sum与target的距离，与自定义的初始最小距离比较；若此时的sum恰巧等于target，直接返回target，若小于target，begin++,否则，end--.
若没有找到等于target的最小和，则最终返回最小距离与target的和。
## 代码实现
```ruby
void quickSort(int* nums,int first,int end){  
    int temp,l,r;  
    if(first>=end)return;  
    temp=nums[first];  
    l=first;r=end;  
    while(l<r){  
        while(l<r && nums[r]>=temp)
            r--;  
        if(l<r)
            nums[l]=nums[r];  
        while(l<r && nums[l]<=temp)
            l++;  
        if(l<r)
            nums[r]=nums[l];  
    }  
    nums[l]=temp;  
    quickSort(nums,first,l-1);  
    quickSort(nums,l+1,end);  
}
int threeSumClosest(int* nums, int numsSize, int target) {
    int begin,end;
    int sum;
    int my_min=INT_MAX;
    quickSort(nums,0,numsSize-1);
    for(int i=0;i<numsSize-2;i++)
    {
        if(i>0 && nums[i]==nums[i-1]) continue;
        begin=i+1;
        end=numsSize-1;
        while(begin<end)
        {
            sum=nums[i]+nums[begin]+nums[end];
            if(abs(sum-target)<abs(my_min))
                my_min=sum-target;
            if(target==sum)
                return target;
            else if(sum>target)
                end--;
            else begin++;
        }
    }
    return my_min+target;
}
```
## 总结
复习了C语言中快排的实现及与3sum问题中相似的算法，都是减小时间复杂度的好办法
