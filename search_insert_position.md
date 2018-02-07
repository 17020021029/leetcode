# Search Insert Position
寻找插入位置
## Problem
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.
## 分析
一维数组的处理
## 解题过程
### 思路一
遍历，若相等，则返回数组下标，如不相等，则分情况讨论：大于最后一个元素；小于第一个元素；居中
#### 代码实现
```
int searchInsert(int* nums, int numsSize, int target) {
    int result;
    for(int i=0;i<numsSize;i++)
    {
        if(*(nums+i)==target)
            result=i;
        if(*(nums+i)<target&&*(nums+i+1)>target)
            result=i+1;
        if(*(nums+0)>target)
            result=0;
        if(*(nums+numsSize-1)<target)
            result=numsSize;
    }
    return result;
}
```
### 改进
二分法减小时间复杂度,而且若没有target，不用讨论，就可以直接得到索引
#### 代码实现
int searchInsert(int* nums, int numsSize, int target) {
    int i=0;
    int r=numsSize-1;
    while(i<=r)
    {
        int mid=i+(r-i)/2;
        if(*(nums+mid)==target)
        {
            return mid;
        }
        if(*(nums+mid)<target)
        {
            i=mid+1;
        }
        else 
        {
            r=mid-1;
        }
    }
    return i;    
}
