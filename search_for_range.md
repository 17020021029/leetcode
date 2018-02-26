# Search for Range
二分查找法的应用
## Problem
Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].

For example,
Given [5, 7, 7, 8, 8, 10] and target value 8,
return [3, 4].
## 问题分析
题意很简单，但是要求时间复杂度，所以需要用到二分法
## 代码实现
```ruby
int* searchRange(int* nums, int numsSize, int target, int* returnSize) {  
    int* result=(int*)malloc(sizeof(int)*2);  
    int l=0,r=numsSize-1,mid;  
    while(l<=r){  
        mid=(l+r)/2;  
        if(nums[mid]==target)
        break;  
        else if(nums[mid]>target)r=mid-1;  
         l=mid+1;  
    }  
    if(l<=r){  
        l=mid-1;  
        while(l>=0 && nums[l]==nums[mid])l--;  
        r=mid+1;  
        while(r<numsSize && nums[r]==nums[mid])r++;  
        result[0]=l+1;
        result[1]=r-1;  
        *returnSize=2;  
        return result;  
    }else{  
        result[0]=-1;result[1]=-1;  
        *returnSize=2;  
        return result;  
    }  
}
## 总结
二分查找法的使用
