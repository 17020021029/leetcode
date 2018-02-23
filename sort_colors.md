# Sort Colors
冒泡排序
## Problem
 Given an array with n objects colored red, white or blue, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

Note:
You are not suppose to use the library's sort function for this problem. 
## 分析
今晚不知怎么老是做到这种题，说是给颜色排序，但其用整型0，1，2表示红，白，蓝后，且从小到大与颜色顺序相同，只需要最基本冒泡排序即可
## 代码实现
```rubt
void sortColors(int* nums, int numsSize) {
    for(int i=0;i<numsSize-1;i++)
    {
        for(int j=0;j<numsSize-i-1;j++)
        {
            if(nums[j]>nums[j+1])
            {
                int temp;
                temp=nums[j];
                nums[j]=nums[j+1];
                nums[j+1]=temp;
            }
        }
    }
    return;
}
```
## 总结
没啥可总结的，就是小小的变通
