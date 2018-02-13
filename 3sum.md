# 3Sum
Two sum 进阶I
## Problem
Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.</br>
Note: The solution set must not contain duplicate triplets.
## 分析
和two sum基本相同，但这个确定target=0;</br>
三胞胎可能有多个，所以涉及二维数组;
## 解题过程
### approach1
采用了two sum的解法，设二维数组三次循环，符合要求即赋值,但是编译过程既不能通过，debug能力不够，网上也没有我这种白痴的做法，只好作罢</br>
*记录一下，说不定什么时候就想起哪里错啦*
```
int** threeSum(int* nums, int numsSize, int* returnSize){
    int len=(numsSize*(numsSize-1)*(numsSize-2)/6);
    static int result[len][3];
    int **p;
    p=result;
    for(int i=0;i<numsSize;i++){
        int count=0;
        for(int j=0;j<numsSize;j++){
            for(int k=0;k<numsSize;k++)
            {
                if(*(nums+i)+*(nums+j)+*(num+k)==0&& i!=j&&k!=j&&i!=k)
                {
                    result[count][0]=*(nums+i);
                    result[count][1]=*(nums+j);
                    result[count][2]=*(nums+k);
                }
                    
            }
        }
        count++;
    }
    return p;
}
```
### approach2
网上最多的解法，快排（减少因冒泡排序的时间复杂度）对数组排序，一层循环遍历，循环中第一个数不变，其他两个数从两边开始遍历</br>
开始我用qsort()来实现快排，可是不知道为什么老是编译错误，没办法只能像网上对qsort函数的解释一样自己写qsort函数来快排
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
int** threeSum(int* nums, int numsSize, int* returnSize) {  
    int i,sum,top=-1,begin,end;  
    int** result=(int**)malloc(sizeof(int*)*(numsSize*(numsSize-1)*(numsSize-2))/6);  //给二维数组赋最大行数
    if(numsSize<3){  
        *returnSize=0;  
        return result;  
    }  
    quickSort(nums,0,numsSize-1);  
    for(i=0;i<numsSize;i++){  
        if(nums[i]>0)   break;  
        if(i>0 && nums[i]==nums[i-1])   continue;  
        begin=i+1;end=numsSize-1;  
        while(begin<end){  
            sum=nums[i]+nums[begin]+nums[end];  
            if(sum==0){  
                top++;  
                result[top]=(int*)malloc(sizeof(int)*3);  
                result[top][0]=nums[i];
                result[top][1]=nums[begin];
                result[top][2]=nums[end];  
                begin++;end--;  
                while(begin<end && nums[begin]==nums[begin-1])
                    begin++;  
                while(begin<end && nums[end]==nums[end+1])
                    end--;  
            }
            else if(sum>0) end--;  
            else begin++;  
        }  
    }  
    *returnSize=top+1;  
    return result;  
}  
```
## 总结
qsort(快排)的使用*这个可以记住然后以后用，像冒泡排序一样（时间复杂度较大）*</br>
二维数组动态内存分配</br>
从两边开始遍历，也是减小时间的好办法</br>
看清注释里的内容，要计算*returnSize,即二维数组行数
