# 4Sum
与3sum类似
## Problem
Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

Note: The solution set must not contain duplicate quadruplets.

For example, given array S = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
## 问题分析
与3sum类似，可以用其算法，就是需要多加一层循环
## 解题思路
1. 写一个快排函数，排列数组；
2. 申请二维指针数组，作为返回的数组，赋给其可能的最大行数；
3. 第一层循环，标记第一个元素；第二层循环标记第二个元素，此时的begin与end标记第三和第四个元素；
4. 记录sum值，若相等，则赋值给result,begin++,end--,继续比较相近的；若sum<target,begin++;sum>target,end--;
5. 使用(*returnSize)标记数组下标
## 代码实现
```ruby
/**
 * Return an array of arrays of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
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
int** fourSum(int* nums, int numsSize, int target, int* returnSize) {
    int** result=(int**)malloc(sizeof(int*)*numsSize*(numsSize-1)*(numsSize-2)*(numsSize-3)/8);
    int sum,begin,end;
    int* temp;
    *returnSize=0;
    quickSort(nums,0,numsSize-1);
    if(numsSize<4){
        *returnSize=0;
        return result;
    }
        
    for(int i=0;i<numsSize-3;i++)
    {
        if(i>0 && nums[i]==nums[i-1])   continue;
        for(int j=i+1;j<numsSize-2;j++)
        {
            if(j>i+1 && nums[j]==nums[j-1]) continue;
            begin=j+1;
            end=numsSize-1;
            while(begin<end)
            {
                sum=nums[i]+nums[j]+nums[begin]+nums[end];
                if(sum==target)
                {
                    temp=(int*)malloc(sizeof(int)*4);
                    temp[0]=nums[i];temp[1]=nums[j];temp[2]=nums[begin];temp[3]=nums[end];
                    result[*returnSize]=temp;
                    (*returnSize)++;
                    begin++;end--;
                    while(begin<end && nums[begin]==nums[begin-1])  begin++;
                    while(begin<end && nums[end]==nums[end+1])  end--;
                }
                else if(sum>target)
                {
                    end--;
                    while(begin<end && nums[end]==nums[end+1])
                        end--;
                }
                else{
                    begin++;
                    while(begin<end && nums[begin]==nums[begin-1])
                        begin++;
                }
            }
        }
    }
    return result;
}
```
## 总结
3sum,3sum closest,4sum都是用到了快排函数，相似的算法
