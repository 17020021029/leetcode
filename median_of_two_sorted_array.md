# Median of Two Sorted Arrays
hard(看错了，哭)
## Problem
There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

Example 1:
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
Example 2:
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
## 解题思路
主要考查如何减少时间复杂度</br>
我的思路很简单，就是排序后，分奇偶讨论，但是总是在小地方编译错误，不知道思路是不是正确
## 未A代码
```
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
double findMedianSortedArrays(int* nums1, int nums1Size, int* nums2, int nums2Size) {
    if(nums1Size==0&&nums2Size==0)
        return 0;
    else{
   int new[nums1Size+nums2Size];
    double result;
    for(int i=0;i<nums1Size;i++)
        new[i]=nums1[i];
    for(int j=0;j<nums2Size;j++)
    {
        int count=nums1Size;
        new[count]=nums2[j];
        count++;
    }
    quickSort(new,0,nums1Size+nums2Size-2);
    int size=nums1Size+nums2Size;
    if((nums1Size+nums2Size)%2!=0){
        int a=size/2-1;
        int b=size/2;
      result=((new[a]+new[b])/2);  
    }
    else
        result=(double)new[size/2];
    return result;
    }
}
```
## 总结
这几天一直不舒服，也没心思做题，连难度都看错了，这道题以后也要再做一遍
